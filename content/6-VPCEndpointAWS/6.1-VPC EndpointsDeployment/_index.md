---
title : "VPC Endpoints - Deployment"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 6.1 </b> "
---

#### VPC Endpoints - Deployment

In a multi-VPC environment, we have the choice of when to determine where these VPC Endpoints are: In the local VPC accessing the AWS service, or in a shared, common VPC. In some cases, you can provide several VPC Endpoints in the central VPC and several VPC Endpoints locally. In this lab, we will add KMS VPC Endpoint in DCS1 VPC and other VPCs will be able to use this central Endpoint.

1. Access to **AWS System Manager**

    - Select **Session Manager**
    - Select **Start Session**
    - Select **NP2 Instance**
    - Select **Start session**

![VPC Endpoint](/images/Lab-VPC-Endpoint-AWS/1/0001.png?featherlight=false&width=90pc)

2. In the **Session** interface

Use the following command:

```
dig kms.your_region.amazonaws.com
```

![VPC Endpoint](/images/Lab-VPC-Endpoint-AWS/1/0002.png?featherlight=false&width=90pc)

As you might have guessed, before the VPC Endpoint is authorized, communication towards the KMS service from the NP2 instance will travel through the DCS1 NAT Gateway (which will also leverage the nternet Gateway inside the VPC). This is a direct result of KMS resolving public ip addresses. Here's what the traffic stream looks like:

![VPC Deployment](/images/kms-noendpoint.png?featherlight=false&width=70pc)

But for now we want to forget about public connection management and use this central KMS VPC Endpoint whenever possible. To do that, we will provide:

- KMS VPC Endpoint in DCS1 VPC
- Route 53 Private Hosted Zone is associated with NP2 VPC so that all DNS queries for KMS service are routed to VPC Endpoint in DCS1 VPC.

![VPC Deployment](/images/kms-endpoint.png?featherlight=false&width=70pc)


#### VPC Endpoints - Deployment

1. Access the creation interface [CloudFormation stack](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?stackName=tgw-kms&templateURL=https://ee-assets-prod-us-east-1.s3.amazonaws.com/modules/c1bed8fa7fe74c40bcf1d5397530fdcb/v1/IntermediateLab.5.tgw-endpoints.yaml&param_ParentStack=tgw)

   - Select all defaults
   - Select **Create stack**

![VPC Endpoint](/images/Lab-VPC-Endpoint-AWS/1/0003.png?featherlight=false&width=90pc)

2. Wait 20 minutes, and finish creating stack.

![VPC Endpoint](/images/Lab-VPC-Endpoint-AWS/1/0004.png?featherlight=false&width=90pc)