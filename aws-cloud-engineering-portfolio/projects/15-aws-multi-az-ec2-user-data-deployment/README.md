# Multi-AZ EC2 Deployment with User Data Scripting

> Guided hands-on lab (AWS Skill Builder / SimuLearn) with an independent extension task.

## Overview
Deploys a compute workload ("Island stabilization system") across two Amazon EC2 instances in
separate Availability Zones within `us-east-1`, each writing to its own Amazon EBS volume and
displaying instance details via a browser-accessible user-data script.

## Problem
A single-instance, single-AZ deployment is a foundational anti-pattern for availability; this lab
establishes the basic pattern of spreading compute across AZs from the start.

## Architecture
A central control system ("Island stabilization system") accesses two "computational modules,"
each running as an EC2 instance in a distinct AZ (`us-east-1a`, `us-east-1b`) within the
`us-east-1` region. Each instance has an attached Amazon EBS volume for data storage, and each was
configured with a user-data script that exposes instance details (e.g., instance ID, AZ) via a
browser at the instance's IP/DNS.

## AWS Services & Roles
| Service | Role |
|---|---|
| Amazon EC2 | Compute instances ("computational modules") running the workload |
| Amazon EBS | Attached block storage volume per instance |
| EC2 User Data | Bootstraps each instance to serve instance metadata/details via a web page |

## High Availability and Scalability
Deploying computational module A in `us-east-1a` and module B in `us-east-1b` ensures the
stabilization system does not depend on a single Availability Zone remaining available — the
foundational building block for later, more sophisticated HA architectures in this portfolio
(see Project 3).

## Workflow
1. Launch an EC2 instance with a user-data script that displays instance details in a browser.
2. Verify the instance details are viewable at its IP address / example.com mapping.
3. (DIY) Launch a second EC2 instance in a different Availability Zone within the same Region,
   running the same configuration.

## What I Implemented (Guided)
- Launched an Amazon EC2 instance.
- Configured a user data script to display instance details in a browser.

## What I Implemented (DIY / Unguided)
- Launched a second EC2 instance in a different Availability Zone of the same AWS Region.

## Limitations / Not Documented
- Contents of the user-data script itself: **Not documented / Requires clarification** — recommend
  committing the actual script to the repo.
- EBS volume type/size: **Not documented / Requires clarification**.
- Whether the two instances are load-balanced or independently accessed: **Not documented /
  Requires clarification** — the diagram shows them as separate, not fronted by a load balancer.

## Skills Demonstrated
EC2 instance launch and configuration, EC2 user-data bootstrapping, basic multi-AZ deployment
patterns, EBS volume attachment.

## Future Improvements
- Commit the actual user-data (bash) script to the repo for reproducibility.
- Front both instances with an Application Load Balancer to turn this from "two independent
  instances" into an actual highly available pair (natural link to Project 3).
