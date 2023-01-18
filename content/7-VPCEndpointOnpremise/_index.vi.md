---
title : "VPC Endpoint Services"
date :  "`r Sys.Date()`" 
weight : 7
chapter : false
pre : " <b> 7. </b> "
---
#### VPC Endpoint Services

VPC Endpoint Services dựa trên công nghệ AWS PrivateLink, công nghệ này giúp đơn giản hóa việc bảo mật dữ liệu được chia sẻ trên các ứng dụng dựa trên đám mây bằng cách loại bỏ việc tiếp xúc dữ liệu với Internet công cộng. AWS PrivateLink cung cấp kết nối riêng tư giữa các VPC, dịch vụ AWS và các ứng dụng tại chỗ.

Mặc dù chúng tôi có thể chọn cung cấp kết nối với ứng dụng thông qua Transit Gateway, nhưng đôi khi chúng tôi muốn chia sẻ ứng dụng của mình với các khách hàng bên ngoài.

Một số tình huống phổ biến mà bạn có thể muốn sử dụng VPC Endpoint Services:

- Ứng dụng trong VPC không có quyền truy cập VPN hoặc TGW vào VPCS khác.
- Ứng dụng trong VPC có địa chỉ IP chồng chéo với VPC mà bạn muốn chia sẻ
- Chia sẻ ứng dụng với người tiêu dùng bên ngoài trong các tài khoản AWS khác (ngay cả qua MarketPlace)
- Giới hạn các quy tắc tường lửa để truy cập vào một ứng dụng tại chỗ bằng cách sử dụng Privatelink làm điểm truy cập duy nhất cho tất cả VPC trong một khu vực
Trong lab này, chúng ta sẽ tập trung vào trường hợp sử dụng số 3) ở trên.

Chúng tôi sẽ cung cấp Endpoint Service ở "Provider side" (nơi ứng dụng của chúng tôi sẽ được chia sẻ từ đó). Điều này sẽ yêu cầu một Network LoadBalancer (NLB) và tương ứng với phần bên phải của sơ đồ bên dưới (NP2 VPC).

![VPC Deployment](/images/pl-createService.png?featherlight=false&width=70pc)