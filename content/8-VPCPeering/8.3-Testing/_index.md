---
title : "Final Testing"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 8.3 </b> "
---

#### Check VPC Peering

1. Access **Systems Manager**

    - Select **Session Manager**
    - Select **Start session**
    - Select **NP1 instance**

![VPC Peering](/images/Lab-VPC-Peering/00019.png?featherlight=false&width=90pc)

2. In **Session** interface we ping to **NP2 instacne** in **NP2 Private Subnet**

```
ping 10.17.22.100
```

![VPC Peering](/images/Lab-VPC-Peering/00020.png?featherlight=false&width=90pc)