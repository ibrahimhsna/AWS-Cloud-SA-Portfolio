# Databases in Practice

### 1. Repository Name
`aws-rds-multi-az-read-replica-setup`

### 2. Project Category
Databases / Relational (Amazon RDS)

### 3. Professional Portfolio Description
Migrated a workload to Amazon RDS with a Multi-AZ deployment for automated failover and a read replica to offload read traffic, plus configured automated backups.

### 4. Recommended Repository Structure
```text
aws-rds-multi-az-read-replica-setup/
├── README.md
├── architecture/
│   └── rds-multi-az-read-replica.png
└── documentation/
    └── backup-configuration.md
```

### 5. Complete README.md
```markdown
# Amazon RDS Multi-AZ Deployment with Read Replica

> Guided hands-on lab (AWS Skill Builder / SimuLearn) with an independent extension task.

## Overview
Migrates a customer application to Amazon RDS to automate routine database administration tasks,
while implementing a Multi-AZ deployment and a read replica to improve availability and read performance.

## Problem
A self-managed database requires manual administration (patching, backups, failover) and a single
instance cannot separate read load from write load, limiting both availability and read scalability.

## Architecture
The customer application sends write operations to the primary Amazon RDS DB instance (Availability
Zone B). Amazon RDS Multi-AZ provides synchronous replication to a standby replica in Availability
Zone C, which becomes the failover instance if the primary fails ("resume read/write operations" →
"redirect requests"). A read replica in Availability Zone A serves read operations independently of
the primary, offloading read traffic.

## AWS Services & Roles
| Service | Role |
|---|---|
| Amazon RDS (Primary, Multi-AZ) | Handles write operations; synchronously replicates to standby |
| Amazon RDS (Standby replica) | Automated failover target in a separate AZ |
| Amazon RDS (Read replica) | Serves read operations, separate from the primary/standby pair |

## Reliability and Scalability
- Multi-AZ synchronous replication to a standby in a separate AZ provides automated failover for
  write availability.
- A read replica in a third AZ offloads read traffic from the primary, improving read performance
  under load.

## Workflow
1. Application sends writes to the primary RDS instance.
2. Primary synchronously replicates to the Multi-AZ standby.
3. On primary failure, RDS redirects requests to the standby, which resumes read/write operations.
4. Read-only queries are separately routed to the read replica.

## What I Implemented (Guided)
- Explored AWS database offerings.
- Launched an Amazon RDS instance.
- Configured a Multi-AZ deployment.
- Configured Amazon RDS backups.

## What I Implemented (DIY / Unguided)
- Created a read replica of the primary database using a `db.t3.xlarge` instance.

## Limitations / Not Documented
- Backup retention window and snapshot schedule: **Not documented / Requires clarification**.
- Database engine (MySQL/PostgreSQL/other): **Not documented / Requires clarification**.
- Application-level logic for routing reads vs writes to the correct endpoint: **Not documented /
  Requires clarification**.

## Skills Demonstrated
Amazon RDS provisioning, Multi-AZ high-availability configuration, read replica setup for read
scaling, automated backup configuration.

## Future Improvements
- Document the actual backup retention/window chosen and why.
- Add connection-routing logic (e.g., via a proxy or app config) to actually separate read/write traffic.
```

### 6–9. Details
Diagram filename: `rds-multi-az-read-replica.png`; Title: "RDS Multi-AZ with Read Replica Architecture"; GitHub caption: "RDS Multi-AZ failover paired with a dedicated read replica for read scaling." LinkedIn caption: "Configured Amazon RDS with Multi-AZ failover and a read replica to separate availability from read scalability."

### 10. LinkedIn Portfolio Description
Migrated a database workload to Amazon RDS with a Multi-AZ deployment for automated failover and configured backups, then independently created a `db.t3.xlarge` read replica to offload read traffic from the primary. Skills: Amazon RDS, Multi-AZ, read replicas, database administration. *(AWS Skill Builder hands-on lab.)*

### 11. Skills Demonstrated
RDS Multi-AZ, read replicas, automated backups.

### 12. Technical Weaknesses and Gaps
Database engine and backup retention window are unstated — both are basic facts a hiring manager will expect you to know cold about your own project.

### 13. Recommended Improvements
Document engine, instance class rationale, backup window; describe an actual failover test if performed.

---
