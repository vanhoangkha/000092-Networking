---
title : "Các bước chuẩn bị"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

#### Các bước chuẩn bị

{{% notice warning %}}
 Bài lab này thực hiện ở Region **US East (N. Virginia) us-east-1**
{{% /notice %}}


{{% notice info %}}
Đặc biệt, không sử dụng **Event Engine** vì không hỗ trợ **AWS Marketplace** để thực hiện bài lab. Bạn cần chuẩn bị 1 tài khoản AWS.
{{% /notice %}}


Ngoài ra về giới hạn của VPC hiện tại là 5 VPC trên 1 AWS Region trên 1 AWS Account nên chúng ta cần xóa **AWS VPC Default** để thực hiện bài lab. 

Trường hợp khác, bạn có thể tạo [case support](https://console.aws.amazon.com/support/cases#/create) để tăng giới hạn tài nguyên. 

#### Nội dung chính

1. [Triển khai VPC](2.1-vpcdeployment/)
2. [Thực hiện triển khai Cisco CSR Agreement](2.2-ciscocsr/)
