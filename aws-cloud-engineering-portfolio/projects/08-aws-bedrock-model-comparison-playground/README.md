# Explore the Amazon Bedrock Playgrounds

### 1. Repository Name
`aws-bedrock-model-comparison-playground`

### 2. Project Category
Generative AI / Model Evaluation & Prompt Management

### 3. Professional Portfolio Description
Used Amazon Bedrock's playgrounds to evaluate and compare multiple foundation models side-by-side, tune hyperparameters, and build a reusable, versioned prompt for model selection decisions.

### 4. Recommended Repository Structure
```text
aws-bedrock-model-comparison-playground/
├── README.md
├── architecture/
│   └── bedrock-playground-comparison-flow.png
└── documentation/
    └── prompt-versions.md
```

### 5. Complete README.md
```markdown
# Amazon Bedrock Playgrounds — Multi-Model Comparison and Prompt Management

> Guided hands-on lab (AWS Skill Builder / SimuLearn) with an independent extension task.

## Overview
Uses Amazon Bedrock's playgrounds to securely evaluate and compare multiple foundation models,
helping select the best model for a given use case, and to build/version a reusable prompt.

## Problem
Choosing a foundation model for a specific use case requires comparing quality, style, and
hyperparameter behavior across candidate models before committing to one in an application.

## Architecture
Users access Amazon Bedrock and interact with individual model playgrounds (single-model
exploration/testing) as well as a compare mode that invokes two text models against the same
prompt and displays outputs side-by-side. A separate chat-based AI flow is used for conversational
testing. Reusable prompts are created, tested, and versioned via Prompt Management.

## AWS Services & Roles
| Service | Role |
|---|---|
| Amazon Bedrock (Playgrounds) | Interactive environment for exploring/testing individual foundation models |
| Amazon Bedrock (Compare mode) | Invokes two models against the same prompt for side-by-side comparison |
| Amazon Bedrock (Prompt Management) | Creates, versions, and reuses prompts with variables |

## Workflow
1. Access models through the Bedrock console and explore/test individual models.
2. Analyze and apply model hyperparameters through the console.
3. Enable compare mode, select two text models, and compare their responses to the same input.
4. Create a reusable prompt with variables and save it as a version via Prompt Management.

## What I Implemented (Guided)
- Launched and navigated two Amazon Bedrock playgrounds.
- Analyzed and applied model hyperparameters through the console.
- Enabled compare mode and selected two text models to compare responses.
- Created a reusable prompt with variables and saved it as a version using Prompt Management.

## What I Implemented (DIY / Unguided)
- Created a new prompt named `ProductDescriptionWriter`, added prompt text, and created a version
  of the prompt.

## Limitations / Not Documented
- Which specific hyperparameters (temperature, top-p, max tokens) were tuned and their final
  values: **Not documented / Requires clarification**.
- Which two models were compared and the qualitative outcome: **Not documented / Requires clarification**.

## Skills Demonstrated
Amazon Bedrock playgrounds, model evaluation/comparison methodology, hyperparameter tuning,
prompt engineering, Prompt Management (versioning, variables).

## Future Improvements
- Record the actual hyperparameter values and comparison outcomes for future reference/reuse.
- Export the `ProductDescriptionWriter` prompt definition into the repo as a documented artifact.
```

### 6–9. Details
Diagram filename: `bedrock-playground-comparison-flow.png`; Title: "Bedrock Playground Model Comparison and Prompt Management Flow"; GitHub caption: "Comparing foundation models and managing reusable prompts in Amazon Bedrock." LinkedIn caption: "Used Amazon Bedrock's compare mode and Prompt Management to evaluate foundation models and build a reusable, versioned prompt."

### 10. LinkedIn Portfolio Description
Used Amazon Bedrock's playgrounds and compare mode to evaluate foundation models side-by-side and tune hyperparameters, then created and versioned a reusable `ProductDescriptionWriter` prompt using Prompt Management. Skills: Amazon Bedrock, model evaluation, prompt engineering. *(AWS Skill Builder hands-on lab.)*

### 11. Skills Demonstrated
Bedrock playgrounds, prompt management, model comparison methodology.

### 12. Technical Weaknesses and Gaps
No recorded outcome of the comparison (which model "won" and why) — currently this is a process description without a result, which weakens the analytical narrative.

### 13. Recommended Improvements
Document actual comparison outcomes and hyperparameter values used.

---
