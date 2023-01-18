---
title : "Network Insights"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 9.3 </b> "
---

#### Network Insights

1. Chúng ta sẽ vào **Network Manager**

- Chọn **Transit gateway network**
- Chọn **Geography**
- Xem hình ảnh mô phỏng vị trí và đường kết nối giữa trung tâm dữ liệu ở nội bộ **(On-Premises-DC-A)** với trung tâm dữ liệu trên AWS.
- Chi tiết có 2 Transit Gateway và 4 VPC.
- Connectivity gồm 2 VPN.
- Ở **On-Premises** gồm 1 **Site** và 1 **Device**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00033.png?featherlight=false&width=90pc)

2. Xem chi tiết về **VPN connections** gồm 

- **VPN connection** hiện tại đang **UP**
- **VPN ECMP connection** hiện tại cũng đang **UP**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00034.png?featherlight=false&width=90pc)

3. Kiểm tra trạng thái của **Route**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00035.png?featherlight=false&width=90pc)

4. Xem **Topology tree**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00036.png?featherlight=false&width=90pc)

5. Thực hiện **Monitoring**

- Xem **Byte in**
- Xem **Byte out**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00037.png?featherlight=false&width=90pc)

