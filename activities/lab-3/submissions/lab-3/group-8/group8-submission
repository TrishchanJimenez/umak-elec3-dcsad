# Lab 3 Submission

## About us

- Group number: 8
- Section: IV - DCSAD
- Client: Esports tournament platform
- VPC CIDR: `10.175.128.0/17`

## Task 1. Equal subnets

New prefix: /19

| # | CIDR | First | Last | Usable | First usable | Last usable |
|---|---|---|---|---:|---|---|
| 1 | `10.175.128.0/19` | `10.175.128.0` | `10.175.159.255` | 8,187 | `10.175.128.4` | `10.175.159.254` |
| 2 | `10.175.160.0/19` | `10.175.160.0` | `10.175.191.255` | 8,187 | `10.175.160.4` | `10.175.191.254` |
| 3 | `10.175.192.0/19` | `10.175.192.0` | `10.175.223.255` | 8,187 | `10.175.192.4` | `10.175.223.254` |
| 4 | `10.175.224.0/19` | `10.175.224.0` | `10.175.255.255` | 8,187 | `10.175.224.4` | `10.175.255.254` |

Reserved addresses of subnet 1: `10.175.128.0`, `10.175.128.1`, `10.175.128.2`, `10.175.128.3`, and `10.175.159.255`.

Working for subnet 1:

```text
4 equal subnets require 2 extra bits.
New prefix = /17 + 2 = /19

Host bits = 32 - 19 = 13
Total addresses = 2^13 = 8,192
Usable addresses = 8,192 - 5 = 8,187

First address = 10.175.128.0
Last address = 10.175.159.255
First usable = 10.175.128.0 + 4 = 10.175.128.4
Last usable = 10.175.159.255 - 1 = 10.175.159.254

Reserved addresses:
10.175.128.0 — network address
10.175.128.1 — VPC router
10.175.128.2 — DNS server
10.175.128.3 — reserved for future use
10.175.159.255 — last address reserved by AWS
```

## Task 2. Subnets of a given size

- **2a.** \(2^{22-17} = 2^5 = 32\) subnets.
- **2b.** \(2^{32-22} - 5 = 1,024 - 5 = 1,019\) usable addresses per subnet.
- **2c.** CIDR: `10.175.244.0/22`. Usable range: `10.175.244.4` – `10.175.247.254`.

Working for 2c:

```text
A /22 subnet contains 2^(32 - 22) = 1,024 addresses.

Subnet 30 starts at:
VPC start + (30 - 1) × 1,024
= 10.175.128.0 + 29 × 1,024
= 10.175.128.0 + 29,696 addresses

29,696 ÷ 256 = 116 increments in the third octet.
128 + 116 = 244

Subnet 30 CIDR = 10.175.244.0/22
Last address = 10.175.247.255
Usable range = 10.175.244.4 – 10.175.247.254
```

- **2d.** `10.175.252.0/22`

## Task 3. Subnets from host counts

| Subnet | Prefix | CIDR | Availability Zone | Usable |
|---|---|---|---|---:|
| private-a | `/19` | `10.175.128.0/19` | ap-southeast-1a | 8,187 |
| private-b | `/19` | `10.175.160.0/19` | ap-southeast-1b | 8,187 |
| public-a | `/21` | `10.175.192.0/21` | ap-southeast-1a | 2,043 |
| public-b | `/21` | `10.175.200.0/21` | ap-southeast-1b | 2,043 |

Working:

```text
Private subnets need 5,874 usable addresses each.
A /20 has 4,091 usable addresses, which is insufficient.
A /19 has 8,187 usable addresses, so each private subnet uses /19.

Public subnets need 1,764 usable addresses each.
A /22 has 1,019 usable addresses, which is insufficient.
A /21 has 2,043 usable addresses, so each public subnet uses /21.

Placement:
private-a: 10.175.128.0/19
private-b: 10.175.160.0/19
public-a: 10.175.192.0/21
public-b: 10.175.200.0/21
```

## Task 4. Proposed subnets

| # | Proposal | Valid or not valid | Why |
|---|---|---|---|
| P1 | `10.175.234.47/21` | Not valid | The address is not aligned to a `/21` boundary. The aligned block containing it is `10.175.232.0/21`. This block is inside the VPC and does not overlap the Task 3 plan, but the proposed CIDR itself is invalid. |
| P2 | `10.175.248.0/21` | Valid | It is aligned to a `/21` boundary, lies inside the VPC, uses an allowed prefix, and does not overlap the Task 3 plan. |
| P3 | `10.175.176.0/20` | Not valid | It overlaps private-b, which covers `10.175.160.0` through `10.175.191.255`. |
| P4 | `10.175.224.0/30` | Not valid | `/30` is outside the allowed subnet prefix range of `/16` through `/28`, even though its starting address is aligned. |