---
title : "VPC Deployment"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---
#### VPC Deployment

We need to get our base infrastructure in place. The following CloudFormation template will build out five VPCs. Pick the region you want to and keep that choice during any upcoming lab.

We will be explaining these VPCs in detail shortly.

Click on the CloudFormation Launch link below that corresponds to the AWS Region in which you want to deploy the workshop.

#### Check deleted VPC Default

1. Access the interface [VPC](https://us-east-1.console.aws.amazon.com/vpc/home?region=us-east-1#Home:)

![VPC Deployment](/images/Lab-1/1/0001.png?featherlight=false&width=90pc)

2. In the **VPC** interface

    + Select **Your VPC**
    + Check current VPC number is 0.

![VPC Deployment](/images/Lab-1/1/0002.png?featherlight=false&width=90pc)

#### Create AWS Key Pair

For our simulated Data Center Router, we will need to use a key pair for secure SSH access. When you generate a key pair in AWS, the public key is stored in your account in the region you created it. Instant downloadable private key; in fact, this is the only time the private key will be available, so download and store it securely.

1. Access the interface [Key Pair](https://us-east-1.console.aws.amazon.com/ec2/v2/home?region=us-east-1#KeyPairs:)

   + Select **Create Key pair**

![VPC Deployment](/images/Lab-1/2/0001.png?featherlight=false&width=90pc)

2. In the **Create Key Pair** interface

    - Enter the name of **Key Pair**
    - Select key pair type as **RSA**
    - Select **format** as **.pem**
    - Select **Create Key Pair**

![VPC Deployment](/images/Lab-1/2/0002.png?featherlight=false&width=90pc)

#### VPC Deployment

In this step we will use CloudFormation to deploy the infrastructure, specifically deploying 5 VPCs.

1. Access the creation interface [Stack CloudFormation](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?stackName=tgw&templateURL=https://ee-assets-prod-us-east-1.s3.amazonaws.com/modules/c1bed8fa7fe74c40bcf1d5397530fdcb/v1/IntermediateLab.1.tgw-vpcs.yaml&param_AvailabilityZoneA=us-east-1a&param_AvailabilityZoneB=us-east-1b)

   - In the stack creation interface, we will enter the stack name
   - Then select the parameters. For **VPC Parameters**, Select the AZs.
   - Select **Capabilities**
   - Select **Create stack**

![VPC Deployment](/images/Lab-1/3/0001.png?featherlight=false&width=90pc)

2. Wait about 20 minutes, we will finish creating the stack.

![VPC Deployment](/images/Lab-1/3/0002.png?featherlight=false&width=90pc)

3. Stack details are created including 5 VPCs in 2 AZs and using IP **10.0.0.0/8** and **AWS Cloud9** environment

![VPC Deployment](/images/Lab-1/3/0003.png?featherlight=false&width=90pc)