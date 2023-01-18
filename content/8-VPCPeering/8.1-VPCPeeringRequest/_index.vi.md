---
title : "VPC Peering Request"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 8.1 </b> "
---

#### VPC Peering Request

1. Truy cập vào **VPC**

- Chọn **Peering connections**

![VPC Peering](/images/Lab-VPC-Peering/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **Peering Connection**

- Chọn **Create Peering connection**

![VPC Peering](/images/Lab-VPC-Peering/0002.png?featherlight=false&width=90pc)

3. Trong gaio diện **Create peering connection**

- Nhập **Name** **NP1toNP2**
- Chọn **VPC ID** chọn **NP1-tgw**

![VPC Peering](/images/Lab-VPC-Peering/0003.png?featherlight=false&width=90pc)

4. Tiếp tục cấu hình

- Trong phần **Select another VPC to peer with**, chọn **My account**
- Region, chon5 **us-east-1**
- Chọn **VPC ID**, chọn **NP2-tgw**
- Chọn **Create peering connection**

![VPC Peering](/images/Lab-VPC-Peering/0004.png?featherlight=false&width=90pc)

5. Tạo VPC Peering thành công.

![VPC Peering](/images/Lab-VPC-Peering/0005.png?featherlight=false&width=90pc)

6. Chúng ta sẽ thực hiện **Accept request**

![VPC Peering](/images/Lab-VPC-Peering/0006.png?featherlight=false&width=90pc)

7. Chọn **Accept request**

![VPC Peering](/images/Lab-VPC-Peering/0007.png?featherlight=false&width=90pc)

8. Hoàn thành khởi tạo **Peering Connect** giữa **NP1** và **NP2**

![VPC Peering](/images/Lab-VPC-Peering/0008.png?featherlight=false&width=90pc)

