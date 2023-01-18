---
title : "Kiểm tra DNS"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 5.2 </b> "
---

#### Kiểm tra DNS

#### DNS giữa Datacenter và các VPC

1. Truy cập **AWS System Manager**

- Chọn **Session Manager**
- Chọn **Start session**

![DNS Components Deployment](/images/Lab-2-DNS/1/0003.png?featherlight=false&width=90pc)

2. Trong giao diện **Start session**

- Chọn **NP1-tgw-Server**
- Chọn **Start session**

![DNS Components Deployment](/images/Lab-2-DNS/1/0004.png?featherlight=false&width=90pc)

3. Trong giao diện **Session**, thực hiện ping **np1.your_domain_name**

```
ping np1.aws.example.com
```

![DNS Components Deployment](/images/Lab-2-DNS/1/0005.png?featherlight=false&width=90pc)

4. Tiếp tục với lệnh:

```
dig aws.example.com
```

![DNS Components Deployment](/images/Lab-2-DNS/1/0006.png?featherlight=false&width=90pc)

5. Trong giao diện **AWS Management Console**

- Tìm **Route 53**
- Chọn **Route 53**

![DNS Components Deployment](/images/Lab-2-DNS/1/0007.png?featherlight=false&width=90pc)

6. Chọn **Outbound endpoints**


![DNS Components Deployment](/images/Lab-2-DNS/1/0008.png?featherlight=false&width=90pc)

7. Chọn **tgw-dns-dc1outendpoint**


![DNS Components Deployment](/images/Lab-2-DNS/1/0009.png?featherlight=false&width=90pc)

8. Chọn **rule** hiện thị

![DNS Components Deployment](/images/Lab-2-DNS/1/00010.png?featherlight=false&width=90pc)

9. Bắt đầu session với **DC1-tgw-BIND**, chọn **Start session**

![DNS Components Deployment](/images/Lab-2-DNS/1/00011.png?featherlight=false&width=90pc)

10. Thực hiện các lệnh sau:

```
sudo su
```

```
cat /etc/named.conf
```

![DNS Components Deployment](/images/Lab-2-DNS/1/00012.png?featherlight=false&width=90pc)

11. Truy cập vào **Inbound Endpoint**, chọn **Ednpoint** hiển thị.

![DNS Components Deployment](/images/Lab-2-DNS/1/00013.png?featherlight=false&width=90pc)

12. Xem chi tiết **Inbound Endpoint**

![DNS Components Deployment](/images/Lab-2-DNS/1/00014.png?featherlight=false&width=90pc)

13. Truy cập vào **Route 53**, chọn **Hosted zones**, chúng ta sẽ thấy các domain name đã tạo.

![DNS Components Deployment](/images/Lab-2-DNS/1/00015.png?featherlight=false&width=90pc)
