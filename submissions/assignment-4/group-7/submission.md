# Assignment 4 Submission

<!--
How to use this template:

1. Copy this file to submissions/assignment-4/group-<number>/submission.md
2. Replace every <answer> with your group's answer. Delete the angle brackets too.
3. Write GitHub usernames, not full names or student numbers.
-->

## About us

- Group number: 7
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

Share link of our estimate: https://calculator.aws/#/estimate?id=0793728aa68d197cd2f86cf1a676af0c9ae01132

## Question

In a month with no requests at all, which costs remain in each setup, and why?

In the serverless setup (Estimate 1), only the DynamoDB data storage cost remains ($0.25/month for the 1 GB of stored data), because Amazon API Gateway, AWS Lambda, and DynamoDB read/write request units charge purely on demand per invocation and drop to $0.00 when there is zero traffic. In contrast, in the EC2 setup (Estimate 2), the entire $12.51 monthly cost remains unchanged. This is because Amazon EC2 bills continuously for the 24/7 provisioned virtual machine compute time ($9.64), Amazon EBS charges for the 8 GB allocated gp3 disk volume ($0.77), and CloudWatch detailed monitoring charges per enabled metric ($2.10) every hour regardless of incoming web traffic.

## Recommendation

Five sentences. Which setup fits the Lab 4 message API at 1 million requests a month, and why? Use our two totals, our answer to the question, and the work that each setup needs from our group.

For the Lab 4 message API handling 1 million requests a month, our group strongly recommends the serverless setup over the EC2 architecture. At this traffic volume, the serverless endpoint costs only $2.14 per month across API Gateway, Lambda, and DynamoDB, compared to $12.51 per month for running a single `t3.micro` EC2 instance with EBS and detailed monitoring. Furthermore, in periods with low or zero traffic, the serverless architecture scales down to near zero ($0.25 for storage), whereas the EC2 instance incurs its full running costs every hour regardless of demand. Operationally, the serverless setup completely eliminates the maintenance overhead of managing a Linux operating system, applying security patches, and manually tuning auto-scaling policies. Therefore, serverless provides our group with a substantially cheaper, more resilient solution that automatically accommodates traffic spikes without operational complexity.

## Contribution

| GitHub username | What this groupmate did |
| --- | --- |
| ichannnj | Configured API Gateway and AWS Lambda estimates in the AWS Pricing Calculator |
| CPCNarido | Configured Amazon DynamoDB and Amazon EC2 estimates and verified regional settings |
| TroyMichaelCamarillo | Generated the estimate share link and answered the zero-traffic cost comparison question |
| Motea47 | Wrote the five-sentence architecture recommendation and reviewed submission details |
