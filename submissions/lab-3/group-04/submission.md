# Lab 3 Submission

<!--
How to use this template:

1. Copy this file to submissions/lab-3/group-<number>/submission.md
2. Replace every <answer> with your group's answer. Delete the angle brackets too.
3. Add rows to the Task 1 table if your VPC divides into 8 subnets.
4. Do not write full names or student numbers in this file.
-->

## About us

- Group number: 4
- Section: IV-DCSAD
- Client: A sari-sari store point-of-sale chain
- VPC CIDR: `10.170.224.0/20`

## Task 1. Equal subnets

New prefix: `/23`

| # | CIDR | First | Last | Usable | First usable | Last usable |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | `10.170.224.0/23` | 10.170.224.0 | 10.170.225.255 | 507 | 10.170.224.4 | 10.170.225.254 |
| 2 | `10.170.226.0/23` | 10.170.226.0 | 10.170.227.255 | 507 | 10.170.226.4 | 10.170.227.254 |
| 3 | `10.170.228.0/23` | 10.170.228.0 | 10.170.229.255 | 507 | 10.170.228.4 | 10.170.229.254 |
| 4 | `10.170.230.0/23` | 10.170.230.0 | 10.170.231.255 | 507 | 10.170.230.4 | 10.170.231.254 |
| 5 | `10.170.232.0/23` | 10.170.232.0 | 10.170.233.255 | 507 | 10.170.232.4 | 10.170.233.254 |
| 6 | `10.170.234.0/23` | 10.170.234.0 | 10.170.235.255 | 507 | 10.170.234.4 | 10.170.235.254 |
| 7 | `10.170.236.0/23` | 10.170.236.0 | 10.170.237.255 | 507 | 10.170.236.4 | 10.170.237.254 |
| 8 | `10.170.238.0/23` | 10.170.238.0 | 10.170.239.255 | 507 | 10.170.238.4 | 10.170.239.254 |

Reserved addresses of subnet 1: `10.170.224.0`, `10.170.224.1`, `10.170.224.2`, `10.170.224.3`, and `10.170.225.255`.

Solution for subnet 1:

```
VPC /20        = 2 ^ (32 - 20) = 4,096 addresses
8 subnets      = 3 extra bits, so new prefix = /20 + 3 = /23
/23 total      = 2 ^ (32 - 23) = 512 addresses
usable         = 512 - 5 = 507
512 / 256      = 2 values of the 3rd octet per subnet
first          = 10.170.224.0
last           = 10.170.224.0 + 511 = 10.170.225.255
first usable   = first + 4 = 10.170.224.4
last usable    = last - 1  = 10.170.225.254
```

## Task 2. Subnets of a given size

- 2a. `2 ^ (24 - 20) = 2 ^ 4 = 16` subnets.
- 2b. `256 - 5 = 251` usable addresses each.
- 2c. CIDR Block 14: `10.170.237.0/24`. Usable range: `10.170.237.4` to `10.170.237.254`

Solution for 2c:

```
/24 = 256 addresses = 1 step of the 3rd octet
10.170.(224 + (1 x 14) - 1).0 = 10.170.237.0/24
last         = 10.170.237.255
usable range = 10.170.237.4 to 10.170.237.254
```

- 2d. Last CIDR Block: `10.170.239.0/24`
  - First: `10.170.239.0`
  - Last: `10.170.239.255`
  - First usable: `10.170.239.4`
  - Last usable: `10.170.239.254`

Solution for 2d:

```
10.170.(224 + (1 x 16) - 1).0 = 10.170.239.0/24
```

## Task 3. Subnets from host counts

| Subnet | Prefix | CIDR | Availability Zone | Usable |
| --- | --- | --- | --- | --- |
| private-a | `/24` | `10.170.224.0/24` | ap-southeast-1a | 251 |
| private-b | `/24` | `10.170.225.0/24` | ap-southeast-1b | 251 |
| public-a | `/26` | `10.170.226.0/26` | ap-southeast-1a | 59 |
| public-b | `/26` | `10.170.226.64/26` | ap-southeast-1b | 59 |

## Task 4. Proposed subnets

| # | Proposal | Valid or not valid | Why |
| --- | --- | --- | --- |
| P1 | `10.170.231.27/26` | Not valid | It does not start on a step. The `/26` that holds `.27` is `10.170.231.0/26`. |
| P2 | `10.170.235.192/26` | Valid | Inside the VPC, on a step, and it overlaps none of the private and public subnets. |
| P3 | `10.170.240.0/22` | Not valid | It is outside the VPC, which ends at `10.170.239.255`. |
| P4 | `10.170.225.128/25` | Not valid | It overlaps `private-b`, `10.170.225.0/24`. |

Checklist:

**P1: `10.170.231.27/26`**

- [x] Inside the VPC
- [ ] Starts on a step: `.27` is not `.0`, `.64`, `.128`, or `.192`
- [x] Size from `/16` to `/28`
- [x] No overlap with Private and Public subnets

**P2: `10.170.235.192/26`** (`10.170.235.192` to `10.170.235.255`)

- [x] Inside the VPC
- [x] Starts on a step: `.192`
- [x] Size from `/16` to `/28`
- [x] No overlap with Private and Public subnets

**P3: `10.170.240.0/22`** (`10.170.240.0` to `10.170.243.255`)

- [ ] Inside the VPC: the VPC ends at `10.170.239.255`
- [x] Starts on a step: 240 is a multiple of 4
- [x] Size from `/16` to `/28`
- [x] No overlap with Private and Public subnets

**P4: `10.170.225.128/25`** (`10.170.225.128` to `10.170.225.255`)

- [x] Inside the VPC
- [x] Starts on a step: `.128`
- [x] Size from `/16` to `/28`
- [ ] No overlap with Private and Public subnets: it is inside `private-b`, `10.170.225.0/24`
