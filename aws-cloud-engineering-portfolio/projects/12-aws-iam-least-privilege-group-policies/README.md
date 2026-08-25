# IAM Least-Privilege Access Control for Support Engineers

> Guided hands-on lab (AWS Skill Builder / SimuLearn) with an independent extension task.

## Overview
Implements an IAM user group (`SupportEngineers`) with least-privilege AWS managed policies to
control which AWS API actions support engineers can perform against EC2 and RDS resources.

## Problem
Support engineers need enough access to diagnose issues (e.g., `DescribeInstances`,
`DescribeDBInstances`) but must not be able to perform destructive or high-impact actions
(e.g., `TerminateInstance`) — a classic least-privilege access control requirement.

## Architecture
An IAM group `SupportEngineers` contains a user (`support-engineer-1`). The `AmazonEC2ReadOnlyAccess`
managed policy is attached to the group, permitting read actions like `ec2:DescribeInstances` while
explicitly denying/excluding mutating actions like `ec2:TerminateInstance`. As the DIY task, the
`AmazonRDSReadOnlyAccess` managed policy is attached, extending the same read-only pattern to RDS
(`rds:DescribeDBInstances` allowed).

## Security Considerations (IAM)
- **Least privilege**: only read (`Describe*`) actions are granted; mutating actions are not.
- **Group-based policy attachment**: the policy is attached to the group, not individual users,
  centralizing access management as team membership changes.
- **AWS managed policies** are used rather than hand-written custom policies, reducing the risk of
  human error in policy JSON, at the cost of less granular control.

## Workflow
1. Create the `SupportEngineers` IAM group and add the `support-engineer-1` user.
2. Attach the `AmazonEC2ReadOnlyAccess` managed policy to the group.
3. Verify: `ec2:DescribeInstances` succeeds; `ec2:TerminateInstance` is denied.
4. (DIY) Attach `AmazonRDSReadOnlyAccess` to the group and verify `rds:DescribeDBInstances` succeeds.

## What I Implemented (Guided)
- Created an IAM group and users.
- Attached an AWS managed policy to the group of users.

## What I Implemented (DIY / Unguided)
- Granted the `SupportEngineers` group read-only access to Amazon RDS.

## Limitations / Not Documented
- MFA enforcement for the support-engineer user: **Not documented / Requires clarification**.
- Resource-level scoping (e.g., restricting to specific EC2/RDS resource ARNs, not account-wide):
  **Not documented / Requires clarification**.
- Password/access-key rotation policy: **Not documented / Requires clarification**.

## Skills Demonstrated
IAM group and user management, AWS managed policy attachment, least-privilege access control
design and verification.

## Future Improvements
- Enforce MFA for the support-engineer user/group.
- Replace or supplement the managed policy with a scoped custom policy limiting actions to specific
  resource ARNs or tags, rather than account-wide read access.
