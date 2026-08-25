# VPC Network Segmentation with Security Groups

### 1. Repository Name
`aws-vpc-public-private-subnet-security`

### 2. Project Category
Networking & Security / VPC Fundamentals

### 3. Professional Portfolio Description
Designed a VPC with segmented public and private subnets, using security groups as stateful firewalls to control access between a public web server and a private database instance.

### 4. Recommended Repository Structure
```text
aws-vpc-public-private-subnet-security/
├── README.md
└── architecture/
    └── vpc-subnet-security-group-topology.png
```

### 5. Complete README.md
```markdown
# VPC Public/Private Subnet Segmentation with Security Groups

> Guided hands-on lab (AWS Skill Builder / SimuLearn).

## Overview
Implements a VPC (`10.10.0.0/16`) with a public subnet (`10.10.0.0/24`) hosting a web server and a
private subnet (`10.10.2.0/24`) hosting a database, using security groups to control traffic
between tiers and an Internet Gateway/router for inbound public access.

## Problem
A database should never be directly internet-accessible; only the web tier should face the
internet, and only specific, minimal traffic should be allowed between tiers.

## Network and Security Design
- Internet traffic enters via an Internet Gateway and router into the public subnet.
- The Web Server (public subnet) has a security group allowing `HTTP:80:Allow`.
- The Database (private subnet) has a separate security group allowing `TCP:3306:Allow`
  (MySQL/Aurora port) — implying access is scoped to the web tier, not the open internet.
- The two security groups gate the connection between the web server and database ("Connected!").

## AWS Services & Roles
| Service | Role |
|---|---|
| Amazon VPC | Network isolation boundary (`10.10.0.0/16`) |
| Public Subnet | Hosts internet-facing resources (web server) |
| Private Subnet | Hosts internal-only resources (database) |
| Internet Gateway + Router | Provides internet ingress/egress for the public subnet |
| Security Groups | Stateful, instance-level firewalls scoping allowed ports per tier |

## Workflow
1. Inbound internet traffic reaches the Internet Gateway, then the router.
2. Traffic to the web server is allowed only on port 80 (HTTP) per its security group.
3. The web server connects to the database on port 3306 (TCP), permitted by the database's
   security group.
4. The database has no direct path from the public internet — it is only reachable from within the VPC.

## What I Implemented
- Reviewed/configured VPC CIDR ranges, public and private subnet allocation.
- Configured security groups scoping HTTP (80) to the web tier and TCP (3306) to the database tier.

## Limitations / Not Documented
- Route table configuration for the private subnet (e.g., NAT Gateway for outbound-only internet):
  **Not documented / Requires clarification**.
- Network ACLs (subnet-level rules) in addition to security groups: **Not documented / Requires clarification**.
- Source scoping of the security group rules (e.g., is port 3306 open to the whole VPC or only the
  web server's security group?): **Not documented / Requires clarification** — this is the single
  most important security detail to confirm and document.

## Skills Demonstrated
VPC design, public/private subnet segmentation, security group configuration, basic network
security reasoning for a two-tier application.

## Future Improvements
- Explicitly document security group rules with source references (SG-to-SG, not just port/protocol).
- Add a NAT Gateway for the private subnet if outbound internet access is needed by the database tier.
- Add Network ACLs as a second layer of defense and document the difference from security groups.
```

### 6–9. Details
Diagram filename: `vpc-subnet-security-group-topology.png`; Title: "VPC Public/Private Subnet Topology with Security Groups"; GitHub caption: "Two-tier VPC design isolating a database in a private subnet behind security groups." LinkedIn caption: "Designed a VPC with public/private subnet segmentation and security groups to isolate a database tier from the internet."

### 10. LinkedIn Portfolio Description
Designed a two-tier VPC architecture separating a public web server from a private database using subnet segmentation and security groups scoped to HTTP and MySQL ports respectively. Skills: Amazon VPC, subnetting, security groups, network security fundamentals. *(AWS Skill Builder hands-on lab.)*

### 11. Skills Demonstrated
VPC subnetting, security groups, network segmentation.

### 12. Technical Weaknesses and Gaps
Security group source scoping is not documented (is 3306 open to any VPC resource, or restricted to the web SG?) — this is the exact kind of detail that separates "I clicked through a lab" from "I understand least-privilege networking," so it needs to be nailed down before publishing.

### 13. Recommended Improvements
Document exact SG source rules; add NACLs; add a NAT Gateway if applicable.

---
