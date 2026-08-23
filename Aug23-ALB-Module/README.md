# Day: August 23, 2026 — ALB Module (Flagship Project)

Code: https://github.com/lalitbhadane/self-healing-aws-infra/tree/main/modules/alb

## What I did
Learned security groups and load balancer concepts, then wrote the ALB module by hand. Also caught and fixed a structural mistake: modules were being applied directly instead of through a root config, which would have caused duplicate infrastructure.

## Concepts learned
- Security groups as stateful virtual firewalls (inbound/outbound rules)
- Application Load Balancer, target groups, and listeners
- Target group health checks — the mechanism that later enables self-healing
- Terraform state is tied to the working directory, not the AWS account — why modules must be called from a root config, not applied standalone
- Wiring modules together: one module's output becomes another module's input variable

## What I built
- ALB module: security group (HTTP inbound from internet), Application Load Balancer, target group with health check, HTTP listener
- Root main.tf wiring the VPC and ALB modules together with one shared state
- Fixed the standalone-module mistake: destroyed the duplicate VPC, reapplied everything cleanly from root (13 resources)
- Applied, got a live ALB DNS name, verified, committed, pushed
- Destroyed all resources at end of session to avoid ongoing ALB cost — new habit: destroy at end of each session, reapply at start of next

## Next
Move on to the ASG (Auto Scaling Group) module — the actual self-healing mechanism.
