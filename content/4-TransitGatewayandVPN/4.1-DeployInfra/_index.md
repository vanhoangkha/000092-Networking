---
title : "Datacenter Router and Transit Gateway Deployment"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 4.1 </b> "
---
#### Transit Gateway Key Definitions

Before we dive deeper into the Transit Gateway and our Cisco router, let's spend a minute covering the Transit Gateway key components. Feel free to refer back to these definitions if you need guidance further in the lab. We have also attached the previous diagram for reference. Note that each colored line towards the Transit Gateway represents a different route table (red, blue, green), as we will see in the upcoming content:

   - **Attachment** — You can attach a VPC or VPN connection to an AWS Transit Gateway. You can also associate (same effect as attaching VPC/VPNs) a Direct Connect Gateway for Direct Connect connectivity.

   - **Transit gateway route table** — A Transit Gateway has a default route table and can optionally have additional route tables. A route table includes dynamic and static routes that decide the next hop based on the destination IP address of the packet. The target of these routes could be a VPC, a VPN connection or a Direct Connect Gateway. By default, the VPCs and VPN connections that you attach to a Transit Gateway are associated with the default Transit Gateway route table.

   - **Associations** — Each attachment is associated with exactly one route table. Each route table can be associated with zero-to-many attachments.

   - **Propagations** — A VPC or VPN connection can dynamically propagate routes to a Transit Gateway route table. With a VPC, you must create static routes to send traffic to the Transit Gateway. With a VPN connection, routes are propagated from the Transit Gateway to your on-premises router using Border Gateway Protocol (BGP).


![VPC Deployment](/images/hybrid-tgw-diagram.png?featherlight=false&width=70pc)


#### Datacenter Router and Transit Gateway Deployment

Using a predefined CloudFormation template we will deploy a Cisco Router (Cisco CSR) into the Datacenter VPC simulating our on-premise VPN router. In addition, a Transit Gateway will be deployed with a couple of Transit Gateway route tables.

1. Access the creation interface [Stack CloudFormation](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?stackName=tgw-csr&templateURL=https://ee-assets-prod-us-east-1.s3.amazonaws.com/modules/c1bed8fa7fe74c40bcf1d5397530fdcb/v1/IntermediateLab.2.tgw-csr.yaml&param_AvailabilityZoneA=us-east-1a&param_AvailabilityZoneB=us-east-1b&param_ParentStack=tgw)

   - Perform configuration, enter the stack name.
   - Select **Key Pair** created in the preparation step
   - **RouterChoice**, choose **Cisco**
   - Select **Capabilities**
   - Select **Create stack**

![VPC Deployment](/images/Lab-1/7/0001.png?featherlight=false&width=90pc)

2. Wait about 20 minutes, you have finished deploying the resource

![VPC Deployment](/images/Lab-1/7/0002.png?featherlight=false&width=90pc)

3. In **Output** of Stack CloudFormation we will see **Key-Value** which we will use to SSH into the Data Center.


![VPC Deployment](/images/Lab-1/7/0003.png?featherlight=false&width=90pc)

4. Go to **EC2** to see deployed instances.

![VPC Deployment](/images/Lab-1/7/0004.png?featherlight=false&width=90pc)