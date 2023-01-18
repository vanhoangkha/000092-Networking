---
title : "Cài đặt Site-to-site VPN"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 4.3 </b> "
---

#### Cài đặt Site-to-site VPN

#### VPN Site to Site

Trong phần này, chúng ta tạo 2 VPN Tunnel từ **Transit Gateway** và kết nối chúng thành một instance của **Cisco CSR** trong **Datacenter VPC**. Đó là mô phỏng site-to-site VPNs  giữa môi trường **AWS** và **on-premise/HQ network**. 

Trên thực tế ở môi trường sản xuất, chúng ta sẽ một bộ định tuyến dự phòng và bổ sung băng thông. Mỗi VPN ipsec tunnel cung cấp  lên đến **1.25Gbps**. Trong khi sử dụng nhiều tunnel ipsec, chúng ta có thể cung cấp băng thông bổ sung với việc sử dụng **ECMP (Đa đường dẫn chi phí ngang nhau)** nghĩa là tất cả các tunnel sẽ được sử dụng. Về phía AWS, hỗ trợ tối đa 50 đường dẫn song song (ECMP). Nhiều nhà cung cấp hỗ trợ 4-8 đường dẫn ECMP.

VPN Site to Site dùng trong mô hình hybrid để thiết lập kết nối liên tục giữa môi trường trung tâm dữ liệu truyền thống tới môi trường VPC của AWS. Việc thiết lập kết nối sẽ cần 2
đầu endpoint ở phía AWS và phía khách hàng :
+ Virtual Private Gateway : Được quản lý hoàn toàn bởi AWS ( chia 2 endpoints ở 2 đầu AZ ).
+ Customer Gateway : Đầu endpoint phía khách hàng, có thể là thiết bị phần cứng hoặc
software appliance.

1. Truy cập vào giao diện [VPC](https://us-east-1.console.aws.amazon.com/vpc/home?region=us-east-1#Home:)

![VPC Deployment](/images/Lab-1/9/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **VPC**

- Chọn **Transit gateway attachments**
- Chọn **Crate transit gateway attachment**


![VPC Deployment](/images/Lab-1/9/0002.png?featherlight=false&width=90pc)

3. Thực hiện cấu hình

- Chọn **Transit Gateway ID**
- Chọn **Attachment Type** là **VPN**
- **Customer Gateway (CGW)** chọn **Existing**
- Chọn **Customer Gateway ID (CGW)**
- Đối với **Routing options**, chọn **Dynamic(requires BGP)**

![VPC Deployment](/images/Lab-1/9/0003.png?featherlight=false&width=90pc)

4. Thực hiện cấu hình các **Tunnel**

- **Inside IP CIDR for Tunnel 1** sử dụng **169.254.10.0/30**.
- **Pre-Shared Key for Tunnel 1** sử dụng **awsamazon**
- **Inside IP CIDR for Tunnel 2** sử dụng **169.254.11.0/30**.
- **Pre-Shared Key for Tunnel 2** sử dụng **awsamazon**
- Chọn **Create transit gateway attachment**

![VPC Deployment](/images/Lab-1/9/0004.png?featherlight=false&width=90pc)

5. Đợi khoảng 7 phút, hoàn thành tạo **Transit gateway attachments**

![VPC Deployment](/images/Lab-1/9/0005.png?featherlight=false&width=90pc)

6. Truy cập vào [Transit gateway route tables](https://us-east-1.console.aws.amazon.com/vpc/home?region=us-east-1#TransitGatewayRouteTables:)

- Chọn **Associations**
- Chọn **Create association**

![VPC Deployment](/images/Lab-1/9/0006.png?featherlight=false&width=90pc)

7. Trong giao diện **Create association**, Chọn **Create association**

![VPC Deployment](/images/Lab-1/9/0007.png?featherlight=false&width=90pc)

8. Đã hoàn thành tạo **Association**

![VPC Deployment](/images/Lab-1/9/0008.png?featherlight=false&width=90pc)

9. Cũng trong giao diện **Transit gateway route table**

- Chọn **Green Route Table**
- Chọn **Propagations**
- Chọn **Create propagations**

![VPC Deployment](/images/Lab-1/9/0009.png?featherlight=false&width=90pc)

10. Trong giao diện **Create propagation**

- Chọn **Create propagation**

![VPC Deployment](/images/Lab-1/9/00010.png?featherlight=false&width=90pc)

11. Hoàn thành tạo **propagation**

![VPC Deployment](/images/Lab-1/9/00011.png?featherlight=false&width=90pc)

12. Thực hiện tạo **Propagation** tương tự đối với **Red Route Table và Blue Route Table.**

![VPC Deployment](/images/Lab-1/9/00012.png?featherlight=false&width=90pc)

13. Quay lại giao diện **AWS Cloud9**

- Chúng ta thực hiện cấu hình **VPN** tạo file cấu hình bằng lệnh sau:

```
./createcsr.sh publicip1 publicip2 mycsrconfig.txt
```

![VPC Deployment](/images/Lab-1/9/00013.png?featherlight=false&width=90pc)

14. Chúng ta truy cập vào [Site-to-Site VPN Connections](https://us-east-1.console.aws.amazon.com/vpc/home?region=us-east-1#VpnConnections:)

- Chọn **VPN Connection**
- Chọn **Tunnel details**
- Vì chưa cấu hình nên trạng thái **Down**
- Chúng ta sử dụng 2 địa chỉ IP của **Outside IP address**

![VPC Deployment](/images/Lab-1/9/00014.png?featherlight=false&width=90pc)

15. Quay lại giao diện **Cloud9** thay thế địa chỉ IP Public và chạy lệnh tạo file **mycsrconfig.txt**

```
./createcsr.sh publicip1 publicip2 mycsrconfig.txt
```

![VPC Deployment](/images/Lab-1/9/00015.png?featherlight=false&width=90pc)

16. Chúng ta mở file **mycsrconfig.txt** xem nội dung cấu hình VPN.

![VPC Deployment](/images/Lab-1/9/00016.png?featherlight=false&width=90pc)

17. Sử dụng lệnh để bắt đầu cấu hình

```
conf t
```

- Sau đó, sao chép tất cả lệnh trong file  **mycsrconfig.txt** dán vào cấu hình.

![VPC Deployment](/images/Lab-1/9/00017.png?featherlight=false&width=90pc)

18. Sau khi cấu hình, nhập **exit** để thoát.

![VPC Deployment](/images/Lab-1/9/00018.png?featherlight=false&width=90pc)

19. Để kiểm tra cấu hình thành công ta thực hiện lệnh

```
sh ip int br
```

![VPC Deployment](/images/Lab-1/9/00019.png?featherlight=false&width=90pc)

20.   Hãy đảm bảo rằng chúng tôi đang nhìn thấy các tuyến đường trên Cisco CSR. đầu tiên chúng ta có thể xem BGP đang thấy gì: **show ip bgp summary**. Điều quan trọng nhất cần xem là State / PfxRcd (Các tiền tố đã nhận). Nếu điều này ở trạng thái Hoạt động hoặc Không hoạt động (có thể là một neighbor statement sai: địa chỉ IP, số AS) thì có vấn đề về cấu hình. Những gì chúng ta muốn thấy là một con số. Trên thực tế, nếu mọi thứ được thiết lập chính xác, chúng ta sẽ thấy 4 cho mỗi neighbor:

```
show ip bgp summary
```
![VPC Deployment](/images/Lab-1/9/00020.png?featherlight=false&width=90pc)

21.    Lưu ý rằng chỉ có một next-hop address cho mỗi CIDR của VPC, mặc dù có 2 tunnel tại chỗ. Đây là kết quả của việc không sử dụng ECMP theo mặc định. Chúng ta có thể khắc phục điều này bằng cách cho phép ECMP trong bộ định tuyến CSR của Cisco. Quay lại chế độ cấu hình, chúng ta sẽ đặt đường dẫn tối đa thành 8 trong bộ định tuyến BGP của chúng ta. Chỉ cần thực hiện các lệnh sau:

```
router bgp 65001
address-family ipv4
maximum-paths 8
end
```

![VPC Deployment](/images/Lab-1/9/00021.png?featherlight=false&width=90pc)

22.   Thực hiện lệnh **sh ip route bgp** lần nữa. Chỉ để xác minh các tuyến đường đó đến từ đâu, chúng ta có thể xem qua Green Route Table. Lưu ý: hãy nhớ rằng nó nằm dưới dịch vụ VPC và Transit Gateway Route Tables ở cuối menu bên trái. Nên có 5 tuyến đường được liệt kê.

```
sh ip route bgp
```

![VPC Deployment](/images/Lab-1/9/00022.png?featherlight=false&width=90pc)

23.   Như bạn có thể đoán, tuyến 10.4.0.0/16 là VPC CIDR cho VPC DataCenter mà CSR của Cisco hoạt động. Cisco CSR đang quảng cáo tuyến đường này tới Transit Gateway. Bạn thực sự có thể kiểm tra điều đó bằng cách kiểm tra cấu hình bộ định tuyến với **sh run** và cuộn xuống phần BGP:

![VPC Deployment](/images/Lab-1/9/00023.png?featherlight=false&width=90pc)

24.  Truy cập vào **VPN Connections**

- Chọn **VPN Connection**
- Chọn  **Tunnel details**
- Hai tunnel đã chuyển trạng thái **UP**

![VPC Deployment](/images/Lab-1/0001.png?featherlight=false&width=90pc)

