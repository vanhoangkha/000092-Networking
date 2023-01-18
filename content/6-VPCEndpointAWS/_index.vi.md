---
title : "VPC Endpoints cho AWS Services"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### VPC Endpoints for AWS Services

Chúng ta có thể sử dụng VPC Endpoint  nếu chúng ta yêu cầu giao tiếp giữa các dịch vụ bên trong các VPC và các dịch vụ AWS được hỗ trợ như Kinesis, Glue, KMS,..) mà không cần phải thông qua Internet Gateway, Nat Gateway, VPN Connection hoặc AWS Direct Connect.

![VPC Deployment](/images/kms-endpoint.png?featherlight=false&width=70pc)