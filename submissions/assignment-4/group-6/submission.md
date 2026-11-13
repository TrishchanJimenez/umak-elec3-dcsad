# Assignment 4 Submission

<!--
How to use this template:

1. Copy this file to submissions/assignment-4/group-<number>/submission.md
2. Replace every <answer> with your group's answer. Delete the angle brackets too.
3. Write GitHub usernames, not full names or student numbers.
-->

## About us

- Group number: 6
- Section: IV - DCSAD

## Estimate 1: the Lab 4 endpoint

Asia Pacific (Singapore), 1 million requests a month: 800,000 GET and 200,000 POST.

| Service | Settings | Monthly cost (USD) |
| --- | --- | --- |
| Amazon API Gateway | HTTP API, 1 million requests, 1 KB each | 1.25 |
| AWS Lambda | Without Free Tier, x86, 1,000,000 requests, 100 ms, 128 MB | 0.41 |
| Amazon DynamoDB | On-demand, Standard, 1 GB, 1 KB items, 0.2 million writes, 0.8 million eventually consistent reads | 0.48 |
| **Total** | | 2.14 |

## Estimate 2: the Lab 2 setup

| Service | Settings | Monthly cost (USD) |
| --- | --- | --- |
| Amazon EC2 | 1 `t3.micro`, Linux, On-Demand, 100% utilization, 8 GB gp3, detailed monitoring on | 12.51 |

Share link of our estimate: https://calculator.aws/#/estimate?id=a9b04b64c4c1b9cf27f09c1fa4d5ead867b781d7

## Question

In a month with no requests at all, which costs remain in each setup, and why?

At 1 million requests a month, the serverless setup (API Gateway, Lambda, DynamoDB) fits the Lab 4 message API better, because it costs $1.86 a month compared with $12.51 for the EC2 setup. The gap comes from idle time: in a month with no requests the serverless setup costs almost nothing, while EC2 still bills about $12.51 because the instance runs all month whether or not anyone visits. Serverless also takes work off our group, since AWS patches and maintains the servers behind all three services, while on EC2 we must patch the operating system, update packages, and keep the instance healthy. A sudden spike in traffic is handled automatically by Lambda and DynamoDB on-demand, but with EC2 we depend on Auto Scaling, which we must tune ourselves and which takes minutes to launch new instances. EC2 would only make sense at much higher, steady traffic or if we needed a long-running server, but at this volume serverless is clearly cheaper and easier to run.


## Recommendation

Five sentences. Which setup fits the Lab 4 message API at 1 million requests a month, and why? Use our two totals, our answer to the question, and the work that each setup needs from our group.

At 1 million requests a month, the serverless setup (API Gateway, Lambda, DynamoDB) fits the Lab 4 message API better, because it costs $1.86 a month compared with $12.51 for the EC2 setup. The gap comes from idle time: in a month with no requests the serverless setup costs almost nothing, while EC2 still bills about $12.51 because the instance runs all month whether or not anyone visits. Serverless also takes work off our group, since AWS patches and maintains the servers behind all three services, while on EC2 we must patch the operating system, update packages, and keep the instance healthy. A sudden spike in traffic is handled automatically by Lambda and DynamoDB on-demand, but with EC2 we depend on Auto Scaling, which we must tune ourselves and which takes minutes to launch new instances. EC2 would only make sense at much higher, steady traffic or if we needed a long-running server, but at this volume serverless is clearly cheaper and easier to run.

## Contribution

| GitHub username | What this groupmate did |
| --- | --- |
| micasanf | Created the branch and folder, filled in `submission.md`, pushed it, and opened the Pull Request. |
| astennue | Built the Lab 4 estimate in the AWS Pricing Calculator (API Gateway, Lambda, DynamoDB) and recorded the monthly costs. |
| JayveeOnUni | Built the Lab 2 EC2 estimate (t3.micro, 8 GB gp3, detailed monitoring) and created and checked the share link. |
| morense-umak | Wrote the answer to the no-requests question and the five-sentence recommendation. |
