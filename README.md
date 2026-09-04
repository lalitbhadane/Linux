# 🧠 100 Days of Linux & DevOps – Learning Journey

Welcome to my daily log of learning Linux and DevOps! This repo documents my hands-on practice, notes, and reflections as I work toward becoming job-ready in the AWS Cloud & DevOps space.

**Status update (Aug 2026):** I logged daily for the first 12 days covering Linux fundamentals, then paused this repo while focused on job applications and interview prep. Resuming now as I move into AWS + Terraform + CI/CD, building toward a full self-healing multi-tier AWS application.

## 📌 Why This Repo?

I recently rebooted my life and committed to going **all in** on my tech career. This repo serves as:

- 💼 A **proof-of-work portfolio**
- 🧰 A **reference for my future self**
- 🔥 A daily **accountability system**
- 🧑‍💻 A resource for others starting the same journey

---

## 📅 Current Phase: **AWS Cloud & Terraform (resumed)**

| Duration | Focus |
| -------- | ----- |
| Ongoing  | AWS fundamentals, Terraform (IaC), CI/CD with GitHub Actions, building toward a self-healing multi-tier AWS application |

**Previously completed:** 30-day Linux Fundamentals track (commands, bash scripting, permissions, users, services, networking, git) — see Day 1-12 below.

---

## 🛠️ Daily Structure

Each day has a dedicated folder like `Day01/`, `Day02/`, etc.
Each folder includes:

- A `README.md` log (topics, commands, reflections)
- Practice scripts or notes (`.sh`, `.txt`, etc.)
- Any supporting diagrams or visuals
- Optional screenshots or tweet visuals

---

## 📚 Linux Learning Topics Breakdown

| Week   | Focus Areas                                                        |
| ------ | ------------------------------------------------------------------ |
| Week 1 | Terminal basics, navigation, file/dir operations, wildcards, paths |
| Week 2 | Permissions, users/groups, processes, disk mgmt                    |
| Week 3 | Bash scripting, automation, cron, basic system monitoring          |
| Week 4 | Services (`systemctl`), logs, networking tools, SSH                |

---

## 📍 Progress So Far

| Day | Status | Summary |
| --- | --- | --- |
| Day 1-12 | ✅ Complete | Linux fundamentals — terminal basics, file/dir ops, permissions & ownership, processes, bash scripting, services (`systemctl`), networking tools, SSH |
| Aug 21, 2026 | ✅ Complete | **Resumed.** Set up full AWS/Terraform toolchain in WSL Ubuntu, created a scoped IAM user (not root), wrote and applied my first Terraform config (S3 bucket), ran the full `init → plan → apply → destroy` cycle, pushed to GitHub |
| Aug 22, 2026 | ✅ Complete | Built a reusable VPC module with public/private subnets, Internet Gateway and route tables. |
| Aug 23, 2026 | ✅ Complete | Built an ALB module and connected the root Terraform configuration with the VPC and ALB modules. |
| Aug 24, 2026 | ✅ Complete | Started the ASG module and configured the application instance security group so HTTP traffic is allowed only from the ALB. |
| Sep 1, 2026 | ✅ Complete | Added a NAT Gateway and private subnet routing. Completed the launch template and Auto Scaling Group, deployed Apache on EC2 through user data, connected instances to the ALB target group and enabled ELB health checks. |
| Sep 4, 2026 | ✅ Complete | Added a PostgreSQL RDS module, dedicated database subnets and DB subnet group. Added IAM/SSM access for EC2 and restricted database access to the application security group. |

*(This table will be updated as I move forward — next up: VPC, ALB, Auto Scaling, RDS, and a GitHub Actions CI/CD pipeline for a self-healing multi-tier AWS app.)*

---

## 🔗 Connect With Me

- 🐦 Twitter (X) : [@lalitbhadanex](https://x.com/lalitbhadanex)
- 💼 LinkedIn: [Lalit Bhadane](https://linkedin.com/in/lalitbhadane)
- 🌐 Blog (coming soon!)

---

## 📣 Shoutout

Big thanks to the open source community & mentors who shared learning paths, and to myself—for showing up every day (even after a break).

Let's go. 💪
