---
title : "VPC Components Deep Dive"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

#### VPC Components Deep Dive

##### VPC Layout

- **Non-production VPCs:** Chúng ta sẽ tạo một số VPC trong số này để chứa các tài nguyên Test và Development của chúng ta.
- **Production VPCs:**  Đây là dành cho hệ thống sản xuất trực tiếp của chúng ta.
- **Shared Resources:** Dành cho các tài nguyên và dịch vụ có thể truy cập được trên tất cả các VPC.
Ngoài ra, chúng ta cần một VPC để đại diện cho môi trường tại chỗ (môi trường công ty) của chúng ta, một Trung tâm dữ liệu mô phỏng:
- **Datacenter:** Trên thực tế, đây sẽ là Trung tâm dữ liệu hoặc cơ sở cùng vị trí hiện có của chúng ta với tất cả phần cứng có sẵn, nhưng chúng ta sẽ tạo phiên bản của riêng mình trên Cloud!


![VPC Deployment](/images/hybrid-vpcs-diagram.png?featherlight=false&width=60pc)

##### IP Addressing

Khắc phục và gán không gian địa chỉ IP riêng (địa chỉ RFC 1918) là một chủ đề lớn và có thể gây khó khăn nếu bạn có một doanh nghiệp lớn, đặc biệt là xem xét các sự kiện kinh doanh lớn có ảnh hưởng đến mạng, chẳng hạn như sáp nhập công ty. Ngay cả khi bạn có một hệ thống quản lý địa chỉ IP tập trung (IPAM), bạn sẽ thấy không gian địa chỉ không có giấy tờ đang được sử dụng và đôi khi việc tìm kiếm không gian ip có thể sử dụng là rất khó.

- **Non-Production CIDR: 10.16.0.0/13** (10.16.0.0 đến 10.23.255.255). Trong bài lab, chúng ta sẽ phân mảnh  10.16.0.0/13 thành các Non-Production VPCs nhỏ hơn: 10.16.0.0/16 và 10.17.0.0/16. Không gian IP còn lại được giữ nguyên để phát triển trong tương lai.
- **Production CIDR: 10.8.0.0/13** (10.8.0.0 đến 10.15.255.255). Trong bài lab, chúng ta chỉ sử dụng IP 10.8.0.0/16 cho Production VPC. Không gian còn lại được giữ nguyên.
- **Shared Services CIDR: 10.0.0.0/16** (10.0.0.0 đến 10.0.255.255).
- **Datacenter VPC CIDR: 10.4.0.0/16** (10.4.0.0 đến 10.4.255.255).

![VPC Deployment](/images/hybrid-subnets-diagram.png?featherlight=false&width=70pc)

1. Truy cập vào [VPC](https://us-east-1.console.aws.amazon.com/vpc/home?region=us-east-1#vpcs:)

   - Quan sát chúng ta thấy đã tạo ra 5 VPC trong trạng thái **Available**

![VPC Deployment](/images/Lab-1/5/0001.png?featherlight=false&width=90pc)

2. Sau đó, truy cập vào [Subnet](https://us-east-1.console.aws.amazon.com/vpc/home?region=us-east-1#subnets:)

   - Quan sát khoảng 30 subnet gồm **Private** và **Public**

![VPC Deployment](/images/Lab-1/5/0002.png?featherlight=false&width=90pc)

3. Truy cập vào [Route table](https://us-east-1.console.aws.amazon.com/vpc/home?region=us-east-1#RouteTables:)

   - Quan sát có khoảng 20 Route table được gán vào các subnet.

![VPC Deployment](/images/Lab-1/5/0003.png?featherlight=false&width=90pc)

4. Truy cập vào [Security Group](https://us-east-1.console.aws.amazon.com/vpc/home?region=us-east-1#SecurityGroups:) xem các security group đã tạo.

![VPC Deployment](/images/Lab-1/5/0004.png?featherlight=false&width=90pc)

5. Truy cập vào [Network ACLs](https://us-east-1.console.aws.amazon.com/vpc/home?region=us-east-1#acls:)

![VPC Deployment](/images/Lab-1/5/0005.png?featherlight=false&width=90pc)

6. Truy cập [Internet Gateway](https://us-east-1.console.aws.amazon.com/vpc/home?region=us-east-1#igws:)

![VPC Deployment](/images/Lab-1/5/0006.png?featherlight=false&width=90pc)

7. Truy cập [NAT Gateway](https://us-east-1.console.aws.amazon.com/vpc/home?region=us-east-1#NatGateways:)

![VPC Deployment](/images/Lab-1/5/0007.png?featherlight=false&width=90pc)

8. Truy cập vào [Elastic IP addresses](https://us-east-1.console.aws.amazon.com/vpc/home?region=us-east-1#Addresses:)

![VPC Deployment](/images/Lab-1/5/0008.png?featherlight=false&width=90pc)

#### Kết nối Linux EC2 instance

1. Truy cập vào [AWS Management Cosole](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)

   - Tìm **System Manager**
   - Chọn **System Manager**

![VPC Deployment](/images/Lab-1/6/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **System Manager**, chọn **Session Manager**

![VPC Deployment](/images/Lab-1/6/0002.png?featherlight=false&width=90pc)

3. Chọn **Start session**

![VPC Deployment](/images/Lab-1/6/0003.png?featherlight=false&width=90pc)

4. Trong giao diện **Start session**

   - Chọn **NP1-tgw-Server**
   - Chọn **Start session**

![VPC Deployment](/images/Lab-1/6/0004.png?featherlight=false&width=90pc)

5. Trong giao diện **NP1-tgw-Server** session. Sử dụng lệnh sau để kiểm tra 

```
ifconfig
```

![VPC Deployment](/images/Lab-1/6/0005.png?featherlight=false&width=90pc)

6. Sử dụng lệnh **cat**

```
cat /etc/resolv.conf
```

![VPC Deployment](/images/Lab-1/6/0006.png?featherlight=false&width=90pc)



