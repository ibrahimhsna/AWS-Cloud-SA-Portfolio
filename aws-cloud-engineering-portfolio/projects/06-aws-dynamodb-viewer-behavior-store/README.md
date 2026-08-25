# DynamoDB Viewer Behavior Data Store

> Guided hands-on lab (AWS Skill Builder / SimuLearn) with an independent extension task.

## Overview
Implements an Amazon DynamoDB table (`UserVideoHistory`) to store and query viewer behavior data —
content consumption and device analytics — for a Fire TV-style streaming application.

## Problem
Store semi-structured, high-write-throughput event data (video playback events across many device
types) where each item's schema can vary, which fits DynamoDB's flexible per-item attribute model
better than a fixed relational schema.

## Solution Architecture
The `UserVideoHistory` table uses a composite primary key: `userId` (partition key) and
`lastDateWatched` (sort key). Non-key attributes (`videoId`, `preferredLanguage`,
`supportedDeviceTypes`, `lastStopTime`) are defined per item rather than fixed at the table level.
A device (Fire TV) writes playback records; a developer/application queries the table and adds
attributes as needed.

## AWS Services & Roles
| Service | Role |
|---|---|
| Amazon DynamoDB | Fully managed NoSQL store for viewer behavior/device analytics records |

## Data Model
- Partition key: `userId`
- Sort key: `lastDateWatched`
- Example attributes observed: `videoId`, `preferredLanguage`, `supportedDeviceTypes`, `lastStopTime`

## Workflow
1. A device (Fire TV) plays a video and the client writes a record to the DynamoDB table.
2. A developer queries the table (e.g., by `userId`) and reviews returned attributes.
3. Records can carry different attribute sets per item, since DynamoDB does not enforce a fixed
   non-key schema.

## What I Implemented (Guided)
- Created a NoSQL database as an Amazon DynamoDB table.
- Added records, with dynamic schema, to the DynamoDB table.
- Queried the DynamoDB table.

## What I Implemented (DIY / Unguided)
- Created a new item in the `UserVideoHistory` table with a unique `userId` value and added a
  Number attribute called `rating` to the record — demonstrating the per-item flexible schema.

## Limitations / Not Documented
- Read/write capacity mode (on-demand vs provisioned): **Not documented / Requires clarification**.
- Secondary indexes (GSI/LSI): **Not documented / Requires clarification** — none appear to be used.
- Encryption/backup configuration: **Not documented / Requires clarification**.

## Skills Demonstrated
Amazon DynamoDB table design, composite primary keys, flexible/per-item schema modeling, querying
NoSQL data.

## Future Improvements
- Document capacity mode and estimate cost at scale.
- Add a GSI (e.g., on `videoId`) to support content-centric queries, not just user-centric ones.
