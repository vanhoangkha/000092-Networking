---
title : "Kiểm tra VPC Peering"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 8.3 </b> "
---

#### Kiểm tra VPC Peering

1. Truy cập vào **Systems Manager**

- Chọn **Session Manager**
- Chọn **Start session**
- Chọn **NP1 instance**

![VPC Peering](/images/Lab-VPC-Peering/00019.png?featherlight=false&width=90pc)

2. Trong giao diện **Session** chúng ta thực hiện ping đến **NP2 instacne** trong **NP2 Private Subnet**

```
ping 10.17.22.100
```

![VPC Peering](/images/Lab-VPC-Peering/00020.png?featherlight=false&width=90pc)