# AWS Cloud Engineering Portfolio

**A structured collection of 17 hands-on AWS projects spanning compute, networking, databases, storage, security, and generative AI.**

> **Scope disclosure:** All 17 projects in this repository were completed as guided, scenario-based hands-on labs in **AWS Skill Builder (SimuLearn)**. Each lab includes a defined "Solution Request," a set of guided practice steps, and an independent, unguided extension task ("DIY Goal"). Every project below explicitly separates **guided work** from **independent work**, and documents scope honestly, no fabricated metrics, IaC, or production claims.

---

## About This Repository

This repository consolidates 17 individual AWS projects into a single, coherent portfolio — organized by domain, documented to a consistent standard, and indexed for easy review by recruiters, hiring managers, and technical interviewers.

Each project lives in its own self-contained folder under [`projects/`](projects/) with its own `README.md` and architecture diagram, so it can be read independently. This root README ties them together as one unified body of work.

| | |
|---|---|
| **Total projects** | 17 |
| **Domains covered** | Compute & Availability · Data & Storage · Security & Networking · Generative AI · Cost & Economics |
| **Platform** | AWS Skill Builder (SimuLearn) |
| **Documentation standard** | Every project: Overview, Architecture, AWS Services & Roles, Security, Reliability, Guided vs. DIY work, Limitations, Skills Demonstrated |

---

## Project Index

### 🖥️ Compute & Availability
| # | Project | AWS Services |
|---|---|---|---|
| 01 | Auto-Healing and Scaling Applications | EC2 Auto Scaling, CloudWatch |
| 03 | Highly Available Web Applications | ALB, ASG, Route 53, CloudFront, RDS Multi-AZ |
| 14 | Computing Solutions | EC2, Systems Manager |
| 15 | Cloud First Steps | EC2, EBS, Multi-AZ | 

### 🗄️ Data & Storage
| # | Project | AWS Services |
|---|---|---|---|
| 06 | First NoSQL Database | DynamoDB |
| 07 | File Systems in the Cloud | EFS |
| 09 | Databases in Practice | RDS Multi-AZ, Read Replicas |
| 17 | Cloud Computing Essentials | S3 Static Website Hosting |

### 🔐 Security & Networking
| # | Project | AWS Services | 
|---|---|---|---|
| 10 | VPC Network Segmentation with Security Groups | VPC, Subnets, Security Groups | 
| 12 | Core Security Concepts | IAM Groups & Policies | 
| 13 | Connecting VPCs | VPC Peering, Route Tables | 

### 🤖 Generative AI
| # | Project | AWS Services | 
|---|---|---|---|
| 02 | Secure Conversational AI with Guardrails | Amazon Bedrock Guardrails | 
| 04 | Get Started with Generative AI | SageMaker AI, SageMaker Studio | 
| 05 | Generate Code for a Webpage | Bedrock, EC2, Systems Manager | 
| 08 | Explore the Amazon Bedrock Playgrounds | Bedrock Playgrounds, Prompt Management | 
| 11 | ⭐ Create an Enterprise Knowledge Assistant (RAG) | Bedrock Knowledge Bases, OpenSearch Serverless, Titan Embeddings | 

### 💰 Cost & Economics
| # | Project | AWS Services |
|---|---|---|---|
| 16 | Cloud Economics | AWS Pricing Calculator |

⭐ = highest-recommended project to review first (see [Master Strategy](docs/MASTER-STRATEGY.md))

---

## Repository Structure

```text
aws-cloud-engineering-portfolio/
│
├── README.md                          ← You are here (portfolio overview + index)
├── LICENSE
├── docs/
│   └── MASTER-STRATEGY.md             ← Full portfolio strategy, recruiter positioning, publishing order
│
└── projects/
    ├── 01-aws-ec2-auto-scaling-scheduled-policies/
    │   ├── README.md                  ← Full project documentation
    │   └── architecture/
    │       └── architecture-overview.png
    ├── 02-aws-bedrock-guardrails-secure-chatbot/
    │   ├── README.md
    │   └── architecture/
    ├── ...
    └── 17-aws-s3-static-website-hosting-policy/
        ├── README.md
        └── architecture/
```

Each project folder is self-contained and could be extracted into its own standalone repository if desired — this monorepo structure is used purely to present the 17 projects as one coherent, browsable portfolio.

---

## Repository Philosophy

This portfolio deliberately avoids two common pitfalls in student/practice portfolios:

1. **Overclaiming.** These are AWS Skill Builder practice labs, not production systems. Every README says so upfront, and none claim "production-ready," "enterprise-grade," or invented performance metrics. This is a credibility choice, not a limitation — a portfolio that survives follow-up questions is worth more than one that doesn't.
2. **Passive completion vs. independent work.** Each lab includes a guided checklist *and* a "DIY Goal" — an unguided extension task. That DIY step is the one piece of self-directed technical work in every project, so every README calls it out explicitly under **"What I Implemented (DIY / Unguided)."** This is the strongest signal of initiative across the whole portfolio and is highlighted consistently rather than buried.

Where information wasn't available from the original lab materials (e.g., specific hyperparameters, encryption settings, IAM scoping details), it is explicitly marked **`Not documented / Requires clarification`** rather than invented. Several projects include a **Future Improvements** section identifying exactly what would need to be added to turn the lab into a fully reproducible, production-style build (e.g., real Terraform, committed scripts/notebooks, quantitative benchmarks).

---

## Skills Demonstrated Across the Portfolio

| Category | Skills |
|---|---|
| **Compute** | EC2, Auto Scaling (dynamic + scheduled), Launch Templates, AMIs, instance right-sizing, Systems Manager |
| **Networking** | VPC design, public/private subnets, security groups, VPC peering, route tables, ALB, CloudFront, Route 53 |
| **Databases & Storage** | RDS (Multi-AZ, read replicas), DynamoDB (NoSQL data modeling), EFS (multi-AZ shared storage), S3 (static hosting, bucket policies) |
| **Security & Identity** | IAM groups/policies, least-privilege access design, network segmentation, bucket policy scoping |
| **Generative AI / ML** | Amazon Bedrock (prompting, Guardrails, Knowledge Bases/RAG, Prompt Management), Amazon SageMaker (deployment, SDK), OpenSearch Serverless (vector search), Titan Embeddings |
| **Cost & Operations** | AWS Pricing Calculator, cost estimation methodology, elastic vs. static provisioning economics |

---

## Master Portfolio Strategy

For the full recruiter-facing strategy — including which projects to pin/feature, GitHub profile structure, LinkedIn Featured section plan, and a suggested publishing order — see:

📄 **[docs/MASTER-STRATEGY.md](docs/MASTER-STRATEGY.md)**

---

## Author

Maintained as a personal AWS learning and portfolio-building project. Feedback and suggestions welcome via Issues.
