---
title : "Transit Gateway và Site-to-Site VPNs"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Transit Gateway và Site-to-Site VPNs

#### Transit Gateway

Transit Gateway được dùng để kết nối các VPC và mạng on-premises thông qua một hub trung tâm. Điều này đơn giản hoá mạng và kết thúc các mối quan hệ định tuyến phức
tạp.
+ Transit Gateway Attachment là một công cụ để gán các subnet của từng VPC cần kết nối với nhau vào một TGW đã được khởi tạo. Transit Gateway Attachment hoạt động ở quy
mô Availability Zone (AZ-level).
+ Trong VPC, khi một subnet ở một AZ có Transit Gateway Attachment với một TGW, các subnet khác trong cùng AZ đều có thể kết nối tới TGW đó.

#### VPN Site to Site

VPN Site to Site dùng trong mô hình hybrid để thiết lập kết nối liên tục giữa môi trường trung tâm dữ liệu truyền thống tới môi trường VPC của AWS. Việc thiết lập kết nối sẽ cần 2
đầu endpoint ở phía AWS và phía khách hàng :
+ Virtual Private Gateway : Được quản lý hoàn toàn bởi AWS ( chia 2 endpoints ở 2 đầu AZ ).
+ Customer Gateway : Đầu endpoint phía khách hàng, có thể là thiết bị phần cứng hoặc
software appliance.

![VPC Deployment](/images/hybrid-tgw-diagram.png?featherlight=false&width=70pc)
