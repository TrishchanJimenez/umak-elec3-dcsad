# Lab 3 Submission - Group 6

## About us

- Group number: 06
- Section: IV-DCSAD
- Client: A dental clinic booking app
- VPC CIDR: 10.76.0.0/16

## Task 1. Equal subnets

New prefix: /19

| # | CIDR | First | Last | Usable | First usable | Last usable |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | 10.76.0.0/19 | 10.76.0.0 | 10.76.31.255 | 8,187 | 10.76.0.4 | 10.76.31.254 |
| 2 | 10.76.32.0/19 | 10.76.32.0 | 10.76.63.255 | 8,187 | 10.76.32.4 | 10.76.63.254 |
| 3 | 10.76.64.0/19 | 10.76.64.0 | 10.76.95.255 | 8,187 | 10.76.64.4 | 10.76.95.254 |
| 4 | 10.76.96.0/19 | 10.76.96.0 | 10.76.127.255 | 8,187 | 10.76.96.4 | 10.76.127.254 |
| 5 | 10.76.128.0/19 | 10.76.128.0 | 10.76.159.255 | 8,187 | 10.76.128.4 | 10.76.159.254 |
| 6 | 10.76.160.0/19 | 10.76.160.0 | 10.76.191.255 | 8,187 | 10.76.160.4 | 10.76.191.254 |
| 7 | 10.76.192.0/19 | 10.76.192.0 | 10.76.223.255 | 8,187 | 10.76.192.4 | 10.76.223.254 |
| 8 | 10.76.224.0/19 | 10.76.224.0 | 10.76.255.255 | 8,187 | 10.76.224.4 | 10.76.255.254 |

Reserved addresses of subnet 1: 10.76.0.0, 10.76.0.1, 10.76.0.2, 10.76.0.3, and 10.76.31.255

Working for subnet 1:

```
Original VPC prefix /16 = 65,536 total addresses.

To divide into 8 equal subnets (2^3), add 3 extra bits: /16 + 3 = /19.

Total addresses per subnet = 2^(32 - 19) = 8,192.

Usable addresses = 8,192 - 5 = 8,187.   

First address: 10.76.0.0.

Last address: 10.76.0.0 + 8,191 = 10.76.31.255.

Reserved addresses: Network (10.76.0.0), VPC Router (10.76.0.1), DNS Server (10.76.0.2), Future use (10.76.0.3), Broadcast (10.76.31.255).   

First usable address: 10.76.0.0 + 4 = 10.76.0.4.  

Last usable address: 10.76.31.255 - 1 = 10.76.31.254.   
```

## Task 2. Subnets of a given size

- 2a. 64
- 2b. 1,019
- 2c. CIDR: 10.76.20.0/22. Usable range: 10.76.20.4 to 10.76.23.254

Working for 2c:

```
VPC is /16 (65,536 addresses) and subnet size is /22 (1,024 addresses).

Number of subnets = 65,536 / 1,024 = 64 subnets.

Subnet step size in 3rd octet = 4.

Subnet 6 starts at 3rd octet index: (6 - 1) * 4 = 20.

First address: 10.76.20.0, Last address: 10.76.23.255.

Usable range: 10.76.20.4 to 10.76.23.254.
```

- 2d. 10.76.252.0/22

## Task 3. Subnets from host counts

| Subnet | Prefix | CIDR | Availability Zone | Usable |
| --- | --- | --- | --- | --- |
| private-a | /20 | 10.76.0.0/20 | ap-southeast-1a | 4,091 |
| private-b | /20 | 10.76.16.0/20 | ap-southeast-1b | 4,091 |
| public-a | /23 | 10.76.32.0/23 | ap-southeast-1a | 507 |
| public-b | /23 | 10.76.34.0/23 | ap-southeast-1b | 507 |

## Task 4. Proposed subnets

| # | Proposal | Valid or not valid | Why |
| --- | --- | --- | --- |
| P1 | 10.76.35.0/24 | Not valid | It overlaps with the public-b subnet (10.76.34.0/23) defined in the Task 3 plan. |
| P2 | 10.76.252.0/23 | Valid | It is inside the VPC CIDR block, starts on a valid step boundary, is within prefix limits, and does not overlap the Task 3 plan. |
| P3 | 10.77.0.0/18 | Not valid | It falls outside the assigned VPC CIDR block boundary (10.76.0.0/16). |
| P4 | 10.76.102.0/30 | Not valid | The prefix length /30 is smaller than /28, which is the smallest subnet block size allowed by AWS. |
