# Secure Conversational AI with Amazon Bedrock Guardrails

> Guided hands-on lab (AWS Skill Builder / SimuLearn) with an independent extension task.

## Overview
This project safeguards interactions between end users and a foundation-model-backed assistant by
routing every request/response pair through Amazon Bedrock Guardrails before it reaches the user.

## Problem
Direct, unfiltered access to a foundation model risks the assistant answering out-of-scope or
sensitive queries (e.g., regulated financial advice), leaking PII, or producing unsafe content.

## Architecture
User input is sent to foundation-model inference; the generated response is evaluated by Amazon
Bedrock Guardrails against a policy set (Denied Topics, Content Filters, PII Redaction, Word Filter)
before the final, filtered response is returned to the user.

## AWS Services & Roles
| Service | Role |
|---|---|
| Amazon Bedrock (Foundation Model inference) | Generates the raw AI response |
| Amazon Bedrock Guardrails | Evaluates input/output against configured safety policies |

## Guardrail Policies Configured
- Denied Topics
- Content Filters
- PII Redaction
- Word Filter

## Workflow
1. User provides input.
2. Foundation model generates a response.
3. The user input and the model's response are both evaluated against Guardrails policies.
4. Only the approved/filtered content is returned as the final response.

## Security Considerations
- Guardrails acts as a policy-enforcement layer independent of the model's own alignment —
  reduces reliance on prompt-only safety instructions.
- PII redaction addresses data-privacy exposure risk in employee/customer interactions.

## What I Implemented (Guided)
- Created and customized model safeguards using Amazon Bedrock Guardrails.
- Validated the safeguard policies by testing the created guardrails.

## What I Implemented (DIY / Unguided)
- Created a new guardrail specifically to block financial investment advice and tested it.

## Limitations / Not Documented
- Specific foundation model used for inference: **Not documented / Requires clarification**.
- Guardrail versioning/deployment strategy: **Not documented / Requires clarification**.
- No logging/audit trail for blocked requests is shown: **Not documented / Requires clarification**.

## Skills Demonstrated
Amazon Bedrock, Guardrails policy configuration (denied topics, content filtering, PII redaction),
responsible-AI / AI governance fundamentals.

## Future Improvements
- Add CloudWatch logging of guardrail interventions for auditability.
- Test guardrail bypass/adversarial prompts to document edge-case behavior.
