# Get Started with Generative AI

### 1. Repository Name
`aws-sagemaker-foundation-model-prompting`

### 2. Project Category
Generative AI / Model Deployment & Prompt Engineering

### 3. Professional Portfolio Description
Deployed a foundation model on Amazon SageMaker AI and experimented with multiple prompting techniques via a SageMaker Studio notebook, comparing behavior across two different model endpoints.

### 4. Recommended Repository Structure
```text
aws-sagemaker-foundation-model-prompting/
├── README.md
├── architecture/
│   └── sagemaker-deployment-flow.png
└── documentation/
    └── prompting-techniques-notes.md
```

### 5. Complete README.md
```markdown
# Foundation Model Deployment and Prompting on Amazon SageMaker AI

> Guided hands-on lab (AWS Skill Builder / SimuLearn) with an independent extension task.

## Overview
Deployed foundation models as SageMaker endpoints and used a SageMaker Studio JupyterLab notebook
with the SageMaker Python SDK to experiment with different prompting techniques.

## Problem
Evaluate how to configure and interact with a hosted foundation model endpoint, and how prompt
design affects model output, using AWS's managed ML platform rather than a third-party API.

## Architecture
Amazon SageMaker Studio is used to configure and launch a notebook. From the notebook (via the
SageMaker Python SDK) and from SageMaker Studio directly, a foundation model is deployed to a
SageMaker Model Endpoint (DeepSeek was deployed via Studio; LLaMA via the notebook), and prompts
are sent to the deployed endpoint(s) to compare responses.

## AWS Services & Roles
| Service | Role |
|---|---|
| Amazon SageMaker AI / Studio | Managed environment for model deployment and experimentation |
| SageMaker Model Endpoint | Hosts the deployed foundation model for inference |
| SageMaker Studio Notebook (JupyterLab) | Used with the SageMaker Python SDK to deploy/prompt a model programmatically |

## Workflow
1. Launch SageMaker Studio.
2. Deploy a model directly from Studio to a Model Endpoint (DeepSeek).
3. Connect to a JupyterLab notebook; use the SageMaker Python SDK to deploy a second model (LLaMA)
   and prompt it programmatically.
4. Compare outputs across different prompting techniques.

## What I Implemented (Guided)
- Set up the necessary configurations for model deployment in Amazon SageMaker Studio.
- Deployed a model endpoint with the SageMaker Python SDK.
- Used a SageMaker Studio notebook to experiment with different prompting techniques.

## What I Implemented (DIY / Unguided)
- Deployed the Mistral Lite model in SageMaker Studio, used the Predictor class in the SageMaker
  Python SDK with the new endpoint, and tested it with the same prompting techniques to evaluate
  differences versus DeepSeek/LLaMA.

## Limitations / Not Documented
- Instance type / endpoint sizing used: **Not documented / Requires clarification**.
- Specific prompting techniques tested (zero-shot, few-shot, chain-of-thought, etc.): **Not
  documented / Requires clarification** — recommend explicitly logging these in the notebook.
- Endpoint cleanup/cost-management steps: **Not documented / Requires clarification**.

## Skills Demonstrated
Amazon SageMaker AI, SageMaker Studio, SageMaker Python SDK, foundation model deployment,
prompt engineering fundamentals, comparative model evaluation.

## Future Improvements
- Publish the actual notebook (.ipynb) with prompts and outputs included, rather than only a
  summary — this is the single highest-value addition for this repo.
- Document endpoint instance types and estimated cost per hour.
```

### 6–9. Details
Diagram filename: `sagemaker-deployment-flow.png`; Title: "SageMaker Studio Model Deployment and Prompting Flow"; GitHub caption: "Deploying and prompting foundation models via SageMaker Studio and the Python SDK." LinkedIn caption: "Deployed and compared multiple foundation models on Amazon SageMaker, including an independent Mistral Lite deployment."

### 10. LinkedIn Portfolio Description
Deployed foundation models (DeepSeek, LLaMA, and independently Mistral Lite) to Amazon SageMaker endpoints and used the SageMaker Python SDK from a Studio notebook to test and compare prompting techniques across models. Skills: Amazon SageMaker, prompt engineering, ML model deployment. *(AWS Skill Builder hands-on lab.)*

### 11. Skills Demonstrated
SageMaker deployment, SDK usage, prompt engineering.

### 12. Technical Weaknesses and Gaps
No actual notebook/code artifact included — this is the weakest point of the repo as currently scoped; a documentation-only README about a coding exercise undercuts the "hands-on" claim.

### 13. Recommended Improvements
Attach the real `.ipynb`; add example prompts and outputs.

---
