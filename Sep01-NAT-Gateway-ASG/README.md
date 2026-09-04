# Sep 1, 2026 — NAT Gateway, Private Routing and Auto Scaling

## What I worked on
I continued building the self-healing AWS infrastructure by improving the network design and completing the main Auto Scaling configuration.

## Networking changes
- Added a NAT Gateway.
- Configured private subnet routing through the NAT Gateway.
- Kept application instances in private subnets while allowing required outbound internet access.

## Auto Scaling changes
- Added an Amazon Linux AMI lookup using a Terraform data source.
- Created the EC2 instance security group.
- Created an EC2 Launch Template.
- Installed and started Apache HTTP Server through user data.
- Generated a simple web page showing the instance ID.
- Created an Auto Scaling Group with:
  - Minimum capacity: 2
  - Desired capacity: 2
  - Maximum capacity: 4
- Placed instances in private subnets.
- Attached the ASG to the ALB target group.
- Enabled ELB health checks.

## What I learned
This was the point where the project started behaving like actual self-healing infrastructure. The ALB can perform health checks, and the ASG can maintain the desired number of application instances.

## Architecture flow
Internet → ALB → Target Group → Auto Scaling Group → EC2 instances in private subnets

Private instances → NAT Gateway → Internet (outbound access)

## Key takeaway
High availability is not just launching multiple servers. The network routing, health checks, load balancer and Auto Scaling Group need to work together.

## Project
[self-healing-aws-infra](https://github.com/lalitbhadane/self-healing-aws-infra)

## Next
Add the database layer and improve secure access to the private EC2 instances.
