# Cloud Computing Essentials

### 1. Repository Name
`aws-s3-static-website-hosting-policy`

### 2. Project Category
Storage / Static Website Hosting

### 3. Professional Portfolio Description
Improved website reliability by migrating to Amazon S3 static website hosting, reviewing and scoping a bucket policy for public read access, and renaming the hosted object.

### 4. Recommended Repository Structure
```text
aws-s3-static-website-hosting-policy/
├── README.md
├── architecture/
│   └── s3-static-hosting-request-flow.png
└── documentation/
    └── bucket-policy.json
```

### 5. Complete README.md
```markdown
# S3 Static Website Hosting with Reviewed Bucket Policy

> Guided hands-on lab (AWS Skill Builder / SimuLearn) with an independent extension task.

## Overview
Improves website reliability for a city information portal by migrating content to Amazon S3
static website hosting, with a bucket policy explicitly reviewed to secure public read access.

## Problem
The prior hosting setup for the city web portal was less reliable than a managed, highly available
static hosting option; S3 static website hosting removes the need to manage servers for what is
purely static content.

## Architecture
City residents access the portal via its S3 static website endpoint
(`https://<bucketname>.s3-website-<region>.amazonaws.com`). The bucket serves a root object (an
HTML page — renamed from `index.html` to `waves.html`), retrieved via a GET request. Access is
governed by a bucket policy that explicitly allows `s3:GetObject`.

## AWS Services & Roles
| Service | Role |
|---|---|
| Amazon S3 (Static Website Hosting) | Serves the HTML portal content directly, no compute server required |
| S3 Bucket Policy | Grants scoped public read (`s3:GetObject`) access to bucket objects |

## Security Considerations
The bucket policy was reviewed before enabling hosting, explicitly granting only `s3:GetObject`
(`"Effect": "Allow"`) — read access to objects — rather than broader S3 permissions such as
`PutObject`/`DeleteObject`/`ListBucket`, which is the correct minimal-permission approach for a
public static site.

## Workflow
1. Review the bucket policy to confirm it secures the bucket appropriately (scoped to `GetObject`).
2. Enable static website hosting on the bucket.
3. City residents visit the portal; the root object is retrieved and rendered.
4. (DIY) Rename `index.html` to `waves.html` and confirm the portal continues to serve correctly.

## What I Implemented (Guided)
- Reviewed a bucket policy to secure a bucket in Amazon S3.
- Enabled static website hosting.

## What I Implemented (DIY / Unguided)
- Renamed `index.html` to `waves.html` and updated the site configuration accordingly.

## Limitations / Not Documented
- Whether a CDN (CloudFront) sits in front of the S3 static site: **Not documented / Requires
  clarification** — the diagram shows direct S3 endpoint access, no CloudFront layer.
- HTTPS support: S3 website endpoints do not natively support HTTPS without CloudFront — this is a
  real limitation worth stating rather than glossing over.
- Custom domain / Route 53 alias configuration: **Not documented / Requires clarification**.

## Skills Demonstrated
Amazon S3 static website hosting configuration, S3 bucket policy review and least-privilege
scoping, basic static site content management.

## Future Improvements
- Add Amazon CloudFront in front of the S3 origin to get HTTPS support and edge caching — directly
  reusing the CloudFront pattern already demonstrated in Project 3.
- Configure a custom domain via Route 53.
```

### 6–9. Details
Diagram filename: `s3-static-hosting-request-flow.png`; Title: "S3 Static Website Hosting Request Flow with Bucket Policy"; GitHub caption: "S3 static website hosting with a reviewed, least-privilege bucket policy." LinkedIn caption: "Migrated a city information portal to S3 static website hosting with a reviewed, least-privilege bucket policy."

### 10. LinkedIn Portfolio Description
Migrated a web portal to Amazon S3 static website hosting, reviewing and confirming a least-privilege bucket policy scoped to read-only access, then independently renamed the hosted root object and verified continued availability. Skills: Amazon S3, static website hosting, bucket policies, least-privilege access. *(AWS Skill Builder hands-on lab.)*

### 11. Skills Demonstrated
S3 static hosting, bucket policy review, least-privilege scoping.

### 12. Technical Weaknesses and Gaps
No HTTPS story (S3 website endpoints are HTTP-only without CloudFront) — for a "reliability" project this is worth explicitly flagging rather than omitting, since a reviewer who knows S3 will notice immediately.

### 13. Recommended Improvements
Add CloudFront for HTTPS/caching (ties directly to Project 3's pattern); add a custom domain.

---
