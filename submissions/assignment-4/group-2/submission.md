# Assignment 4 Submission

## About us

- Group number: 02
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

Share link of our estimate: [<answer>](https://calculator.aws/#/estimate?id=cf9bcb87b835f68d029e9cd1ec953483ea9b78f1)

## Question

In a month with no requests at all, which costs remain in each setup, and why?

In the Lab 4 setup, almost nothing remains. API Gateway and Lambda charge per request and per run, so with no requests they cost 0. Only DynamoDB storage for the 1 GB of 
data remains, because stored data is billed even when nobody uses it. In the Lab 2 setup, the full cost of about 12.51 USD remains, because the EC2 instance is billed for 
every hour it runs and the EBS disk is billed whether or not there is traffic.

## Recommendation

For 1 million requests a month, the Lab 4 serverless setup fits better, at 2.14 USD a month compared with 12.51 USD for the Lab 2 EC2 setup. It is cheaper because we pay only for the requests we get, while EC2 charges for every hour even with no visitors. The serverless setup also needs less work from our group, since AWS handles patching, servers, and scaling, and a sudden spike in traffic is absorbed automatically. With EC2, our group has to patch the server and set up Auto Scaling to handle a spike. We therefore recommend the Lab 4 serverless setup.

## Contribution

| GitHub username | What this groupmate did |
| --- | --- |
| mmanzanilloa12241800-sudo | Built the Estimate 1 calculator setup for API Gateway, Lambda, and DynamoDB, created the share link, filled in `submission.md`, and opened the Pull Request |
| Zanis3 | Built the Lab 2 EC2 estimate (t3.micro, gp3, detailed monitoring) and checked its monthly cost |
| johnlenardtaligatos16 | Wrote the answer to the no-requests question and the five-sentence recommendation, and checked the share link |
