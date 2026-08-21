# Aug 21, 2026 — Terraform + AWS: First Steps

## What I did

- Set up a full DevOps toolchain from scratch inside WSL Ubuntu: Terraform (via HashiCorp's official apt repo) and AWS CLI v2
- Created a dedicated IAM user (`terraform-admin`) instead of using root credentials — generated programmatic access keys and connected them via `aws configure`
- Verified the connection with `aws sts get-caller-identity`
- Wrote my first Terraform configuration (`main.tf`) from scratch — an AWS provider block and a single `aws_s3_bucket` resource
- Ran the full Terraform lifecycle for the first time:
  - `terraform init` — downloaded the AWS provider plugin
  - `terraform plan` — reviewed the dry-run output before touching real infrastructure
  - `terraform apply` — created a real S3 bucket in my AWS account (ap-south-1)
  - Verified it existed independently via `aws s3 ls`
  - `terraform destroy` — tore it down cleanly

## What I learned

- **Provider vs. resource**: the provider is the plugin that lets Terraform talk to AWS; a resource block is one real thing you want to exist
- **The state file** is Terraform's memory of what it created — never edit it by hand
- **Why `plan` exists separately from `apply`**: it's a safety check, a habit that matters a lot more once real production infrastructure is involved
- Caught and fixed my own syntax error (`provider = "aws" {` should be `provider "aws" {` — block headers never take `=`)
- Set up a billing budget alert and learned my AWS account's 12-month free tier had already expired — so cost awareness (destroying resources after each session) is now a deliberate habit, not just a nice-to-have

## Files

- `main.tf` — the actual Terraform config used in this session

## Next up

Building a full self-healing multi-tier AWS application: VPC, ALB, Auto Scaling Group, RDS, and a GitHub Actions CI/CD pipeline. Separate flagship repo coming this weekend.
