# Assignment 3 Submission

<!--
How to use this template:

1. Copy this file to submissions/assignment-3/group-<number>/submission.md
2. Replace every <answer> with your group's answer. Delete the angle brackets too.
3. Write GitHub usernames, not full names or student numbers.
-->

## About us

- Group number: 7
- Section: IV-DCSAD
- Lab 3 client: A bakery delivery app

## Three estimates

Asia Pacific (Singapore), MySQL, OnDemand, 100% utilization, RDS Proxy No, Database Insights No.

| Option | Instance | Deployment | Nodes | Storage | Total monthly cost (USD) |
| --- | --- | --- | --- | --- | --- |
| A. Small and cheap | db.t4g.micro| Single-AZ | 1 | 20 GB gp3 | $21.01 |
| B. High availability | db.t4g.micro | Multi-AZ | 1 | 20 GB gp3 | $42.75 |
| C. Read scaling | db.t4g.micro | Single-AZ with read replica | 2 (primary + read replica) | 20 GB gp3 | $42.02 |

Share link of our estimate: [(https://calculator.aws/#/estimate?id=97447e08c8424ba3d728c7fff6bb9c10cb4afc24)]

## Recommendation

Lab 3 identifies the client as a bakery delivery app but does not specify the number of users or the volume of read traffic. Because order placement and delivery coordination depend on database availability, downtime could interrupt core operations; this is an inference from the app's purpose. We recommend Option B, Multi-AZ at $42.75 per month, because its standby failover design better supports service availability. Option C costs $42.02 per month and adds a read replica, but the provided Lab 3 information does not establish a read-heavy workload that would require read scaling. Although Option B costs $21.74 more than Option A, the additional cost is reasonable when minimizing order-service interruption is a priority.

## Question

A Multi-AZ standby provides high availability by maintaining a standby database for failover when the primary database becomes unavailable. It is not intended to serve the application's read queries.

A read replica is a separate database instance that can serve read-only queries, helping distribute read traffic and scale read workloads. Unlike a Multi-AZ standby, it is intended to be used for read scaling.
<answer>

## Contribution

| GitHub username | What this groupmate did |
| --- | --- |
| TroyMichaelCamarillo | Reviewed the database deployment options and discussed their suitability for the application. |
| ichannnj | Reviewed the pricing configurations and compared the estimated costs.|
| CPCNarido | Coordinated the group discussion and checked the assignment requirements. |
| Motea47 |Prepared the AWS Pricing Calculator estimates and compiled the submission document. |