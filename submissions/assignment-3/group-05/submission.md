# Assignment 3 Submission

## About us

- Group number: 5
- Section: IV-DCSAD
- Lab 3 client: A campus library reservation system

## Three estimates

Asia Pacific (Singapore), MySQL, OnDemand, 100% utilization, RDS Proxy No, Database Insights No.

| Option | Instance | Deployment | Nodes | Storage | Total monthly cost (USD) |
| --- | --- | --- | --- | --- | --- |
| A. Small and cheap | db.t4g.micro | Single-AZ | 1 | 20 GB, General Purpose SSD (gp3) | $21.01 |
| B. High availability | db.t4g.micro | Multi-AZ | 1 | 20 GB, General Purpose SSD (gp3) | $42.75 |
| C. Read scaling | db.t4g.micro | Single-AZ | 2 (primary and one read replica) | 20 GB, General Purpose SSD (gp3) | $42.02 |

Share link of our estimate: https://calculator.aws/#/estimate?id=52ffe5967751f1b858db339001c4c75b8badd5bc

## Recommendation

Five sentences. Which option fits our client, and why? Use the client's users, the cost of downtime for that client, and the read load.

Our client is a campus library reservation system used by students and staff, where browsing available seats and study rooms generates a predominantly read-heavy query workload compared to occasional booking confirmations. Downtime incurs severe operational disruption rather than direct revenue loss, causing lockouts, double-booking conflicts, and library front-desk congestion during peak traffic spikes like term enrollment and final exams. Option B (Multi-AZ) directly eliminates this single point of failure by synchronously replicating data to a standby instance in a second Availability Zone and executing automatic DNS failover during an outage. While Option C scales read throughput, it lacks automated failover, making Option B's high availability the strictly superior choice for just 21.74 USD more per month than the baseline Single-AZ setup. We therefore recommend Option B to guarantee uninterrupted service during critical academic periods, with the flexibility to attach asynchronous read replicas later if query throughput ever demands it.

## Question

Why is a Multi-AZ standby not the same as a read replica?

A Multi-AZ standby is a passive, synchronous replica in a secondary Availability Zone used for high availability and automatic failover, kind of like a backup database that automatically takes over when the primary database fails. We learned that applications use the same DNS endpoint and cannot send queries to the standby during normal operations. In contrast, a read replica is an active, asynchronously updated copy with its own read-only endpoint that handles `SELECT` queries to reduce the primary database's workload. Simply put, Multi-AZ improves availability, while read replicas improve read performance but do not provide automatic failover.

## Contribution

| GitHub username | What this groupmate did |
| --- | --- |
| JoeyRVisayaJr | Built the three estimates in the AWS Pricing Calculator and opened the Pull Request with the filled estimates table |
| TrishchanJimenez | Checked the calculator inputs and the three monthly totals |
| jjcabalo | Wrote the five-sentence recommendation for the client |
| scaoile | Answered the Multi-AZ versus read replica question |
