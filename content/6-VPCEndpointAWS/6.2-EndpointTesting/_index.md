---
title : "NP2 Endpoint Testing"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 6.2 </b> "
---

#### Check VPC Endpoint

1. Access **System Manager**

   - Select **Session Manager**
   - Select **Start session**
   - Select **NP2-tgw-Server**
   - Select **Start session**

![VPC Endpoint](/images/Lab-VPC-Endpoint-AWS/1/0005.png?featherlight=false&width=90pc)

2. Execute the following command:

```
dig kms.your_region.amazonaws.com
```

![VPC Endpoint](/images/Lab-VPC-Endpoint-AWS/1/0006.png?featherlight=false&width=90pc)

3. Access to **Route 53**

   - Select **Hosted zones**
   - Select **kms.your_region.amazonaws.com**

![VPC Endpoint](/images/Lab-VPC-Endpoint-AWS/1/0007.png?featherlight=false&width=90pc)

4. View details

![VPC Endpoint](/images/Lab-VPC-Endpoint-AWS/1/0008.png?featherlight=false&width=90pc)