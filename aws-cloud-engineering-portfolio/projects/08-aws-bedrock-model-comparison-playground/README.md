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
