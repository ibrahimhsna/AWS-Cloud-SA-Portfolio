# Highly Available Web Applications

### 1. Repository Name
`aws-multi-az-ha-web-architecture`

### 2. Project Category
Networking & Resilience / High Availability Web Architecture

### 3. Professional Portfolio Description
Deployed a web application across three Availability Zones behind an Application Load Balancer with health checks, Route 53 DNS, CloudFront caching, and a Multi-AZ RDS backend with automated failover.

### 4. Recommended Repository Structure
```text
aws-multi-az-ha-web-architecture/
├── README.md
├── architecture/
│   └── ha-architecture-diagram.png
└── documentation/
    └── failover-and-health-checks.md
```

### 5. Complete README.md
```markdown
# Highly Available Multi-AZ Web Application Architecture

> Guided hands-on lab (AWS Skill Builder / SimuLearn) with an independent extension task.

## Overview
A web application is deployed across multiple Availability Zones behind an Application Load
Balancer with configured health checks, fronted by CloudFront/S3 for cached content and Route 53
for DNS, with an RDS Multi-AZ database providing automatic failover.

## Problem
A single-AZ, single-instance deployment is a single point of failure for both compute and database
tiers, and cannot absorb AZ-level outages or handle horizontal scale.

## Solution Architecture
- Route 53 resolves the domain; CloudFront serves/caches static content from S3 and forwards
  dynamic requests.
- Elastic Load Balancing distributes traffic across EC2 instances in Availability Zones A, B, and C.
- An Auto Scaling group (with CloudWatch metrics, CPU > 80% scale trigger) manages EC2 capacity in AZ A
  (and was extended to a third AZ as the DIY task).
- Amazon RDS runs a primary DB instance with a standby replica for automated failover between AZs.

## AWS Services & Roles
| Service | Role |
|---|---|
| Route 53 | DNS resolution for the application domain |
| Amazon CloudFront | CDN caching of static content |
| Amazon S3 | Origin/storage for cached static content |
| Elastic Load Balancing (ALB) | Distributes traffic across EC2 instances, performs health checks |
| EC2 Auto Scaling | Maintains/scales EC2 instance capacity, triggered by CloudWatch CPU metric |
| Amazon CloudWatch | Supplies scaling metrics to the ASG |
| Amazon RDS (Multi-AZ) | Primary/standby database with automated failover |

## Network and Security Design
Not fully detailed in the source diagram beyond AZ segmentation. **Not documented / Requires
clarification**: VPC/subnet layout, security group rules, public vs private subnet placement.

## High Availability and Scalability
- Compute spans 3 Availability Zones (A, B, C) — AZ C was added as part of the DIY task.
- ALB health checks were configured against the Auto Scaling group so unhealthy instances are
  taken out of rotation.
- RDS Multi-AZ standby provides automatic failover for the database tier.

## Monitoring and Logging
CloudWatch is used for ASG scaling metrics (CPU-based trigger). No dashboards/alerting beyond the
scaling metric are documented.

## What I Implemented (Guided)
- Configured an Auto Scaling group to use an Application Load Balancer.
- Configured load balancer health checks for the Auto Scaling group.
- Added a second Availability Zone to the Auto Scaling group.

## What I Implemented (DIY / Unguided)
- Configured the existing Auto Scaling group to include a new EC2 instance in a third Availability Zone.

## Limitations / Not Documented
- VPC/subnet/security group design: **Not documented / Requires clarification**.
- SSL/TLS termination point: **Not documented / Requires clarification**.
- Backup strategy for RDS: **Not documented / Requires clarification**.

## Skills Demonstrated
Application Load Balancer configuration, health checks, multi-AZ Auto Scaling, CloudFront/S3 static
content delivery, RDS Multi-AZ failover concepts, Route 53 DNS.

## Future Improvements
- Document/diagram the VPC and security group layer explicitly.
- Add HTTPS/ACM certificate to the ALB and document the security posture.
```

### 6–9. Details
Diagram filename: `ha-architecture-diagram.png`; Title: "Multi-AZ Highly Available Web Architecture"; GitHub caption: "3-AZ web tier behind ALB with CloudFront/S3 and Multi-AZ RDS." LinkedIn caption: "Built a 3-AZ highly available web architecture with automated failover for compute and database."

### 10. LinkedIn Portfolio Description
Deployed a web application across three Availability Zones behind an Application Load Balancer with health checks, added CloudFront/S3 for cached content delivery, and configured Multi-AZ RDS for automated database failover — then extended the compute tier into a third AZ as an independent task. Skills: ALB, Auto Scaling, RDS Multi-AZ, CloudFront, Route 53. *(AWS Skill Builder hands-on lab.)*

### 11. Skills Demonstrated
High availability architecture, ALB, ASG, RDS Multi-AZ, CDN.

### 12. Technical Weaknesses and Gaps
No VPC/security-group detail; no TLS story; "highly available" claim would be stronger with an explicit RTO/RPO discussion for the RDS failover, which is not documented.

### 13. Recommended Improvements
Diagram the network layer; add HTTPS; document failover test results if performed.

---
