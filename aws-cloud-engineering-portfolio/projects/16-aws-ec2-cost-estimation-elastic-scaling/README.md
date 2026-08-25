# EC2 Cost Estimation: Static vs. Elastic Provisioning

> Guided hands-on lab (AWS Skill Builder / SimuLearn) with an independent extension task.

## Overview
Compares the cost/capacity implications of traditional static IT provisioning against cloud elastic
provisioning, and builds a cost estimate for an Amazon EC2 architecture (via AWS Pricing Calculator)
based on peak customer demand.

## Problem
Traditional, statically-provisioned infrastructure is sized for peak demand, leaving unused capacity
during low-demand periods and unserved customers during demand spikes beyond the fixed line. Cloud
elastic infrastructure (an Auto Scaling group of `t3.medium` web servers) can track demand more
closely, but its cost implications need to be estimated and understood before being adopted.

## What I Implemented (Guided)
- Created logical pricing groups.
- Created a cost estimate for Amazon EC2 usage based on a given architecture (`t3.medium` web
  servers behind an Auto Scaling group).

## What I Implemented (DIY / Unguided)
- Changed the EC2 instance type in the price estimate from `t3.medium` to `t2.micro` and generated
  a new price-estimate link to compare cost impact.

## Key Concepts Illustrated
- Static (traditional IT) provisioning: fixed resource line causes both **unserved customers**
  during spikes and **unused capacity** during troughs.
- Elastic (cloud) provisioning: infrastructure tracks the demand curve directly, with no upfront
  expenditure required to size for peak.

## Limitations / Not Documented
- The actual dollar cost estimates produced for `t3.medium` vs `t2.micro`: **Not documented /
  Requires clarification** — recommend saving and linking the actual AWS Pricing Calculator
  estimate URLs in this repo.
- Assumed usage hours/Region used in the estimate: **Not documented / Requires clarification**.

## Skills Demonstrated
AWS Pricing Calculator usage, cost estimation methodology, understanding of elastic vs. static
provisioning economics, Total Cost of Ownership (TCO) reasoning fundamentals.

## Future Improvements
- Include the actual saved AWS Pricing Calculator estimate links/screenshots and dollar figures for
  both instance types, since the estimate output itself is the actual deliverable of this lab and
  is currently missing from the documentation.
