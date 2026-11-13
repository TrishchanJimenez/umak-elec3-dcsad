# Assignment 3 Submission

<!--
How to use this template:

1. Copy this file to submissions/assignment-3/group-<number>/submission.md
2. Replace every <answer> with your group's answer. Delete the angle brackets too.
3. Write GitHub usernames, not full names or student numbers.
-->

## About us

- Group number: 8
- Section: IV - DCSAD
- Lab 3 client: Esports Tournament Platform

## Three estimates

Asia Pacific (Singapore), MySQL, OnDemand, 100% utilization, RDS Proxy No, Database Insights No.

| Option | Instance | Deployment | Nodes | Storage | Total monthly cost (USD) |
| --- | --- | --- | --- | --- | --- |
| A. Small and cheap | db.t4g.micro | Single-AZ | 1 | 20 GB General Purpose SSD (gp3) | 21.01 USD |
| B. High availability | db.t4g.micro | Multi-AZ | 1 | 20 GB gp3 | 42.75 USD |
| C. Read scaling | db.t4g.micro | Single-AZ | 2, the primary and one read replica | 20 GB gp3 | 42.02 USD |

Share link of our estimate: https://calculator.aws/#/estimate?id=bd6e1ab44b1b13c96eeb2cd722287bb711352ba8

## Recommendation

Option B, High Availability, is the most suitable choice for the Esports Tournament Platform because it helps keep the database accessible during important tournament events. The platform serves players, tournament organizers, and administrators who need reliable access to tournament information, registrations, schedules, and match results. Database downtime during an ongoing tournament could interrupt registrations, delay match updates, and affect the overall experience of participants. Although Multi-AZ is more expensive than Single-AZ, the additional cost is justified by the improved availability and automatic failover. Since the platform is expected to handle frequent read requests for tournament schedules, player information, and match results, a read replica may be considered in the future if its read workload increases.

## Question

A Multi-AZ standby is not the same as a read replica because they serve different purposes. A Multi-AZ standby is designed for high availability and disaster recovery, allowing Amazon RDS to automatically fail over to the standby if the primary database becomes unavailable. It is not intended to handle application read requests. A read replica, on the other hand, is designed to improve read performance by allowing applications to direct read queries to another database instance. Therefore, Multi-AZ improves database availability, while read replicas help distribute read workloads.

## Contribution

| GitHub username | What this groupmate did |
| --- | --- |
| micmiccc16 | Prepared the submission document and handled GitHub submission |
| jdyyy1 | Verified all computing |
| shaeluh | Prepared the recommendation and answered the technical question |
| MarcoLasaga | Created and configured the AWS Pricing Calculator estimates. Compared the three database configurations and costs |