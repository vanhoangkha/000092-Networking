---
title : "Transit Gateway Routing"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 4.5 </b> "
---
#### Transit Gateway Routing

![VPC Deployment](/images/hybrid-routes-diagram.png?featherlight=false&width=60pc)

1. Truy cập vào **VPC**, chọn **Route tables**

- Chọn **NP1-_stackname-Private route table**

![VPC Deployment](/images/Lab-1/11-TGWRoute/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **NP1-_stackname-Private route table**

- Chọn **Routes**
- Chọn **Edit routes**

![VPC Deployment](/images/Lab-1/11-TGWRoute/0002.png?featherlight=false&width=90pc)

3. Chọn **Add route**

- Chọn **Destination** là **0.0.0.0/0**
- Chọn **Target** là **TGW**
- Chọn **Save changes**

![VPC Deployment](/images/Lab-1/11-TGWRoute/0003.png?featherlight=false&width=90pc)

4. Hoàn thành thêm **Route**. Thực hiện thêm **Route** tương tự với **NP2-stack_name-Private và  P1-stack_name-Private**

![VPC Deployment](/images/Lab-1/11-TGWRoute/0004.png?featherlight=false&width=90pc)

5. Quay lại giao diện **AWS Cloud9**

- Thực hiện lệnh sau để liệt kê **PrivateIPAddress** của các instance

```
aws ec2 describe-instances | grep "PrivateIpAddress" | cut -d '"' -f 4 | awk 'NR == 0 || NR % 4 == 0'
```

![VPC Deployment](/images/Lab-1/11-TGWRoute/0005.png?featherlight=false&width=90pc)

- 10.0.x.x là DCS1 instance
- 10.4.x.x là DC1 instances (Cisco CRS router, Cloud9 instance)
- 10.8.x.x là P1 instance
- 10.16.x.x là NP1 instance
- 10.17.x.x là NP2 instance

6. Trong **AWS Management Console**

- Tìm **System Manager**
- Chọn **System Manager**

![VPC Deployment](/images/Lab-1/11-TGWRoute/0006.png?featherlight=false&width=90pc)

7. Trong giao diện **System Manager**

- Chọn **Session Manager**
- Chọn **Start session**

![VPC Deployment](/images/Lab-1/11-TGWRoute/0007.png?featherlight=false&width=90pc)

8. Trong giao diện **Start a session**

- Chọn **NP1-tgw-Server**
- Chọn **Start session**

![VPC Deployment](/images/Lab-1/11-TGWRoute/0008.png?featherlight=false&width=90pc)

9. Thực hiện ping đến **NP2 server**

```
ping 10.17.22.100 -c5
```

![VPC Deployment](/images/Lab-1/11-TGWRoute/0009.png?featherlight=false&width=90pc)

10. Kiểm tra **DCS1-tgw-Attach-B Subnet**

![VPC Deployment](/images/Lab-1/11-TGWRoute/00010.png?featherlight=false&width=90pc)

11. Kiểm tra **Route Tables**

![VPC Deployment](/images/Lab-1/11-TGWRoute/00011.png?featherlight=false&width=90pc)

12. Kiểm tra **DCS1-tgw-Pub-A Subnet**

![VPC Deployment](/images/Lab-1/11-TGWRoute/00012.png?featherlight=false&width=90pc)

13. Truy cập **Transit gateway route tables**

- Chọn **Blue Route Table**
- Chọn **Route**
- Chọn **Create static route**

![VPC Deployment](/images/Lab-1/11-TGWRoute/00013.png?featherlight=false&width=90pc)

14. Nhầm hạn chế giao tiếp giữa 2 môi trường **Pro** và **Non-Pro**. Trong trang **Create static route**

- **CIDR** **10.16.0.0/13**
- Chọn **Blackhole**
- Chọn **Create static route**

![VPC Deployment](/images/Lab-1/11-TGWRoute/00014.png?featherlight=false&width=90pc)

15. Hoàn thành tạo **Static route**. Thực hiện tạo **blackhole route** cho **Red Route Table** cho **10.8.0.0/13.**

![VPC Deployment](/images/Lab-1/11-TGWRoute/00015.png?featherlight=false&width=90pc)

16. Truy cập vào **System Manager** sau đó **start session** kết nối đến **P1 server**

![VPC Deployment](/images/Lab-1/11-TGWRoute/00016.png?featherlight=false&width=90pc)

17. Thực hiện ping bất kỳ đến **NP1** hoặc **NP2 server**. Chắc chắn là ping thất bại.

```
ping 10.16.22.100 -c5
```

![VPC Deployment](/images/Lab-1/11-TGWRoute/00017.png?featherlight=false&width=90pc)
