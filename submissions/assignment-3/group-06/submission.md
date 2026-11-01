# Assignment 3 Submission

## About us

- Group number: Group 06
- Section: IV-DCSAD
- Lab 3 client: Fil International Recruitment Agency (FIRA)

## Three estimates

Asia Pacific (Singapore), MySQL, OnDemand, 100% utilization, RDS Proxy No, Database Insights No.

| Option | Instance | Deployment | Nodes | Storage | Total monthly cost (USD) |
| --- | --- | --- | --- | --- | --- |
| A. Small and cheap | db.t4g.micro | Single-AZ | 1 | 20 GB, gp3 | $21.01 |
| B. High availability | db.t4g.micro | Multi-AZ | 1 | 20 GB, gp3 | $42.75 |
| C. Read scaling | db.t4g.micro | Single-AZ | 2 | 20 GB, gp3 | $42.02 |

Share link of our estimate: https://calculator.aws/#/estimate?id=07a20838a87c8ff3063bb4f55e51a3b211199302

## Recommendation

Fil International Recruitment Agency (FIRA) manages overseas job applications where candidates constantly search for job openings while recruitment staff regularly process applicant profiles. Option C (Read Scaling) is the most fitting architecture because candidate job browsing generates a significantly higher volume of read queries compared to write operations. By deploying a dedicated read replica alongside the primary DB instance, FIRA can effectively offload read traffic from candidate searches without degrading the performance of core administrative recruitment workflows. Although Option B provides high availability, FIRA's current primary operational bottleneck is database read latency during peak job application periods rather than strict zero-downtime failover requirements. Therefore, investing in Read Scaling delivers the best balance of query performance, user experience, and cost efficiency for FIRA's operational workload.

## Question

Why is a Multi-AZ standby not the same as a read replica?

A Multi-AZ standby instance is a synchronous failover replica strictly used for high availability and disaster recovery; it cannot accept read or write traffic from applications during normal operations. In contrast, a read replica is an asynchronous copy of the primary database designed specifically to handle offloaded read queries from applications to scale read performance.

## Contribution

| GitHub username | What this groupmate did |
| --- | --- |
| astennue | Performed pricing calculator estimates, client workload recommendation analysis, repository setup, and PR submission |
| micasanf | Pricing Calculator estimate verification and cost table checking |
| JayveeOnUni | Technical review of the Multi-AZ vs Read Replica analysis |
| morense-umak | File structure validation and submission documentation check |