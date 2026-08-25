# AI-Generated Web Content Deployed to Amazon EC2 via Amazon Bedrock

> Guided hands-on lab (AWS Skill Builder / SimuLearn) with an independent extension task.

## Overview
This project combines generative AI content creation (Amazon Bedrock) with a conventional
EC2-hosted web application. Bedrock is used to generate static HTML content, which is then deployed
to a running EC2 instance and verified over the instance's public DNS.

## Problem
Demonstrate an integration pattern where generative AI produces deployable web assets that are
pushed into existing hosting infrastructure, without provisioning new infrastructure per request.

## Architecture
A user prompts Amazon Bedrock (chat/playground) to generate static content. The generated
`index.html` (and later `tictactoe.html`) is applied to a web application running on an Amazon EC2
instance. Instance access/updates are performed via AWS Systems Manager Session Manager
(no inbound SSH required).

## AWS Services & Roles
| Service | Role |
|---|---|
| Amazon Bedrock | Generates static HTML content from a natural-language prompt |
| Amazon EC2 | Hosts the web application serving the generated content |
| AWS Systems Manager Session Manager | Provides secure, keyless shell access to the EC2 instance to update files |

## Workflow
1. Prompt Amazon Bedrock's chat/playground to generate an `index.html` file.
2. Connect to the EC2 instance via Session Manager (no SSH key/port 22 exposure).
3. Update the deployed application with the generated `index.html`.
4. Verify the update using the EC2 instance's public DNS address.
5. (DIY) Prompt Bedrock to generate a tic-tac-toe game as `tictactoe.html`, deploy it the same way.

## Security Considerations
- Using Systems Manager Session Manager instead of SSH avoids opening inbound port 22 and avoids
  key-pair management — a meaningful, real security choice in this lab.

## What I Implemented (Guided)
- Used a prompt to generate an `index.html` file in the Amazon Bedrock chat/playground.
- Updated a deployed application on an Amazon EC2 instance.
- Tested the updated application using the DNS address of the EC2 instance.

## What I Implemented (DIY / Unguided)
- Used Amazon Bedrock to generate a tic-tac-toe game in an `.html` file and deployed
  `tictactoe.html` to the EC2 instance via Session Manager.

## Limitations / Not Documented
- Foundation model used to generate the HTML: **Not documented / Requires clarification**.
- Web server software on the EC2 instance (Apache/Nginx/other): **Not documented / Requires clarification**.
- No input validation/review process for AI-generated code before deployment is documented — worth
  calling out as a real-world risk (AI-generated code should be reviewed before being served publicly).

## Skills Demonstrated
Amazon Bedrock prompting, AI-assisted content generation, EC2 web hosting, AWS Systems Manager
Session Manager for secure instance access.

## Future Improvements
- Add a basic code-review/lint step before deploying AI-generated HTML/JS.
- Commit the actual generated files to the repo for full reproducibility.
