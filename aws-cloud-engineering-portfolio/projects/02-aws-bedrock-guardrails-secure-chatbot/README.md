# Secure Conversational AI with Guardrails

### 1. Repository Name
`aws-bedrock-guardrails-secure-chatbot`

### 2. Project Category
Generative AI / AI Safety & Governance

### 3. Professional Portfolio Description
Implementation of Amazon Bedrock Guardrails to enforce content-safety and topic policies (denied topics, content filters, PII redaction, word filters) around a foundation-model-based conversational assistant.

### 4. Recommended Repository Structure
```text
aws-bedrock-guardrails-secure-chatbot/
├── README.md
├── architecture/
│   └── guardrails-request-flow.png
└── documentation/
    └── guardrail-policy-config.md
```

### 5. Complete README.md
```markdown
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
```

### 6–9. Technical Explanation / Services / File Naming / Diagram
- Diagram filename: `guardrails-request-flow.png`; Title: "Bedrock Guardrails Enforcement Flow"; GitHub caption: "Request/response flow with Bedrock Guardrails policy enforcement." LinkedIn caption: "How I used Amazon Bedrock Guardrails to keep a conversational AI assistant on-topic and PII-safe."
- Alternatives not selected: custom prompt-engineering-only safety layer (weaker, non-declarative) — Guardrails chosen for policy-based, auditable enforcement.

### 10. LinkedIn Portfolio Description
Implemented Amazon Bedrock Guardrails around a conversational AI assistant to enforce denied-topic, content-filter, PII-redaction, and word-filter policies, then extended it with a custom guardrail to block financial-advice queries. Skills: Amazon Bedrock, AI safety/governance, responsible AI. *(AWS Skill Builder hands-on lab.)*

### 11. Skills Demonstrated
Bedrock Guardrails, AI governance policy design.

### 12. Technical Weaknesses and Gaps
No observability/logging of guardrail interventions documented; model choice unstated; no adversarial testing evidence beyond the one DIY policy.

### 13. Recommended Improvements
Add logging, document the specific FM, test adversarial prompts and record results.

---
