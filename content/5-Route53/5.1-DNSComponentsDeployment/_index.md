---
title : "DNS Components Deployment"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 5.1 </b> "
---

#### DNS Components Deployment

We will use **CloudFormation template** to initialize the resource.

1. Access the creation interface [CloudFormation Stack](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?stackName=tgw-dns&templateURL=https://ee-assets-prod-us-east-1.s3.amazonaws.com/modules/c1bed8fa7fe74c40bcf1d5397530fdcb/v1/IntermediateLab.3.tgw-dns.yaml&param_AvailabilityZoneA=us-east-1a&param_AvailabilityZoneB=us-east-1b&param_ParentStack=tgw)

   - Enter the stack name
   - Select **Zone**: example.com
   - Select **Capabilities**
   - Select **Create stack**

![DNS Components Deployment](/images/Lab-2-DNS/1/0001.png?featherlight=false&width=90pc)

2. Wait 20 minutes, finish creating the infrastructure deployment stack.

![DNS Components Deployment](/images/Lab-2-DNS/1/0002.png?featherlight=false&width=90pc)