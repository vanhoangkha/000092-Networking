---
title : "Giới thiệu"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

#### Tổng quan về các dịch vụ Networking trên AWS

![VPC Deployment](/images/hybrid-routes-diagram.png?featherlight=false&width=70pc)

#### Availability Zone ( AZ )

Một Availability Zone ( AZ ) bao gồm một hoặc nhiều trung tâm dữ liệu, các (AZ) được thiết kế để không xảy ra sự cố ảnh hưởng đồng thời 2 AZ một lúc (fault isolation)
Giữa 2 AZ là đường kết nối riêng tốc độ cao.AWS khuyến nghị nên triển khai ứng dụng tối thiểu trên 2 AZ.

#### Region 

Một AWS Region bao gồm tối thiểu 3 Availability Zone. Hiện tại có hơn 25 Region trên toàn cầu. Các Region được kết nối với nhau bởi mạng backbone của AWS.
Mặc định dữ liệu và dịch vụ ở các Region độc lập với nhau. ( Trừ một số dịch vụ ở quy mô Global ).

#### Edge Locations

Là mạng lưới trung tâm dữ liệu AWS được thiết kế để cung cấp dịch vụ với độ trễ thấp nhất có thể. Các dịch vụ AWS hoạt động tại Edge Locations bao gồm
+ CloudFront ( CDN )
+ Web Application Firewall ( WAF )
+ Route 53 (DNS Service)

