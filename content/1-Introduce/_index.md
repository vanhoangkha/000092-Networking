---
title : "Introduction"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 1. </b> "
---

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