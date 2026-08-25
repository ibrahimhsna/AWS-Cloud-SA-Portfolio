# Auto-Healing and Scaling Applications

### 1. Repository Name
`aws-ec2-auto-scaling-scheduled-policies`

### 2. Project Category
Compute / Resilience & Elasticity (EC2 Auto Scaling)

### 3. Professional Portfolio Description
Hands-on implementation of an EC2 Auto Scaling group for a game-server workload, combining a CloudWatch CPU-utilization alarm with time-based scheduled scaling actions to align capacity with a known daily demand pattern.

### 4. Recommended Repository Structure
```text
aws-ec2-auto-scaling-scheduled-policies/
├── README.md
├── architecture/
│   └── architecture-overview.png
└── documentation/
    └── scaling-policy-notes.md
```
(No IaC/scripts included — configuration was done via the AWS/SimuLearn console. See "Not documented" below.)

### 5. Complete README.md
```markdown
# EC2 Auto Scaling with Scheduled and Dynamic Scaling Policies

> This project was completed as a guided hands-on lab in AWS Skill Builder (SimuLearn).
> It demonstrates applied configuration of Amazon EC2 Auto Scaling in a simulated AWS environment,
> including an independent extension task (DIY Goal).

## Overview
This lab implements auto-healing and elastic capacity management for a fleet of game-server EC2
instances using an Auto Scaling group (ASG), a CloudWatch CPU alarm for dynamic scaling, and two
CloudWatch scheduled events for predictable daily demand cycles.

## Problem
A game-server workload experiences (a) unpredictable spikes in CPU load and (b) predictable
daily peak/off-peak usage windows. Static capacity either under-serves peak load or wastes spend
during low-usage hours.

## Architecture
- An Auto Scaling group is configured with **Minimum = 1** and **Maximum = 3** instances, launched
  from a Launch Template built off a custom AMI created from a running "Game server" instance.
- A CloudWatch alarm monitors CPU utilization; when usage stays below the 70% threshold the ASG
  is not scaled further, and above it a new instance is added (`CPU usage < 70%` → maintain, else scale out).
- Two scheduled scaling events adjust desired capacity at fixed UTC times (11:00 PM and 5:00 PM),
  independent of the CPU-based policy.

## AWS Services & Roles
| Service | Role |
|---|---|
| Amazon EC2 Auto Scaling | Maintains 1–3 game-server instances, replaces unhealthy instances |
| Amazon CloudWatch (Alarms) | Triggers dynamic scale-out based on CPU utilization |
| Amazon CloudWatch (Scheduled Actions) | Adjusts capacity at fixed daily times |
| Amazon Machine Image (AMI) | Custom image used to launch consistent game-server instances |
| EC2 Launch Template | Standardizes instance configuration for the ASG |

## Workflow
1. CloudWatch alarm evaluates average CPU utilization across the ASG.
2. If load is high, the ASG launches an instance from the Launch Template (sourced from the AMI).
3. If load is low, the ASG may terminate an instance, subject to Min=1.
4. Independently, scheduled events force desired-capacity changes at 5:00 PM and 11:00 PM UTC,
   overriding organic demand at those two points in the day.

## Reliability and Scalability
- Minimum capacity of 1 guarantees the service is never fully down (auto-healing: a terminated/
  unhealthy instance is automatically replaced up to the Min setting).
- Maximum capacity of 3 bounds cost exposure during demand spikes.
- Scheduled scaling reduces the lag between known demand changes and capacity changes, compared to
  relying on the CPU alarm alone.

## What I Implemented (Guided)
- Created the Auto Scaling group and attached EC2 instances to it.

## What I Implemented (DIY / Unguided)
- Configured an additional scheduled scaling policy to scale the group down to 0 resources at
  01:00 AM daily.

## Limitations / Not Documented
- Multi-AZ placement for the ASG: **Not documented / Requires clarification**.
- Health check type (EC2 vs ELB) and grace period: **Not documented / Requires clarification**.
- No load balancer is shown in this lab; traffic distribution mechanism to the 3 instances is
  **Not documented / Requires clarification**.

## Skills Demonstrated
EC2 Auto Scaling group configuration, Launch Templates, AMI creation, CloudWatch alarms, scheduled
scaling actions, basic capacity planning for variable workloads.

## Future Improvements
- Add an Application Load Balancer + target group health checks (as done in Project 3) to actually
  distribute traffic, not just scale headcount.
- Reproduce this configuration in Terraform in a personal AWS account for a fully IaC-backed repo.
```

### 6. Architecture Explanation
The design pairs **reactive** scaling (CloudWatch CPU alarm) with **proactive** scaling (scheduled events at known peak/trough times), a common real-world pattern for workloads with both predictable and unpredictable variance. The Min=1/Max=3 boundary is the fault-tolerance and cost-control mechanism respectively.

### 7. AWS Services and Their Roles
Covered in the README table above. Alternative not selected: Target Tracking scaling policy on a custom metric — the lab uses a simple alarm-threshold model instead.

### 8. Technical File Naming Recommendations
- `architecture-overview.png`
- `scaling-policy-notes.md`

### 9. Architecture Diagram Information
- Filename: `architecture-overview.png`
- Title: "EC2 Auto Scaling — Dynamic + Scheduled Policies"
- Description: Shows CloudWatch-driven scale actions and two scheduled events feeding a 1–3 instance ASG behind a shared AMI/Launch Template.
- GitHub caption: "Auto Scaling architecture combining CPU-based and scheduled scaling policies."
- LinkedIn caption: "How I combined CloudWatch alarms with scheduled scaling to handle both spikes and predictable daily load."

### 10. LinkedIn Portfolio Description
Configured an EC2 Auto Scaling group combining CloudWatch CPU alarms with scheduled scaling events to handle both spike and predictable demand, and extended it with a custom scheduled policy to scale to zero overnight — reducing idle spend. Skills: EC2 Auto Scaling, CloudWatch, capacity planning. *(AWS Skill Builder hands-on lab.)*

### 11. Skills Demonstrated
EC2 Auto Scaling, CloudWatch alarms/scheduled actions, AMI/Launch Templates.

### 12. Technical Weaknesses and Gaps
- No load balancer or health-check strategy documented — "auto-healing" claim is weak without it.
- No multi-AZ evidence in the diagram.
- No IaC; repo currently is documentation-only.

### 13. Recommended Improvements
Add ALB + target-group health checks; document AZ placement; convert to Terraform for reproducibility.

---
