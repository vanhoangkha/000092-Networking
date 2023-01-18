---
title : "Route53 DNS Endpoints và Internal Hosted Zones"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

#### Route53 DNS Endpoints và Internal Hosted Zones

Nhiều khách hàng cần môi trường AWS của họ để giao tiếp với các trung tâm dữ liệu tại chổ  (môi trường công ty) của họ. Tại thời gian kiến trúc kết nối DNS này là một trong những người chơi chính trong phòng vò tài nguyên tại chổ sẽ cần phân giải tên DNS cho tài nguyên trong AWS và ngược lại.

Trong bài lab này, chúng ta sẽ hướng đến **On-primes DNS server** với **AWS Route 53** để cả 2 cùng tồn tại. Tiếp đến chúng ta sẽ triển khai các tài nguyên:

- **Route 53 Inbound Endpoints** làm **DNS entry point** đến **AWS**
- **Route 53 Outbound Endpoints** làm **DNS exit point** 
-  4 **Route 53 Private Hosted Zones**, một cho mỗi domain mà chúng ta muốn lưu trữ trên AWS.
- **DNS Bind server** với **Data Center VPC** (mô phỏng DNS Server on-premise)
- Thêm **Route 53 Outbound Endpoint** cho DataCenter VPC.

#### On-premise -> AWS flow diagram

Trong bài lab, chúng ta sẽ triển khai **Route 53 Outbound Endpoint Resolver** được gắn  vào **Data Center VPC** với quy tắc gửi lưu lượng **DNS** nhất định đến **Bind Server** **Bind Server** sau đó được cấu hình để gửi lưu lượng DNS này đến **Route 53 Inbound Endpoint Resolver** trong **DCS VPC**. **Inbound Endpoint** có nhận thức về **Private Hosted Zones** trong **VPC** và sẽ có thể phân giải một số **DNS name** như **np1.example.com** hoặc **p1.example.com**


![VPC Deployment](/images/dns-dc1tonp1.png?featherlight=false&width=60pc)

#### AWS -> On-premise flow diagram

Mặt khác, nếu chúng ta cố gắng giải quyết tên DNS không có sẵn trong **Private Hosted Zones** cho VPC, truy vấn DNS sẽ được chuyển tiếp ra bên ngoài VPC theo các quy tắc có trong **Route 53 Ountbound Endpoint** cho VPC. Các quy tắc trỏ đến **on-premise DNS Bind Server** làm trình phân giải

![VPC Deployment](/images/dns-np1todc.png?featherlight=false&width=60pc)