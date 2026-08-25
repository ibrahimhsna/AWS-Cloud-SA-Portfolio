# Connecting VPCs

### 1. Repository Name
`aws-vpc-peering-cross-department-access`

### 2. Project Category
Networking / VPC Peering

### 3. Professional Portfolio Description
Implemented VPC peering to enable controlled cross-VPC communication between Marketing, Finance, and Developer VPCs, allowing specific departments to reach a Financial Services server without merging networks.

### 4. Recommended Repository Structure
```text
aws-vpc-peering-cross-department-access/
├── README.md
└── architecture/
    └── vpc-peering-topology.png
```

### 5. Complete README.md
```markdown
# Cross-Department VPC Peering

> Guided hands-on lab (AWS Skill Builder / SimuLearn) with an independent extension task.

## Overview
Implements VPC peering connections to allow Marketing and Developer VPC resources to reach a
Financial Services server hosted in a separate Finance VPC, without exposing traffic to the public
internet.

## Problem
Three departments — Marketing, Finance, Developer — operate in separate VPCs with distinct CIDR
ranges. Marketing and Developer instances need access to a server in the Finance VPC, but the VPCs
should remain otherwise isolated (no VPC merge, no third-party network transit).

## Architecture
- Marketing VPC: `10.10.0.0/16`
- Finance VPC: `172.31.0.0/16`
- Developer VPC: `192.168.0.0/20`

A VPC peering connection is established between Marketing and Finance, and a separate peering
connection between Finance and Developer. Each VPC's route table is updated with a rule pointing
non-local peered CIDR ranges to the corresponding peering connection ("Add rule" / "Allow
communication" in the diagram).

## AWS Services & Roles
| Service | Role |
|---|---|
| Amazon VPC | Isolated network per department |
| VPC Peering Connection | Point-to-point private connectivity between two VPCs |
| Route Tables | Direct traffic destined for a peered VPC's CIDR through the peering connection |

## Network and Security Design
Peering is point-to-point and **non-transitive** by design (an AWS VPC peering property) —
Marketing cannot reach Developer through Finance simply because both are peered with Finance; that
would require a separate, explicit peering connection or a transit gateway.

## Workflow
1. Establish a VPC peering connection between Marketing VPC and Finance VPC.
2. Update route tables in both VPCs to route peered-CIDR traffic through the peering connection.
3. Verify the Marketing server can reach the Finance server.
4. (DIY) Establish and route a peering connection between Developer VPC and Finance VPC.

## What I Implemented (Guided)
- Set up a VPC peering connection.
- Made sure traffic is properly routed between the peered VPCs.

## What I Implemented (DIY / Unguided)
- Configured VPC peering between the Developer and Finance department VPCs.

## Limitations / Not Documented
- Security group rules gating access to the Financial Services server (beyond routing reachability):
  **Not documented / Requires clarification**.
- Whether Marketing and Developer VPCs are also peered to each other directly: **Not documented /
  Requires clarification** — based on the architecture, they should not be (non-transitive peering).
- DNS resolution settings for the peering connections: **Not documented / Requires clarification**.

## Skills Demonstrated
VPC peering configuration, route table management for cross-VPC routing, understanding of
non-transitive peering behavior, multi-VPC network segmentation by department.

## Future Improvements
- Document security group rules restricting exactly which instances/ports can reach the Financial
  Services server, not just VPC-level reachability.
- Consider and document why VPC peering (vs. a Transit Gateway) is appropriate at this scale, and
  when that choice would need to change.
```

### 6–9. Details
Diagram filename: `vpc-peering-topology.png`; Title: "Cross-Department VPC Peering Topology"; GitHub caption: "Non-transitive VPC peering connecting Marketing and Developer VPCs to a shared Finance VPC." LinkedIn caption: "Set up cross-department VPC peering with proper route-table configuration, connecting Marketing and Developer VPCs to a Finance VPC."

### 10. LinkedIn Portfolio Description
Implemented VPC peering and route-table configuration to give Marketing and Developer department VPCs controlled access to a server in a separate Finance VPC, independently extending the peering setup to the Developer VPC. Skills: Amazon VPC, VPC peering, route tables, network segmentation. *(AWS Skill Builder hands-on lab.)*

### 11. Skills Demonstrated
VPC peering, route table configuration, multi-VPC design.

### 12. Technical Weaknesses and Gaps
Security-group-level access control at the destination server is undocumented — routing reachability alone is not the same as "properly secured," and this repo would benefit from stating that distinction explicitly rather than implying routing = access control.

### 13. Recommended Improvements
Document destination security group rules; discuss Transit Gateway as the scale-up alternative and why it wasn't needed here.

---
