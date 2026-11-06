# Assignment 3 Submission

<!--
How to use this template:

1. Copy this file to submissions/assignment-3/group-<number>/submission.md
2. Replace every <answer> with your group's answer. Delete the angle brackets too.
3. Write GitHub usernames, not full names or student numbers.
-->

## About us

- Group number: 02
- Section: IV-DCSAD
- Lab 3 client: A barangay health records system

## Three estimates

Asia Pacific (Singapore), MySQL, OnDemand, 100% utilization, RDS Proxy No, Database Insights No.

| Option | Instance | Deployment | Nodes | Storage | Total monthly cost (USD) |
| --- | --- | --- | --- | --- | --- |
| A. Small and cheap | db.t4g.micro | Single-AZ | 1 | 20 GB gp3 | $21.01 |
| B. High availability | db.t4g.micro | Multi-AZ | 1 | 20 GB gp3 | $42.75 |
| C. Read scaling | db.t4g.micro | Single-AZ | 2 | 20 GB gp3 | $42.02 |

Share link of our estimate: [Group 2 Estimates](https://calculator.aws/#/estimate?id=7e70a5e99cf7cba8b691d056d43e4b6eb5300ec9)

## Recommendation

Five sentences. Which option fits our client, and why? Use the client's users, the cost of downtime for that client, and the read load.

For the barangay health records system, we think that option B is the most suitable configuration which uses a Multi-AZ deployment. The system may be used by healthcare personnel who need to access patient records and other important information as part of their daily work. If the database becomes unavailable, it could interrupt their work and make it difficult for them to access the records they need. While Option C allows the system to have an additional database that can help handle requests for information, we do not think that this is the main priority for our system. Therefore, we believe that the additional cost of Option B is worth it because it helps keep the database available even if the primary database encounters a problem.

## Question

Why is a Multi-AZ standby not the same as a read replica?

A Multi-AZ standby is mainly used to keep the database available if the primary database encounters a problem, while a read replica is used to help handle additional requests for information. The standby database takes over when the primary database fails, while the read replica helps reduce the workload of the primary database. In simple terms, Multi-AZ focuses on keeping the database running, while a read replica focuses on handling more reading requests.

## Contribution

| GitHub username | What this groupmate did |
| --- | --- |
| Zanis3 | Provided the recommendation answer after discussing it with the group members and answered the question differentiating Multi-AZ standby and read replica. |
| johnlenardtaligatos16 | Did the calculations for all three estimates in the AWS Pricing Calculator |
| mmanzanilloa12241800-sudo | Did the verification of all the provided group input inside submission.md |
