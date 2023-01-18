---
title : "Truy cập Cisco CSR Router với Cloud9"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 4.2 </b> "
---

#### Truy cập Cisco CSR Router với Cloud9

AWS Cloud9 là môi trường phát triển tích hợp (IDE) dựa trên đám mây cho phép bạn viết, chạy và gỡ lỗi mã chỉ bằng một trình duyệt. Môi trường này bao gồm một trình soạn mã, trình gỡ lỗi và thiết bị đầu cuối. Cloud9 được trang bị sẵn các công cụ thiết yếu cho các ngôn ngữ lập trình phổ biến, bao gồm JavaScript, Python, PHP và nhiều ngôn ngữ khác, nhờ vậy bạn không cần cài đặt tệp hoặc cấu hình máy phát triển để bắt đầu các dự án mới. Vì IDE Cloud9 là nền tảng dựa trên đám mây, nên bạn có thể làm việc với các dự án từ văn phòng, nhà hoặc bất cứ nơi đâu thông qua máy được kết nối với internet. Cloud9 cũng mang đến trải nghiệm liền mạch cho các ứng dụng serverless đang phát triển, cho phép bạn dễ dàng xác định các tài nguyên, gỡ lỗi và chuyển đổi giữa thực thi cục bộ và từ xa các ứng dụng serverless. Với Cloud9, bạn có thể nhanh chóng chia sẻ môi trường phát triển của mình với nhóm, từ đó cho phép bạn ghép cặp chương trình và theo dõi đầu ra lẫn nhau trong thời gian thực.

1. Chọn **tgw-Workshop**.

- Chọn **Open IDE**.

![VPC Deployment](/images/Lab-1/8/0001.png?featherlight=false&width=90pc)

2. Sau đó, giao diện **AWS Cloud9** xuất hiện.

![VPC Deployment](/images/Lab-1/8/0002.png?featherlight=false&width=90pc)

3. Trong giao diện **Cloud9**.

- Chọn **File**
- Chọn **Upload Local Files...**

![VPC Deployment](/images/Lab-1/8/0003.png?featherlight=false&width=90pc)

4. Chúng ta sẽ chọn file **Key Pair** đã tạo ở bước chuẩn bị. 

![VPC Deployment](/images/Lab-1/8/0004.png?featherlight=false&width=90pc)

5. Di chuyển key đến thư mục **.ssh**.

```
mv _key_name_.pem ~/.ssh/
```

![VPC Deployment](/images/Lab-1/8/0005.png?featherlight=false&width=90pc)

6. Cấp quyền truy cập vào file key.

```
chmod 400 ~/.ssh/_key_name_.pem
```

![VPC Deployment](/images/Lab-1/8/0006.png?featherlight=false&width=90pc)

7. Xem lại **Output** của **Stack CloudFormation**

![VPC Deployment](/images/Lab-1/8/0007.png?featherlight=false&width=90pc)

8. Sử dụng lệnh từ **Output** CloudFormation, sau đó nhập **yes**

![VPC Deployment](/images/Lab-1/8/0008.png?featherlight=false&width=90pc)

9. Thực hiện một số lệnh kiểm tra sau:

```
show ip interface brief
```

```
sh ip int br
```

```
sh ip route
```

![VPC Deployment](/images/Lab-1/8/0009.png?featherlight=false&width=90pc)