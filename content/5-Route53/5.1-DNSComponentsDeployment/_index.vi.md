---
title : "Triển khai DNS"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 5.1 </b> "
---

#### DNS Components Deployment

Chúng ta sẽ sử dụng **CloudFormation template** để khởi tạo tài nguyên.

1. Truy cập vào giao diện tạo [CloudFormation Stack](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?stackName=tgw-dns&templateURL=https://ee-assets-prod-us-east-1.s3.amazonaws.com/modules/c1bed8fa7fe74c40bcf1d5397530fdcb/v1/IntermediateLab.3.tgw-dns.yaml&param_AvailabilityZoneA=us-east-1a&param_AvailabilityZoneB=us-east-1b&param_ParentStack=tgw)

- Nhập stack name
- Chọn **Zone**: example.com
- Chọn **Capabilities**
- Chọn **Create stack**

![DNS Components Deployment](/images/Lab-2-DNS/1/0001.png?featherlight=false&width=90pc)

2. Đợi 20 phút sau, hoàn thành tạo stack triển khai hạ tầng.

![DNS Components Deployment](/images/Lab-2-DNS/1/0002.png?featherlight=false&width=90pc)

