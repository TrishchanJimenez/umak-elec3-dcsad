# Assignment 4 Submission

## About us

- Group number: dcsad-g05
- Section: DCSAD

## Estimate 1: the Lab 4 endpoint

Asia Pacific (Singapore), 1 million requests a month: 800,000 GET and 200,000 POST.

| Service | Settings | Monthly cost (USD) |
| --- | --- | --- |
| Amazon API Gateway | HTTP API, 1 million requests, 1 KB each | 1.25 |
| AWS Lambda | Without Free Tier, x86, 1,000,000 requests, 100 ms, 128 MB | 0.41 |
| Amazon DynamoDB | On-demand, Standard, 1 GB, 1 KB items, 0.2 million writes, 0.8 million eventually consistent reads | 0.48 |
| **Total** | | **2.14** |

## Estimate 2: the Lab 2 setup

| Service | Settings | Monthly cost (USD) |
| --- | --- | --- |
| Amazon EC2 | 1 `t3.micro`, Linux, On-Demand, 100% utilization, 8 GB gp3, detailed monitoring on | 12.51 |

Share link of our estimate: https://calculator.aws/#/estimate?id=4d29126d62b7d586f655a039835b1bdad9f7798a

## Question

In a month with no requests at all, which costs remain in each setup, and why?

With no requests, the serverless setup still pays for stored data: DynamoDB on-demand charges for the 1 GB table (about $0.29 a month), while API Gateway and Lambda charge nothing because they bill only per request and per execution. The EC2 setup keeps paying for the running t3.micro instance, its 8 GB gp3 EBS volume, and detailed monitoring all month, about $12.51, because EC2 and EBS bill by the hour and by provisioned storage regardless of traffic.

## Recommendation

Five sentences. Which setup fits the Lab 4 message API at 1 million requests a month, and why? Use our two totals, our answer to the question, and the work that each setup needs from our group.

At 1 million requests a month, the Lab 4 serverless endpoint costs about $2.14, while the Lab 2 EC2 setup costs about $12.51, so the serverless setup is roughly $10.37 cheaper every month. With no requests, API Gateway and Lambda cost nothing and DynamoDB keeps only its small storage charge, but the EC2 instance, its EBS volume, and detailed monitoring keep billing all month. The serverless setup also needs less work from our group because we do not patch or administer a server, and AWS scales Lambda and API Gateway automatically during sudden spikes. The EC2 setup, by contrast, requires us to maintain the operating system and to add or remove instances ourselves when traffic changes. We recommend the serverless setup for the Lab 4 message API at 1 million requests a month because it is cheaper at this traffic level, costs almost nothing when idle, and removes most of the operational work.

## Contribution

| GitHub username | What this groupmate did |
| --- | --- |
| TrishchanJimenez | Configured the API Gateway and Lambda entries in the estimate |
| JoeyRVisayaJr | Configured the EC2, EBS, and detailed monitoring settings |
| scaoile | Checked every field against the activity and completed submission.md |
| jjcabalo | Configured the DynamoDB entries and verified the share link |
