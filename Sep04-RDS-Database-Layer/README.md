# Sep 4, 2026 — RDS PostgreSQL, Database Subnets and SSM Access

## What I worked on
Today I added the database layer to the self-healing AWS infrastructure project and improved access to private EC2 instances.

## Database networking
I extended the VPC module with:
- Dedicated database subnets across availability zones.
- An AWS DB Subnet Group.
- Outputs for database subnet IDs and the DB subnet group name.

## RDS module
I created a reusable `modules/rds` Terraform module containing:
- RDS security group.
- PostgreSQL database instance.
- Private database deployment.
- Configurable engine version.
- Configurable instance class and storage.
- Database name and master username variables.
- Sensitive password variable.
- Multi-AZ configuration option.
- Outputs for the database endpoint and instance ID.

## Security
The RDS security group allows PostgreSQL traffic on port `5432` only from the EC2 instance security group. The database is not publicly accessible.

## Systems Manager access
I also added:
- An IAM role for EC2.
- The `AmazonSSMManagedInstanceCore` policy.
- An IAM instance profile attached to the launch template.

This prepares the private EC2 instances for AWS Systems Manager access without relying on direct SSH exposure.

## Architecture now
Internet
  ↓
Application Load Balancer
  ↓
Auto Scaling Group
  ↓
EC2 instances in private subnets
  ↓
PostgreSQL RDS in dedicated database subnets

Private EC2 instances can use the NAT Gateway for required outbound access and are configured for AWS Systems Manager.

## What I learned
- Why database workloads should be isolated in dedicated subnets.
- How security groups can restrict database access to application servers only.
- How Terraform modules make a growing infrastructure project easier to organize.
- Why SSM is useful for managing instances without opening SSH to the internet.

## Project
[self-healing-aws-infra](https://github.com/lalitbhadane/self-healing-aws-infra)

## Current status
The project now includes:
- VPC
- Public and private subnets
- Internet Gateway
- NAT Gateway
- Application Load Balancer
- Auto Scaling Group
- EC2 launch template
- PostgreSQL RDS
- Database subnet group
- Security groups
- IAM/SSM access for EC2

## Next
Continue testing the complete infrastructure and build the CI/CD workflow with GitHub Actions.
