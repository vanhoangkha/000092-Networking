---
title : "AWS Networking and Content Delivery"
date : "`r Sys.Date()`"
weight : 1
chapter : false
---
# AWS Networking and Content Delivery

#### Overview of Networking services on AWS

![VPC Deployment](/images/hybrid-routes-diagram.png?featherlight=false&width=70pc)

#### Availability Zone ( AZ )

An Availability Zone (AZ) consists of one or more data centers, the (AZs) are designed so that no failure affects 2 AZs at the same time (fault isolation).
Between the 2 AZs is a dedicated high-speed connection. AWS recommends deploying the application on at least 2 AZs.

#### Region

An AWS Region consists of at least 3 Availability Zones. Currently, there are more than 25 Regions globally. Regions are connected by the AWS backbone network.
By default, data and services in regions are independent of each other. (Except for some services at a global scale).

#### Edge Locations

An AWS data center network designed to deliver service with the lowest possible latency. AWS services that work at Edge Locations include
+ CloudFront (CDN)
+ Web Application Firewall (WAF)
+ Route 53 (DNS Service)

#### Amazon Virtual Private Cloud ( VPC )

Amazon Virtual Private Cloud (Amazon VPC) allows you to launch AWS resources into a virtual network that you have defined. VPC is located in a Region, when creating a VPC, it is necessary to declare a CIDR network class IPv4 (required) and IPv6 (optional). The current VPC limit is 5 VPCs per AWS Region per AWS Account. The main purpose of using VPC is usually to separate environments.(Production/Dev/Test/Staging).

Note: If you want to separate resources (Users can't see a specific resource, need to split into multiple AWS accounts, multiple VPCs can't solve this problem)

#### Amazon Virtual Private Cloud ( VPC ) – Subnet

Amazon VPC allows creating multiple virtual networks and dividing these virtual networks into subnets (subnets). VPC Subnet will be located in a specific Availability Zone. When creating a Subnet, we specify the CIDR for that subnet and this is a subset of the VPC CIDR block.

In each Subnet, AWS will keep 5 IP addresses. For example, if the Subnet has a CIDR of 10.10.1.0/24
+ Network address ( 10.10.1.0 )
+ Broadcast address ( 10.10.1.255 )
+ Address for the router ( 10.10.1.1 )
+ Address for DNS ( 10.10.1.2 )
+ Address for future feature ( 10.10.1.3 )

#### Amazon Virtual Private Cloud ( VPC ) – Route table

Route table (Routing table), a collection of Routes, to determine the route for the network. When creating a VPC, AWS will create a Default Route table, the Default Route table cannot be deleted and contains only 1 Route, which allows all Subnets in the VPC to communicate with each other. The route table will be assigned to the Subnet. We can create a Custom Route table, but we cannot delete the default route. (VPC CIDR – Local)

#### Amazon Virtual Private Cloud ( VPC ) – Elastic Network Interface ( ENI )

Elastic Network Interface (ENI) is a virtual network card we can switch to EC2s
Other Instances.
When migrating to a new server, a virtual network card will remain:

+ Private IP address
+ Elastic IP address
+ MAC address

#### Amazon Virtual Private Cloud ( VPC ) – Elastic IP address ( EIP )

An Elastic IP address (EIP) is a static IPv4 public address that can be associated with an Elastic Network Interface.
When not used, will be charged. (avoid waste)

#### Amazon Virtual Private Cloud ( VPC ) – VPC Endpoint

VPC Endpoint allows us to connect resources located in VPC to supported AWS services (AWS PrivateLink – over AWS private network) without going through an internet connection.

There are two types of VPC Endpoints:

Interface Endpoint: Use an Elastic Network Interface in the VPC with the same address
Private IP to connect to a support service.

Gateway Endpoint: Use a route table to route to the endpoint of the support service
( S3 and Dynamo DB )

#### Amazon Virtual Private Cloud ( VPC ) – Internet Gateway

The Internet Gateway is a component of Amazon VPC that scales out that allows EC2 Instances in the VPC to transmit information over the Internet. Internet Gateway is managed by AWS, we don't need to configure autoscale or high availability.

#### Amazon Virtual Private Cloud ( VPC ) – NAT Gateway

The NAT Gateway allows EC2 instances in the subnet to access the internet or other AWS services. Only accepts outgoing connections and does not accept incoming connections.

#### Amazon Virtual Private Cloud ( VPC ) – Security Group

Security Group (SG) is a stateful virtual firewall that helps control incoming and outgoing traffic to AWS resources.
Security Group rules are restricted by protocol, source address, connection port, or another Security Group.
+ Security Group rule only allows allowing rule.
Security Group is applied to Elastic Network Interfaces.
+ By default Security Group blocks all incoming access and allows all outgoing access.

#### Amazon Virtual Private Cloud ( VPC ) – Network Access Control List ( NACL )

The Network Access Control List (NACL) is a stateless virtual firewall that helps control incoming and outgoing traffic to AWS resources.
+ NACL is limited by protocol, source address, and connection port.
+ Security Group is applied to Amazon VPC Subnets
+ By default NACL allows all incoming and outgoing access.

Rules read from top to bottom. If any rule is satisfied, take that rule.

#### VPC Peering

VPC Peering is a feature that helps to connect two or more VPCs so that the resources inside those two VPCs can communicate directly with each other without having to go through the Internet.
increase security for VPC.
+ VPC Peering is a connection that needs to be created 1:1 between two members VPCs, does not support transitive routing.
+ VPC Peering is not supported when 2 VPCs have overlapping IP address space.

#### Transit Gateway

Transit Gateway is used to connect VPCs and on-premises networks through a central hub. This simplifies the network and ends complex routing relationships
complex.
+ Transit Gateway Attachment is a tool to assign the subnets of each VPC to be connected to an initialized TGW. Transit Gateway Attachment operates at
Availability Zone (AZ-level) model.
In VPC, when a subnet in an AZ has a Transit Gateway Attachment with a TGW, other subnets in the same AZ can connect to that TGW.

#### VPN Site to Site

VPN Site to Site uses a hybrid model to establish a persistent connection between a traditional data center environment and an AWS VPC environment. Establishing a connection will require 2
endpoints on the AWS side and the client side:
+ Virtual Private Gateway: Fully managed by AWS (dividing 2 endpoints at 2 ends of AZ).
+ Customer Gateway: The customer-side endpoint, which can be a hardware device or
software appliance.

#### AWS Direct Connect

AWS Direct Connect is a service that allows creating a private connection from a traditional data center to AWS.
+ Latency about 20ms - 30ms.
+ AWS Direct Connect in Vietnam will now be through AWS Direct Connect partners and operate as Hosted Connections. (If directly to AWS, it is Dedicated Connections )
+ Direct Connect bandwidth can be changed up / down depending on needs.

#### Elastic Load Balancing – Network Load Balancer

Network Load Balancer (NLB) is an AWS-managed load balancing service that operates at Layer 4.
+ Using TCP and TLS protocols.
+ Supports static IP set feature.
+ Supports the highest performance in Load Balancer types capable of handling up to millions of
requests.
+ Allow route traffic to both targets outside of VPC (IP address), EC2, and Container (ECS, EKS).

#### Main content

1. [Introduction](1-introduce/)
2. [Preparation steps](2-prerequiste/)
3. [VPC Components Deep Dive](3-vpcs/)
4. [Transit Gateway and Site-to-Site VPNs](4-transitgatewayandvpn/)
5. [Route53 DNS Endpoints and Internal Hosted Zones](5-route53/)
6. [VPC Endpoints for AWS Services](6-vpcendpointaws/)
7. [VPC Endpoint Services](7-vpcendpointonpremise/)
8. [VPC Peering](8-vpcpeering/)
9. [Transit Gateway Network Manager](9-transitgatewaynetworkmanager/)
10. [Resource Cleanup](10-cleanup/)