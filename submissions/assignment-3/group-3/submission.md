# Assignment 3 Submission

## About our group

- Group number: 3
- Section: DCSAD
- Lab 3 Client: A jeepney fleet tracking service

## Cost Estimate

| Option | Instance | Deployment | Nodes | Storage | Monthly Total (USD) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **A. Small and cheap** | db.t4g.micro | Single-AZ | 1 | 20 GB, General Purpose SSD (gp3) | $21.01 |
| **B. High availability** | db.t4g.micro | Multi-AZ | 1 | 20 GB, General Purpose SSD (gp3) | $42.75 |
| **C. Read scaling** | db.t4g.micro | Single-AZ | 2 | 20 GB, General Purpose SSD (gp3) | $42.02 |

**Estimate Share Link:** https://calculator.aws/#/estimate?id=ddce556db7c5485f7d20122b1d31c616bec0c633

## Recommendation

For a jeepney fleet tracking service, we recommend Option B (High availability with Multi-AZ). Jeepney tracking relies on constant, real-time location updates, meaning any database downtime immediately disrupts dispatch operations and active passenger tracking. The cost of downtime is significant, as it can lead to misrouted fleets, delayed schedules, and a severe loss of user trust in the app. While Option C offers read scaling, fleet tracking is typically a write-heavy workload due to continuous incoming GPS pings from the jeepneys. Therefore, the automatic failover protection of Multi-AZ is far more critical for this client than adding a read replica. 

## Multi-AZ vs. Read Replica

**Why is a Multi-AZ standby not the same as a read replica?**
A Multi-AZ standby is a synchronous, hidden replica meant strictly for automatic failover and high availability, meaning you cannot route read traffic to it. In contrast, a read replica is an asynchronous, accessible copy of the primary database designed specifically to handle read-heavy workloads and scale performance, but it does not automatically fail over if the primary goes down.

## Contribution

| GitHub username | What this groupmate did |
| --- | --- |
| @Vinjin2705 | Handled pricing configuration for Option A, drafted the architecture recommendation, and managed GitHub submission |
| @abulotano | Configured pricing for Option B and generated the AWS Pricing Calculator share link |
| @plngpc | Configured pricing for Option C and authored the technical explanation of Multi-AZ vs. Read Replicas |