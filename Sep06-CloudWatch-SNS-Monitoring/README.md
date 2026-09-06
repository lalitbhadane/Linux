# Sep 6, 2026 — CloudWatch Alarms and SNS Alerting

## What I worked on
Added observability to the self-healing AWS infrastructure project — until now, the ASG could self-heal silently with no visibility into it.

## Concepts learned
- CloudWatch Metrics vs Alarms vs Logs — metrics are raw numbers, alarms are threshold rules on top of metrics, logs are separate text output
- SNS as a pub/sub notification service — a Topic that fans out to subscribers (email, in this case)
- Why CloudWatch Alarms can't send emails directly — they publish to an SNS Topic, which handles delivery
- EventBridge vs CloudWatch Alarms — Alarms watch continuous metrics against a threshold; EventBridge reacts to discrete events (e.g. an ASG replacing an instance). Both can target the same SNS topic, but they solve different problems
- Industry practice: start monitoring with utilization/saturation metrics (CPU, memory, disk) as leading indicators, before capacity-count or event-based alarms which are lagging signals
- Burstable instance types (t3.micro) and CPU credits — a CPU alarm firing on a t3.micro can mean actual undersized-instance signal, not just noise

## What I built
New `modules/monitoring` Terraform module:
- SNS Topic + email subscription for alerts
- CloudWatch Alarm watching average CPU utilization across the ASG (>= 80% for 2 consecutive 5-minute periods), with both `alarm_actions` and `ok_actions` wired to the SNS topic
- Wired into root `main.tf`

## Verification
Confirmed the alarm is actively evaluating real metrics via AWS CLI (`describe-alarms`) — state `OK`, correctly reading live CPU data from the ASG (~2.8%, expected for idle instances serving a static page).

## Key takeaway
Self-healing infrastructure that heals silently is still a gap — a real production system needs to notify a human when something is degrading, not just recover invisibly. Utilization alarms are a leading indicator (catch problems before they cause a failure), while "instance replaced" events are a lagging indicator (tell you after the fact) — that ordering is why CPU alarms come first in the industry, not capacity-change alerts.

## Project
[self-healing-aws-infra](https://github.com/lalitbhadane/self-healing-aws-infra)

## Next
Add RDS-level CloudWatch alarms (CPU, free storage) using the same SNS topic. Then GitHub Actions CI/CD pipeline, the self-healing demo, and final README.
