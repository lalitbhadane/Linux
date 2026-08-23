# Day: August 22, 2026 — VPC Module (Flagship Project)

Code: https://github.com/lalitbhadane/self-healing-aws-infra/tree/main/modules/vpc

## What I did
Started the flagship self-healing AWS infrastructure project (separate repo: self-healing-aws-infra). Learned core networking concepts and wrote the VPC module by hand.

## Concepts learned
- VPC as an isolated network space
- Subnets tied to Availability Zones, public vs private (route table determines this)
- Internet Gateway vs NAT Gateway
- Route tables and route table associations
- Terraform `count` for looping resource creation
- Module file convention: main.tf / variables.tf / outputs.tf

## What I built
- VPC module: 1 VPC, 2 public + 2 private subnets across 2 AZs, Internet Gateway, public route table
- Applied and verified via AWS CLI and Console resource map
- Committed and pushed to self-healing-aws-infra repo

## Next
Move on to the ALB (Application Load Balancer) module.
