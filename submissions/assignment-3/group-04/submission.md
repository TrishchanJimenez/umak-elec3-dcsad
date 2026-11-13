# Assignment 3 Submission

## About us

- Group number: 04
- Section: IV-DCSAD
- Lab 3 client: A sari-sari store point-of-sale chain

## Three estimates

Asia Pacific (Singapore), MySQL, OnDemand, 100% utilization, RDS Proxy No, Database Insights No.

| Option               | Instance     | Deployment | Nodes | Storage            | Total monthly cost (USD) |
| -------------------- | ------------ | ---------- | ----- | ------------------ | ------------------------ |
| A. Small and cheap   | db.t4g.micro | Single-AZ  | 1     | 20 GB gp3          | 21.01                    |
| B. High availability | db.t4g.micro | Multi-AZ   | 1     | 20 GB gp3          | 42.75                    |
| C. Read scaling      | db.t4g.micro | Single-AZ  | 2     | 20 GB gp3 per node | 42.02                    |

Share link of our estimate: [Three Estimates](https://calculator.aws/#/estimate?id=c51c04d2d1eecb8c2037586a8c1c49cce265c596)

## Recommendation

Five sentences. Which option fits our client, and why? Use the client's users, the cost of downtime for that client, and the read load.

Option B, the Multi-AZ deployment, fits the sari-sari store point-of-sale chain because its cashiers and store managers need the system to keep recording sales during business hours. If the database goes down, stores lose sales, build long queues, and fall back to manual receipts that are hard to reconcile. The extra USD 21.74 a month over Option A is justified if even a short checkout outage costs the chain more than that, which can be plausible for a POS business that depends on continuous checkout. Multi-AZ can provide automatic failover, not read scaling, as it keeps writes available when the primary database or its Availability Zone fails, but it does not serve read traffic while the primary is healthy. The chain’s read load is modest and comes mainly from product lookups and end-of-day reports, so a read replica is not worth the cost yet.

## Question

Why is a Multi-AZ standby not the same as a read replica?

A Multi-AZ is a copy of the database in another Availability Zone that is mainly used for automatic failover, so it cannot serve read queries. A Read Replica is a separate DB instance that receives changes asynchronously from the primary database and can serve read traffic. It's mainly used for read scaling and load balancing, though it may lag behind the primary database and does not provide automatic failover.

## Contribution

| GitHub username       | What this groupmate did                                                                         |
| --------------------- | ----------------------------------------------------------------------------------------------- |
| vivrelavie            | Built and saved the three RDS for MySQL estimates in the AWS Pricing Calculator                 |
| JoaquinLuisGuevarra96 | Provided recommendations for the client and reviewed the estimate share link                    |
| AJPSJ                 | Verified the instance class, deployment, nodes, and storage settings                            |
| CharlesTogle          | Answered the Multi-AZ standby versus read replica question and reviewed the estimate share link |
