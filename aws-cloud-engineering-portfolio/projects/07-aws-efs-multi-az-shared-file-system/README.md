# Amazon EFS Multi-AZ Shared File System

> Guided hands-on lab (AWS Skill Builder / SimuLearn) with an independent extension task.

## Overview
Implements Amazon EFS to provide a fully managed, scalable shared file system accessible from
multiple EC2 instances across multiple Availability Zones, simulating access from multiple
branch-location web servers.

## Problem
Multiple web servers across separate Availability Zones need a common, consistently shared file
system (rather than instance-local EBS volumes) so files written by one server are immediately
visible to the others.

## Architecture
Amazon EFS is deployed inside a VPC with mount targets in Availability Zones A, B, and C. Each
zone's web server (Web server 1/2/3) mounts EFS at a shared `data/` path via its AZ's mount target.
Writes from any server (e.g., "A", "B", "C" appended to `data/access.log`) are visible to and
appended from all connected instances.

## AWS Services & Roles
| Service | Role |
|---|---|
| Amazon EFS | Fully managed, elastic NFS file system shared across AZs |
| Amazon EC2 | Web server instances mounting the shared file system |
| Amazon VPC | Network boundary containing EFS mount targets and EC2 instances |

## Network and Security Design
EFS mount targets are created per-AZ inside the VPC, giving each AZ local, low-latency access to
the shared file system rather than routing all traffic through a single AZ's mount target.

## High Availability and Scalability
- Mount targets exist in three AZs, so file system access does not depend on a single AZ being available.
- EFS scales storage capacity automatically (no manual provisioning of size).

## Workflow
1. Web servers in AZ A and AZ B write to a shared `data/` directory via their local EFS mount target.
2. Both servers' writes accumulate in the same underlying `data/access.log`, proving shared,
   consistent state across instances.
3. (DIY) A third EC2 instance's EFS mount target is created/attached in AZ C, and file
   accessibility is verified from that instance too.

## What I Implemented (Guided)
- Launched and configured an Amazon EFS file system.
- Mounted the file system to an Amazon EC2 instance.
- Connected a second EC2 instance to the same file system.
- Shared files between the two EC2 instances.

## What I Implemented (DIY / Unguided)
- Mounted an EFS endpoint to a third EC2 instance and tested that files were accessible from it.

## Limitations / Not Documented
- EFS performance mode (General Purpose vs Max I/O) and throughput mode: **Not documented / Requires clarification**.
- Security group rules controlling NFS (port 2049) access: **Not documented / Requires clarification**.
- Encryption at rest/in transit configuration: **Not documented / Requires clarification**.

## Skills Demonstrated
Amazon EFS provisioning, multi-AZ mount target configuration, shared POSIX file system access
across EC2 instances.

## Future Improvements
- Document/enable encryption in transit for the NFS mounts.
- Document EFS lifecycle management (Infrequent Access) for cost optimization.
