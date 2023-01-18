---
title : "Routing Configuration"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 8.2 </b> "
---

#### Routing Configuration

#### Configuring VPC Routing - NP1 Private Subnets

1. Sau khi tạo thành công **Peering Connection**. Chọn và xem chi tiết.

![VPC Peering](/images/Lab-VPC-Peering/0009.png?featherlight=false&width=90pc)

2. Quay lại trang **VPC**, chọn **Route tables**

![VPC Peering](/images/Lab-VPC-Peering/00010.png?featherlight=false&width=90pc)

3. Tìm **NP1-tgw-Private Route Table**

![VPC Peering](/images/Lab-VPC-Peering/00011.png?featherlight=false&width=90pc)

4. Trong giao diện **NP1-tgw-Private Route Table**

- Chọn **Routes**
- Chọn **Edit routes**

![VPC Peering](/images/Lab-VPC-Peering/00012.png?featherlight=false&width=90pc)

5. Trong giao diện **Edit routes**

- Chọn **Add route**
- **Destination: 10.17.0.0/16**
- **Target** chọn **Peering Connection** đã tạo 
- Sau đó bỏ **default route 0.0.0.0/0**, không sử dụng **Transit gateway**
- Chọn **Save routes**

![VPC Peering](/images/Lab-VPC-Peering/00013.png?featherlight=false&width=90pc)

6. Hoàn thành cấu hình Route cho **VPC Peering**

![VPC Peering](/images/Lab-VPC-Peering/00014.png?featherlight=false&width=90pc)

#### Configuring VPC Routing - NP2 Private Subnets

1. Chúng ta quay lại giao diện **VPC**, chọn **Route tables**. Sau đó tìm **NP2** và chọn **NP2-tgw-Private Route Table**

![VPC Peering](/images/Lab-VPC-Peering/00015.png?featherlight=false&width=90pc)

2. Trong giao diện **NP2-tgw-Private Route Table**

- Chọn **Routes**
- Chọn **Edit routes**

![VPC Peering](/images/Lab-VPC-Peering/00016.png?featherlight=false&width=90pc)

3. Trong giao diện **Edit route**

- Chọn **Add Route**
- **Destination: 10.16.0.0/16**
- **Target**, chọn **Peering Connection**
- Thực hiện remove  default route 0.0.0.0/0, không sử dụng **Transit Gateway**
- Chọn **Save Routes**

![VPC Peering](/images/Lab-VPC-Peering/00017.png?featherlight=false&width=90pc)

4. Hoàn thành cấu hình Route.

![VPC Peering](/images/Lab-VPC-Peering/00018.png?featherlight=false&width=90pc)


