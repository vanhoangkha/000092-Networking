---
title : "Preparation"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

#### Preparation

{{% notice warning %}}
 This lab was conducted in Region **US East (N. Virginia) us-east-1**
{{% /notice %}}


{{% notice info %}}
In particular, do not use **Event Engine** because **AWS Marketplace** is not supported to perform the lab. You need to prepare 1 AWS account.
{{% /notice %}}


In addition, the current limit of VPC is 5 VPCs on 1 AWS Region on 1 AWS Account, so we need to delete **AWS VPC Default** to perform the lab.

In other cases, you can create [case support](https://console.aws.amazon.com/support/cases#/create) to increase the resource limit.

#### Overview

#### Considerations

When building a multi-VPC and/or multi-account architecture, there are several services that we need to consider to provide seamless integration between our AWS environment and the existing infrastrucuture in our datacenter. We need to provide robust connectivity and routing between the datacenter and all the VPCs but we also need to provide and control routing between those VPCs. For example, we may have a 'Shared Services' VPC that every other VPC needs access to in which we place common resources that everyone needs, such as a NAT Gateway service to access the Internet. At the same time, we don't want just any VPC talking to any other VPC. In particular, we don't want our 'Non-Production' VPCs talking to our 'Production' VPCs.

#### Connectivity

In the past, customers used third-party solutions and/or transit VPCs that they built and managed on their own. In order to remove much of that undifferentiated heavy lifting, we will use the AWS Transit Gateway Service to provide this connectivity and routing. AWS Transit Gateway is a service that enables customers to connect their Amazon Virtual Private Clouds (VPCs) and their on-premise networks to a highly-available gateway. AWS Transit Gateway provides easier connectivity, better visibility, more control and on-demand bandwidth.

#### DNS Resolution

After we have established connectivity and routing, we need to provide seamless DNS resolution between our Datacenter and the VPCs. Our on-prem devices will want to reach our resources in the cloud using DNS names, not IP addresses, and the resources in the cloud will want to do the same for the servers back in our datacenter. To accomplish this we will use Amazon Route53 Resolver. Amazon Route53 Resolver for hybrid clouds allows us to create highly available endpoints in our VPCs to integrate with the Amazon-provided DNS (sometimes referred to as the .2 resolver, since it is always 2 addresses up from the VPC CIDR block, i.e. 172.16.0.2 for VPC CIDR 172.16.0.0/24).

#### Conclusion and AWS Services featured

During the upcoming labs, we will leverage the following AWS Services to deliver a robust, secure and efficient multi-VPC architecture:

- **Amazon Virtual Private Cloud (VPC)** - logically isolated section of the AWS Cloud
- **AWS Transit Gateway** - connectivity and routing between VPCs and Datacenter
- **AWS Site-to-Site VPN** - connection from our Datacenter to our VPCs
- **Amazon Route 53 Resolver** - DNS integration between AWS and on-prem (Datacenter)
- **AWS Cloud9** - cloud development environment used to edit files and access the Datacenter VPN Virtual Device
- **AWS Systems Manager**, Session Manager - secure server shell access without SSH keys to manage EC2 instances during the workshop
- **AWS CloudFormation** - a common language to model all the resources needed for your applications across all regions and accounts in JSON or YAML format
- **AWS Privatelink** - a technology that enables you to privately connect your VPC to supported AWS services, services hosted by other AWS accounts (VPC endpoint services), and supported AWS Marketplace partner service
- **AWS Transit Gateway Network Manager** - enables you to centrally manage your networks that are built around transit gateways. You can visualize and monitor your global network across Regions and on-premises locations

#### Main content

1. [VPC Deployment](2.1-vpcdeployment/)
2. [Implement Cisco CSR Agreement](2.2-ciscocsr/)