---
title : "VPC Peering"
date :  "`r Sys.Date()`" 
weight : 8
chapter : false
pre : " <b> 8. </b> "
---

#### VPC Peering

VPC Peering là tính năng giúp kết nối hai hay nhiều VPC để các tài nguyên bên trong hai VPC đó có thể liên lạc trực tiếp với nhaukhông cần phải thông qua Internet , góp phần gia
tăng tính bảo mật cho VPC.
+ VPC Peering là kết nối cần tạo 1 : 1 giữa hai VPC thành viên , không hỗ trợ transitive routing.
+ VPC Peering không hỗ trợ khi 2 VPC bị overlap IP address space.


![VPC Peering](/images/peer-np1tonp2diagram.png?featherlight=false&width=60pc)