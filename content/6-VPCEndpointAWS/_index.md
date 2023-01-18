---
title : "VPC Endpoints for AWS Services"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### VPC Endpoints for AWS Services

We can use VPC endpoints if we require communication between resources within our VPCs and supported AWS services (Kinesis, Glue, KMS, etc.) without the need of crossing an Internet Gateway, NAT Gateway, VPN connection or AWS Direct Connect. A full list of the services available as VPC endpoints can be found here .

VPC Endpoints are virtual devices. They are horizontally scaled, redundant and highly available VPC components. See the AWS Documentation  for more info.

In a multi-VPC environment, such as this workshop, we have a choice at the time of defining where these VPC Endpoints will reside: in the local VPC that is accessing the AWS Service, or in a common, shared VPC. In some cases, you may decide to have some VPC Endpoints in a central VPC and some in the local VPCs. In this scenario we will add a KMS VPC endpoint within the DCS1 VPC, and the other VPCs will be able to use this central endpoint.

![VPC Deployment](/images/kms-endpoint.png?featherlight=false&width=70pc)