# Computing Solutions

### 1. Repository Name
`aws-ec2-instance-type-scaling-ssm`
*(Note: this repo covers vertical resizing of a single EC2 instance and Session Manager access — distinct from Project 1's Auto Scaling group work, so keep them separate rather than merging.)*

### 2. Project Category
Compute / Instance Right-Sizing & Secure Access

### 3. Professional Portfolio Description
Selected an appropriate EC2 instance type based on workload attributes, connected to the instance securely via AWS Systems Manager (no SSH), and vertically scaled the instance from `t3.micro` to `m4.large` to improve performance.

### 4. Recommended Repository Structure
```text
aws-ec2-instance-type-scaling-ssm/
├── README.md
└── architecture/
    └── instance-connect-and-resize-flow.png
```

### 5. Complete README.md
```markdown
# EC2 Instance Type Selection, Secure Access, and Vertical Scaling

> Guided hands-on lab (AWS Skill Builder / SimuLearn) with an independent extension task.

## Overview
Covers selecting an EC2 instance type based on workload requirements, connecting to the instance
via multiple secure access paths, and vertically scaling the instance to a larger type to improve
application performance.

## Problem
An application running on a `t3.micro` instance needs improved performance; rather than default to
"pick a bigger instance," the workload's attributes should first be used to filter/identify
appropriate instance types, and access to the instance should not depend on SSH key management.

## Architecture
A user connects to the EC2 instance via three possible paths shown in the diagram: a terminal,
EC2 Instance Connect, or AWS Systems Manager — all converging on the instance itself. The instance
also exposes metadata, retrievable via the instance metadata service and viewable through a web
browser path. The instance is then resized from `t3.micro` to `m4.large`.

## AWS Services & Roles
| Service | Role |
|---|---|
| Amazon EC2 | Compute instance being sized and accessed |
| AWS Systems Manager | Secure, keyless connection path to the instance |
| EC2 Instance Connect | Alternative browser-based/CLI secure connection path |
| EC2 Instance Metadata Service | Provides instance metadata (type, region, etc.) to the user/browser |

## Workflow
1. Filter and identify EC2 instance types based on workload attributes (vCPU, memory, network needs).
2. Connect to the EC2 instance using Session Manager and view its metadata.
3. Start/stop the instance using the EC2 console.
4. (DIY) Change the instance type to a larger, general-purpose `m4.large` instance.

## What I Implemented (Guided)
- Filtered and identified EC2 instance types based on workload attributes.
- Connected to an EC2 instance using Session Manager and viewed its metadata.
- Started and stopped an EC2 instance using the Amazon EC2 console.

## What I Implemented (DIY / Unguided)
- Changed the Amazon EC2 instance type to a larger (`m4.large`) general-purpose instance.

## Limitations / Not Documented
- The specific workload attributes used to select the original instance type: **Not documented /
  Requires clarification**.
- Any downtime incurred during the resize (stop → change type → start): **Not documented /
  Requires clarification** — worth noting explicitly, since `m4.large` is a different instance
  family/generation than `t3.micro`, and not all resizes are hardware-compatible without a stop.
- Cost delta between `t3.micro` and `m4.large`: **Not documented / Requires clarification**.

## Skills Demonstrated
EC2 instance type selection methodology, secure instance access via Systems Manager, EC2 lifecycle
management (start/stop/resize), vertical scaling fundamentals.

## Future Improvements
- Document the workload attributes and the specific reasoning for selecting `m4.large` over other
  general-purpose or compute-optimized types.
- Benchmark before/after performance to substantiate the "enhance performance" goal with data.
```

### 6–9. Details
Diagram filename: `instance-connect-and-resize-flow.png`; Title: "EC2 Secure Connection Paths and Instance Resize Flow"; GitHub caption: "Multiple secure paths to an EC2 instance, followed by a vertical resize from t3.micro to m4.large." LinkedIn caption: "Connected securely to an EC2 instance via Systems Manager and vertically scaled it from t3.micro to m4.large."

### 10. LinkedIn Portfolio Description
Selected an EC2 instance type based on workload attributes, connected securely via AWS Systems Manager, and independently resized the instance from t3.micro to a larger m4.large general-purpose instance to improve application performance. Skills: Amazon EC2, Systems Manager, instance right-sizing. *(AWS Skill Builder hands-on lab.)*

### 11. Skills Demonstrated
EC2 instance selection, Systems Manager, vertical scaling.

### 12. Technical Weaknesses and Gaps
No before/after performance data to actually substantiate the "enhance performance" claim from the original solution request — currently an assumption, not a demonstrated result.

### 13. Recommended Improvements
Add a simple before/after benchmark (even a basic load test) to make the performance claim verifiable.

---
