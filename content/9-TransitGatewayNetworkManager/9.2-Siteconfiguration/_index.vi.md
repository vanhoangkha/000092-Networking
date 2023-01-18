---
title : "Cấu hình Site"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 9.2 </b> "
---

#### Cấu hình Site

1. Trong giao diẽn **Network Manager**

- Chọn **Site**
- Chọn **Create site**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00013.png?featherlight=false&width=90pc)

2. Trong giao diện **Create site**

- Thực hiện cấu hình site, **Name** nhập là **On-premise-DC-A**
- Nhập **Description**
- **Address**, giữ **Somerset**
- Về **Latitude** và **Longitude** bạn nhập tọa độ của bạn.
- Chọn **Create Site**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00014.png?featherlight=false&width=90pc)

3. Tạo site thành công.

![Transit Gateway Network Manager](/images/TGWNetworkManager/00015.png?featherlight=false&width=90pc)

4. Vào xem chi tiết **Site**, chọn **Links** và chọn **Create link**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00016.png?featherlight=false&width=90pc)

5. Thực hiện cấu hình **links**

- Nhập **Name**
- Nhập **Description**
- **Upload speed (Mbps)** nhập **1000**
- **Download speed (Mbps)** nhập **1000**
- Nhập **Provider** là **Awesome-ISP**
- **Type** là **Broadband**
- Chọn **Create link**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00017.png?featherlight=false&width=90pc)

6. Tạo links thành công.

![Transit Gateway Network Manager](/images/TGWNetworkManager/00020.png?featherlight=false&width=90pc)

7. Sau khi đã cấu hình **Site** và **Links**, tiếp theo ta cấu hình **Devices**

- Trong giao diện **Network Manager**, chọn **Devices**
- Chọn **Create devices**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00021.png?featherlight=false&width=90pc)

8. Thực hiện cấu hình **Devices**

- **Name**, nhập **Edge-Route-A**
- Nhập **Description**
- Chọn **Model** là **CSR1000V**
- **Serial number** là **123456789**
- **Type**, chọn **Router**
- **Vendor**, chọn **Cisco**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00022.png?featherlight=false&width=90pc)

9. Đối với **Location type**

- Chọn **On-premise/Data Center/ Other Cloud Provider**
- **Address**, chọn **Somerset**
- Nhập **Latitude** và **Longitude**
- Chọn **Create device**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00023.png?featherlight=false&width=90pc)

10. Cấu hình **device** thành công. Sau đó chọn **Associate site**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00024.png?featherlight=false&width=90pc)

11. Trong giao diện **Edit site association**

- Chọn **site** đã tạo.
- Chọn **Edit site association**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00025.png?featherlight=false&width=90pc)

12. Chọn **Links**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00026.png?featherlight=false&width=90pc)

13. Thực hiện **Associate link**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00027.png?featherlight=false&width=90pc)

14. Chọn link đã tạo và chọn **Associate link**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00028.png?featherlight=false&width=90pc)

15. **Associate link** thành công.

![Transit Gateway Network Manager](/images/TGWNetworkManager/00029.png?featherlight=false&width=90pc)

16. Trong giao diện **EdgeEdge-Router-A**

- Chọn **On-premise associations**
- Chọn **Associate**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00030.png?featherlight=false&width=90pc)

17. Trong giao diện **Create on-premises association**

- Thực hiện chọn **Customer gateway**
- Chọn **link**
- Chọn **Create on-premises association**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00031.png?featherlight=false&width=90pc)

18.  Hoàn thành tạo **on-premises association**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00032.png?featherlight=false&width=90pc)

