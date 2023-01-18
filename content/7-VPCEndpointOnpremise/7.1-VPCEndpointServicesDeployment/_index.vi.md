---
title : "Triển khai VPC Endpoint Services"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 7.1 </b> "
---
#### Triển khai VPC Endpoint Services

1. Đến giao diện tạo **[Stack CloudFormation](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?stackName=tgw-vpce&templateURL=https://ee-assets-prod-us-east-1.s3.amazonaws.com/modules/c1bed8fa7fe74c40bcf1d5397530fdcb/v1/IntermediateLab.6.tgw-privatelink.yaml&param_ParentStack=tgw)**

- Chọn mặc định
- Chọn **Create stack**

![VPC Endpoint](/images/Lab-VPC-Endpoint/1/0001.png?featherlight=false&width=90pc)

2. Hoàn thành tạo stack sau 20 phút.

![VPC Endpoint](/images/Lab-VPC-Endpoint/1/0002.png?featherlight=false&width=90pc)

3. Truy cập vào **AWS System Manager**

- Chọn **Session Manager**
- Chọn **Start Session**
- Chọn **NP2 Instance**
- Chọn **Start Session**

![VPC Endpoint](/images/Lab-VPC-Endpoint/1/0003.png?featherlight=false&width=90pc)

4. Thử lệnh sau:

```
curl web.np2.aws.your_domain_name
```

![VPC Endpoint](/images/Lab-VPC-Endpoint-AWS/1/00011.png?featherlight=false&width=90pc)

5. Tiếp tục với lệnh:

```
dig web.np2.aws.example.com
```

![VPC Endpoint](/images/Lab-VPC-Endpoint/1/0005.png?featherlight=false&width=90pc)



