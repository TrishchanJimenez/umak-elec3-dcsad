# Assignment 4 Submission

## About us

- Group number: 4
- Section: IV-DCSAD

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

Share link of our estimate: https://calculator.aws/#/estimate?id=4dda17f424e8e6e74ee982a517d66bbbc44012fe

## Question

In a month with no requests at all, which costs remain in each setup, and why?

In a month with no requests, the Lab 4 serverless setup costs almost nothing. API Gateway and Lambda bill only per request and per execution time, so with zero traffic they would drop to 0.00 USD. The only cost that remains is DynamoDB storage for the 1 GB of data, which is billed per GB-month whether or not anyone reads or writes it.

In the Lab 2 setup, the full 12.51 USD remains. The t3.micro instance is billed for every hour it runs, and the Auto Scaling group keeps at least one instance running all month. The 8 GB gp3 is billed for provisioned storage, and detailed monitoring is billed per metric while the instance runs. The reason for the difference is that the serverless services charge for work actually done, while EC2 charges for capacity you keep running, so an idle server costs the same as a busy one.

## Recommendation

Five sentences. Which setup fits the Lab 4 message API at 1 million requests a month, and why? Use our two totals, our answer to the question, and the work that each setup needs from our group.

The serverless setup in Lab 4 costs about 2.14 USD a month at one million requests, while the EC2 setup in Lab 2 costs about 12.51 USD a month, so the serverless setup is roughly six times cheaper for this traffic. The difference is even larger when traffic is low; with no requests, Amazon API Gateway and AWS Lambda drop to zero and only a small DynamoDB storage charge remains, but the EC2 instance, its 8 GB gp3 volume, and detailed monitoring still cost about 12.51 USD because they run or are allocated all month. The serverless setup also needs less work from our group because AWS manages the servers, so we do not need to patch an operating system, and API Gateway and Lambda scale automatically during a sudden spike in traffic. The EC2 setup would need us to patch and maintain the instance and to configure Auto Scaling to handle spikes, which is more operational work for the same message API. Therefore, for the Lab 4 message API at 1 million requests a month, we recommend the serverless setup because it is cheaper, costs almost nothing when idle, and requires less server maintenance.

## Contribution

| GitHub username | What this groupmate did |
| --- | --- |
| vivrelavie | Answered the question |
| JoaquinLuisGuevarra96 | Wrote the recommendation |
| CharlesTogle | Made the calculations in the AWS Pricing Calculator |
| AJPSJ | Verified the share link and double-checked the configuration in it |
