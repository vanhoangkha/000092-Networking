---
title : "Kiểm tra VPC Endpoint"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 6.2 </b> "
---

#### Kiểm tra VPC Endpoint

1. Truy cập vào **System Manager**

- Chọn **Session Manager**
- Chọn **Start session**
- Chọn **NP2-tgw-Server**
- Chọn **Start session**

![VPC Endpoint](/images/Lab-VPC-Endpoint-AWS/1/0005.png?featherlight=false&width=90pc)

2. Thực hiện lệnh sau:

```
dig kms.your_region.amazonaws.com
```

![VPC Endpoint](/images/Lab-VPC-Endpoint-AWS/1/0006.png?featherlight=false&width=90pc)

3. Truy cập vào **Route 53**

- Chọn **Hosted zones**
- Chọn **kms.your_region.amazonaws.com**

![VPC Endpoint](/images/Lab-VPC-Endpoint-AWS/1/0007.png?featherlight=false&width=90pc)

4. Xem chi tiết

![VPC Endpoint](/images/Lab-VPC-Endpoint-AWS/1/0008.png?featherlight=false&width=90pc)


