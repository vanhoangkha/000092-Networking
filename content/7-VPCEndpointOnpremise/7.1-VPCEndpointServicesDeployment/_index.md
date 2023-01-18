---
title : "VPC Endpoint Services - Deployment"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 7.1 </b> "
---
#### VPC Endpoint Services - Deployment

1. Go to creation interface **[Stack CloudFormation](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?stackName=tgw-vpce&templateURL=https://ee-assets-prod-us-east-1.s3.amazonaws.com/modules/c1bed8fa7fe74c40bcf1d5397530fdcb/v1/IntermediateLab.6.tgw-privatelink.yaml&param_ParentStack=tgw)**

   - Choose default
   - Select **Create stack**

![VPC Endpoint](/images/Lab-VPC-Endpoint/1/0001.png?featherlight=false&width=90pc)

2. Finish creating stack after 20 minutes.

![VPC Endpoint](/images/Lab-VPC-Endpoint/1/0002.png?featherlight=false&width=90pc)

3. Access **AWS System Manager**

   - Select **Session Manager**
   - Select **Start Session**
   - Select **NP2 Instance**
   - Select **Start Session**

![VPC Endpoint](/images/Lab-VPC-Endpoint/1/0003.png?featherlight=false&width=90pc)

4. Try the following command:

```
curl web.np2.aws.your_domain_name
```

![VPC Endpoint](/images/Lab-VPC-Endpoint-AWS/1/00011.png?featherlight=false&width=90pc)

5. Continue with the command:

```
dig web.np2.aws.example.com
```

![VPC Endpoint](/images/Lab-VPC-Endpoint/1/0005.png?featherlight=false&width=90pc)