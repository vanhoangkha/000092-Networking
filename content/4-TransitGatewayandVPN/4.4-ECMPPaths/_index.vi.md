---
title : "Thêm ECMP Path"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4.4 </b> "
---

#### Thêm ECMP Path

**Equal-cost multi-path routing (ECMP)** hay **Equal Cost Multiple Path** là 1 tính năng cho phép thiết bị mạng như router, switch hay firewall sử dụng nhiều đường dẫn tốt nhất có chi phí bằng nhau đến cùng 1 đích. Các tuyến đường này sẽ được ECMP đưa vào bảng định tuyến và cân bằng tải lưu lượng để tăng băng thông của hệ thống.

Nếu không có ECMP, nếu có nhiều tuyến đường có chi phí ngang nhau đến cùng một đích, các thiết bị mạng sẽ chọn một trong các tuyến đường đó từ bảng định tuyến và thêm nó vào bảng chuyển tiếp của nó (Forwarding Information Base FIB), nó sẽ không sử dụng bất kỳ tuyến đường nào khác trừ khi có sự cố trong tuyến đường đã chọn.

Cân bằng tải ECMP được thực hiện ở cấp phiên (session), không phải ở cấp gói (Packet) - thời điểm bắt đầu một phiên mới là khi thiết bị mạng (ECMP) chọn một đường dẫn chi phí ngang nhau để truyền tải gói tin.

Khả năng mở rộng băng thông và Tính khả dụng cao được tích hợp sẵn trong **Transit Gateway** cũng như thông qua **multiple Availability Zone (AZ) attachments** cho các VPC của chúng ta. Tuy nhiên; để kết nối trở lại Trung tâm dữ liệu của chúng ta, chúng ta có một số điều cần xem xét. Trên thực tế, chúng ta sẽ tạo một  Customer Gateway khác trên một thiết bị vật lý hoàn toàn tách biệt. Lý tưởng nhất, về mặt vật lý, điều này được cách ly về mặt vật lý với Customer Gateway đầu tiên mà chúng ta có thể tạo ra nó (hãy nghĩ, xuyên phòng hoặc thậm chí trong một phòng liên lạc khác với kết nối và nguồn điện riêng biệt nếu chúng ta có). Nhưng để phân phối tải trên cả hai Customer Gateway trong trung tâm dữ liệu, bạn thường sử dụng một cấp bộ định tuyến khác (được hiển thị bên dưới làm bộ định tuyến lõi) để cân bằng lưu lượng. Đối với mục đích demo của chúng ta, hãy xây dựng nó trên cùng một CSR của Cisco mà chúng ta có trong Trung tâm dữ liệu mô phỏng của mình để chúng ta có thể thấy nhiều ECMP hơn trong hoạt động.

![VPC Deployment](/images/vpn-ecmp.png?featherlight=false&width=70pc)

1. Truy cập vào **Transit Gateway attachment**

- Chúng ta sẽ tạo 1 **VPN-ECMP** transit gateway attachment.

![VPC Deployment](/images/Lab-1/10-ECMP/0001.png?featherlight=false&width=90pc)

2. Thực hiện cấu hình

- Chọn **Transit Gateway ID**
- Chọn **Attachment Type** là **VPN**
- Đối với **Customer Gateway (CGW)**, chọn **Existing**
- Đối với **Routing options**, cài **Dynamic(requires BGP)**
  
![VPC Deployment](/images/Lab-1/10-ECMP/0002.png?featherlight=false&width=90pc)

3. Thực hiện cấu hình các **Tunnel**

- **Inside IP CIDR for Tunnel 1** sử dụng **169.254.12.0/30** cho **CIDR**
- **Pre-Shared Key for Tunnel 1** sử dụng **awsamazon**
- **Inside IP CIDR for Tunnel 2** sử dụng **169.254.13.0/30**
- **Pre-Shared Key for Tunnel 2** sử dụng **awsamazon**
- Chọn **Create transit gateway attachment**

![VPC Deployment](/images/Lab-1/10-ECMP/0003.png?featherlight=false&width=90pc)

4. Đợi khoảng 7 phút sau, hoàn thành tạo **VPN-ECMP** transit gateway attachment.

![VPC Deployment](/images/Lab-1/10-ECMP/0004.png?featherlight=false&width=90pc)

5. Kiểm tra **VPN-ECMP connection**

![VPC Deployment](/images/Lab-1/10-ECMP/0005.png?featherlight=false&width=90pc)

6. Thực hiện truy cập vào **Transit gateway route tables**

- Chọn **Green Route Table**
- Chọn **Associations**
- Chọn **Create association**

![VPC Deployment](/images/Lab-1/10-ECMP/0006.png?featherlight=false&width=90pc)

7. Trong giao diện **Create association**

- Chọn **Create association**

![VPC Deployment](/images/Lab-1/10-ECMP/0007.png?featherlight=false&width=90pc)

8. Hoàn thành tạo **association**

![VPC Deployment](/images/Lab-1/10-ECMP/0008.png?featherlight=false&width=90pc)

9. Chọn **Green Route Table**

- Chọn **Propagations**
- Chọn **Create propagation**

![VPC Deployment](/images/Lab-1/10-ECMP/0009.png?featherlight=false&width=90pc)

10. Trong giao diện **Propagation**

- Chọn **Create propagation**

![VPC Deployment](/images/Lab-1/10-ECMP/00010.png?featherlight=false&width=90pc)

11. Hoàn thành tạo **Propagation**. Thực hiện lại bước tạo **Progapation** đối với **Red Route Table và Blue Route Tables.**

![VPC Deployment](/images/Lab-1/10-ECMP/00011.png?featherlight=false&width=90pc)

12. Truy cập vào **VPN connections**

- Chọn **VPN ECMP connection**
- Chọn **Tunnel details**
- Sử dụng **Outside IP addresses** để bước tiếp theo cấu hình.
- Hiện tại chưa cấu hình nên trạng thái **Down**

![VPC Deployment](/images/Lab-1/10-ECMP/00012.png?featherlight=false&width=90pc)

13. Truy nhập vào giao diện **AWS Cloud9**, thực hiện cấu hình bằng cách chạy lệnh tạo file **my2ndcsrconfig.txt**

```
./create2ndcsr.sh publicip1 publicip2 my2ndcsrconfig.txt
```

![VPC Deployment](/images/Lab-1/10-ECMP/00013.png?featherlight=false&width=90pc)

14. Thực hiện kết nối SSH từ **Output** của **CloudFormation**

- Thực hiện lệnh cấu hình

```
conf t
```

- Sau đó, sao chép nội dung  file **my2ndcsrconfig.txt** và cấu hình.

![VPC Deployment](/images/Lab-1/10-ECMP/00014.png?featherlight=false&width=90pc)

15. Chúng ta kiểm tra sẽ thấy có thêm **Tunnel3 và Tunnel4**

```
sh ip int br
```

![VPC Deployment](/images/Lab-1/10-ECMP/00015.png?featherlight=false&width=90pc)

16.  Hãy đảm bảo rằng chúng tôi đang nhìn thấy các tuyến đường trên Cisco CSR. đầu tiên chúng ta có thể xem BGP đang thấy gì: **show ip bgp summary**. Điều quan trọng nhất cần xem là State / PfxRcd (Các tiền tố đã nhận). Nếu điều này ở trạng thái Hoạt động hoặc Không hoạt động (có thể là một neighbor statement sai: địa chỉ IP, số AS) thì có vấn đề về cấu hình. Những gì chúng ta muốn thấy là một con số. Trên thực tế, nếu mọi thứ được thiết lập chính xác, chúng ta sẽ thấy 4 cho mỗi neighbor:

```
sh ip bgp summ
```

![VPC Deployment](/images/Lab-1/10-ECMP/00016.png?featherlight=false&width=90pc)

17. Để xác minh thiết lập **Equal Cost Multipathing (ECMP)** sử dụng lệnh **sh ip ro**. Các tunnel đều up.

```
sh ip ro
```

![VPC Deployment](/images/Lab-1/10-ECMP/00017.png?featherlight=false&width=90pc)

18. Ngoài ra, bạn có thể sử dụng show ip route bgp như chúng ta đã làm trước đây để chỉ xem các đường BGP).

```
show ip route bgp
```

![VPC Deployment](/images/Lab-1/10-ECMP/00018.png?featherlight=false&width=90pc)

