---
title : "Transit Gateway và Site-to-Site VPNs"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 4.1 </b> "
---

#### Transit Gateway và Site-to-Site VPNs

Trong bước này, chúng ta sử dụng **CloudFormation template** để triển khai hạ tầng gồm **Cisco Router (Cisco CSR)** và **Transit Gateway**

1. Truy cập vào giao diện tạo [Stack CloudFormation](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?stackName=tgw-csr&templateURL=https://ee-assets-prod-us-east-1.s3.amazonaws.com/modules/c1bed8fa7fe74c40bcf1d5397530fdcb/v1/IntermediateLab.2.tgw-csr.yaml&param_AvailabilityZoneA=us-east-1a&param_AvailabilityZoneB=us-east-1b&param_ParentStack=tgw)

   - Thực hiện cấu hình, nhập tên stack.
   - Chọn **Key Pair** đã tạo ở bước chuẩn bị
   - **RouterChoice**, chọn **Cisco**
   - Chọn **Capabilities**
   - Chọn **Create stack**

![VPC Deployment](/images/Lab-1/7/0001.png?featherlight=false&width=90pc)

2. Đợi khoảng 20 phút sau, bạn đã hoàn thành triển khai tài nguyên

![VPC Deployment](/images/Lab-1/7/0002.png?featherlight=false&width=90pc)

3. Vào trong **Output** của Stack CloudFormation chúng ta sẽ thấy **Key-Value** mà chúng ta sẽ dùng để SSH vào Data Center.


![VPC Deployment](/images/Lab-1/7/0003.png?featherlight=false&width=90pc)

4. Truy cập vào **EC2** để xem các instance được triển khai.

![VPC Deployment](/images/Lab-1/7/0004.png?featherlight=false&width=90pc)