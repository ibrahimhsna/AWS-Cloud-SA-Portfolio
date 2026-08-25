# Create an Enterprise Knowledge Assistant

### 1. Repository Name
`aws-bedrock-rag-knowledge-assistant`

### 2. Project Category
Generative AI / Retrieval-Augmented Generation (RAG)

### 3. Professional Portfolio Description
Built a RAG-based enterprise knowledge assistant using an Amazon Bedrock knowledge base backed by Amazon OpenSearch Serverless as a vector store, enabling natural-language queries over sales documents stored in Amazon S3.

### 4. Recommended Repository Structure
```text
aws-bedrock-rag-knowledge-assistant/
├── README.md
├── architecture/
│   └── rag-knowledge-base-architecture.png
└── documentation/
    └── data-source-sync-notes.md
```

### 5. Complete README.md
```markdown
# Enterprise Knowledge Assistant with Amazon Bedrock Knowledge Bases (RAG)

> Guided hands-on lab (AWS Skill Builder / SimuLearn) with an independent extension task.

## Overview
Implements a Retrieval-Augmented Generation (RAG) knowledge assistant using an Amazon Bedrock
knowledge base to support natural-language queries over sales documents stored in Amazon S3, with
vector embeddings indexed in Amazon OpenSearch Serverless.

## Problem
Foundation models cannot answer questions about private, organization-specific documents (e.g.,
internal sales reports) out of the box. RAG grounds model responses in retrieved, relevant document
content instead of relying solely on the model's training data.

## Architecture
Source documents (a sales-details CSV and a sales-report PDF) are uploaded to separate S3 buckets.
An Amazon Bedrock knowledge base is configured with these S3 locations as data sources; on sync, the
Amazon Titan Embeddings foundation model converts document content into vector embeddings, which are
stored in Amazon OpenSearch Serverless. At query time, a sales representative's natural-language
question is sent to Amazon Nova Lite (the query foundation model), which retrieves relevant
information from the knowledge base (via the vector store) before generating a grounded response.

## AWS Services & Roles
| Service | Role |
|---|---|
| Amazon Bedrock Knowledge Bases | Orchestrates data-source ingestion, embedding sync, and RAG retrieval |
| Amazon S3 | Stores raw source documents (CSV, PDF) as knowledge base data sources |
| Amazon Titan Embeddings | Converts document content into vector embeddings |
| Amazon OpenSearch Serverless | Vector store for embedded document chunks, used for retrieval |
| Amazon Nova Lite (FM) | Query-time foundation model that generates the grounded answer |

## Workflow
1. Upload documents (`Sales details.csv`, `Sales report.pdf`) to their respective S3 buckets.
2. Enable required models in the Bedrock console.
3. Create a Bedrock knowledge base and define S3 as its data source.
4. Sync the data source — Titan Embeddings vectorizes content into OpenSearch Serverless.
5. A sales representative queries the assistant in natural language; Nova Lite retrieves relevant
   embedded content and generates a response grounded in it.
6. Test accuracy by asking sales-related questions and validating the responses.

## What I Implemented (Guided)
- Uploaded documents to an Amazon S3 bucket.
- Enabled models on the Amazon Bedrock console.
- Created an Amazon Bedrock knowledge base.
- Used Amazon OpenSearch Serverless as a vector store.
- Tested knowledge base accuracy by asking sales-related questions.

## What I Implemented (DIY / Unguided)
- Uploaded a `Sales_Report.pdf` file to the sales-reports bucket.
- Added a second data source to the knowledge base (`sales-kb`).
- Synced the new data source and re-asked the annual-sales question to confirm the assistant
  incorporated the new document.

## Limitations / Not Documented
- Chunking strategy (fixed-size, semantic, hierarchical) for the knowledge base: **Not documented /
  Requires clarification**.
- Access control on the knowledge base/OpenSearch collection: **Not documented / Requires clarification**.
- Evaluation methodology beyond manual spot-checking of answers: **Not documented / Requires clarification**.

## Skills Demonstrated
Retrieval-Augmented Generation (RAG) architecture, Amazon Bedrock Knowledge Bases, Amazon
OpenSearch Serverless as a vector store, S3 data source management, multi-source knowledge base
sync and validation.

## Future Improvements
- Document and tune the chunking strategy for better retrieval precision.
- Add an evaluation set (question/expected-answer pairs) to measure retrieval quality quantitatively.
- Apply least-privilege IAM/OpenSearch access policies and document them.
```

### 6–9. Details
Diagram filename: `rag-knowledge-base-architecture.png`; Title: "RAG Knowledge Assistant — Bedrock Knowledge Base + OpenSearch Serverless"; GitHub caption: "RAG pipeline: S3 sources → Titan embeddings → OpenSearch Serverless → Nova Lite query response." LinkedIn caption: "Built a RAG-based enterprise knowledge assistant on Amazon Bedrock, then extended it with a second synced data source."

### 10. LinkedIn Portfolio Description
Built a Retrieval-Augmented Generation (RAG) knowledge assistant using Amazon Bedrock Knowledge Bases, Amazon Titan Embeddings, and Amazon OpenSearch Serverless as a vector store to answer natural-language questions over sales documents in S3, then independently added and synced a second data source. Skills: RAG architecture, Amazon Bedrock, OpenSearch Serverless, vector search. *(AWS Skill Builder hands-on lab.)*

### 11. Skills Demonstrated
RAG design, Bedrock Knowledge Bases, OpenSearch Serverless, vector embeddings.

### 12. Technical Weaknesses and Gaps
This is one of the technically strongest projects in the set (multi-service RAG pipeline), but chunking strategy and access control are undocumented — both are exactly what a Solutions Architect interviewer would probe on a RAG project.

### 13. Recommended Improvements
Document chunking; add a small quantitative eval set; document IAM/OpenSearch access policy. This is a strong candidate for the **flagship / most-highlighted repo** in the portfolio (see Master Strategy).

---
