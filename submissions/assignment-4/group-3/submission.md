# Assignment 4 Submission

## About us

- Group number: 3
- Section: DCSAD

## Estimate 1: the Lab 4 endpoint

Asia Pacific (Singapore), 1 million requests a month: 800,000 GET and 200,000 POST.

| Service | Settings | Monthly cost (USD) |
| --- | --- | --- |
| Amazon API Gateway | HTTP API, 1 million requests, 1 KB each | $1.25 |
| AWS Lambda | Without Free Tier, x86, 1,000,000 requests, 100 ms, 128 MB | $0.41 |
| Amazon DynamoDB | On-demand, Standard, 1 GB, 1 KB items, 0.2 million writes, 0.8 million eventually consistent reads | $0.48 |
| **Total** | | **$2.14** |

## Estimate 2: the Lab 2 setup

| Service | Settings | Monthly cost (USD) |
| --- | --- | --- |
| Amazon EC2 | 1 `t3.micro`, Linux, On-Demand, 100% utilization, 8 GB gp3, detailed monitoring on | $12.51 |

Share link of our estimate: https://calculator.aws/#/estimate?id=0a334ad5f44754a0a1bdff367879794656e1eee2

## Question

In a month with no requests at all, which costs remain in each setup, and why?

In the Serverless setup (Estimate 1), the compute and request costs for API Gateway, Lambda, and DynamoDB drop to exactly $0, leaving only the tiny cost for the 1 GB of persistent DynamoDB storage. In the Traditional setup (Estimate 2), 100% of the costs remain; you still pay for the EC2 instance running 730 hours a month, the provisioned EBS storage, and the detailed monitoring, because traditional servers charge continuously regardless of whether they are processing traffic or sitting completely idle.

## Recommendation

Five sentences. Which setup fits the Lab 4 message API at 1 million requests a month, and why? Use our two totals, our answer to the question, and the work that each setup needs from our group.

We recommend the Serverless API setup (Estimate 1) for the Lab 4 message API because it is significantly more cost-effective than the EC2 setup (Estimate 2). As noted in our cost breakdown, the serverless architecture scales down perfectly, meaning we are not wasting budget on idle compute time during periods of low or zero traffic. Furthermore, the serverless route drastically reduces the operational work required from our group. If we used EC2, our group would be responsible for manually patching the Linux operating system, managing the web server software, and configuring complex auto-scaling. With API Gateway, Lambda, and DynamoDB, AWS handles all infrastructure maintenance and traffic scaling automatically out of the box.

## Contribution

| GitHub username | What this groupmate did |
| --- | --- |
| @Vinjin2705 | Configured the AWS Pricing Calculator for all services, generated the share link, wrote the recommendation/answers, and submitted the PR. |
| @abulotano | Reviewed the serverless architecture cost breakdown and verified the API Gateway, Lambda, and DynamoDB numbers against the assignment requirements. |
| @plngpc | Proofread the `submission.md` file and cross-checked the EC2 instance pricing logic and public share link before PR creation. |