# Aug 24, 2026 — Auto Scaling Group (ASG) Module

## What I worked on
Today I added the first version of the **Auto Scaling Group module** to my self-healing AWS infrastructure project.

## What I learned
- Created an EC2 instance security group that allows HTTP traffic only from the Application Load Balancer security group.
- Restricted inbound access so application instances are not directly exposed to the internet.
- Configured outbound access for the instances.
- Started separating infrastructure into reusable Terraform modules.

## Project work
The initial ASG module contains:
- `modules/asg/main.tf`
- `modules/asg/variables.tf`
- `modules/asg/outputs.tf`

## Key takeaway
A self-healing infrastructure needs more than individual EC2 instances. The next step was to turn this into a real Auto Scaling setup where unhealthy instances can be replaced automatically.

## Project
[self-healing-aws-infra](https://github.com/lalitbhadane/self-healing-aws-infra)

## Next
Build the launch template and Auto Scaling Group, then connect the instances to the ALB target group.
