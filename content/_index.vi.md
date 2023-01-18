---
title : "AWS Networking and Content Delivery"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
---
# AWS Networking and Content Delivery

#### Tổng quan về các dịch vụ Networking trên AWS

![VPC Deployment](/images/hybrid-routes-diagram.png?featherlight=false&width=70pc)

#### Availability Zone ( AZ )

Một Availability Zone ( AZ ) bao gồm một hoặc nhiều trung tâm dữ liệu, các (AZ) được thiết kế để không xảy ra sự cố ảnh hưởng đồng thời 2 AZ một lúc (fault isolation)
Giữa 2 AZ là đường kết nối riêng tốc độ cao.AWS khuyến nghị nên triển khai ứng dụng tối thiểu trên 2 AZ.

#### Region 

Một AWS Region bao gồm tối thiểu 3 Availability Zone. Hiện tại có hơn 25 Region trên toàn cầu. Các Region được kết nối với nhau bởi mạng backbone của AWS.
Mặc định dữ liệu và dịch vụ ở các Region độc lập với nhau. ( Trừ một số dịch vụ ở quy mô Global ).

#### Edge Locations

Là mạng lưới trung tâm dữ liệu AWS được thiết kế để cung cấp dịch vụ với độ trễ thấp nhất có thể. Các dịch vụ AWS hoạt động tại Edge Locations bao gồm
+ CloudFront ( CDN )
+ Web Application Firewall ( WAF )
+ Route 53 ( DNS Service )

#### Amazon Virtual Private Cloud ( VPC )

Amazon Virtual Private Cloud (Amazon VPC) cho phép bạn khởi chạy các tài nguyên AWS vào một mạng ảo mà bạn đã xác định. VPC nằm trong 1 Region , khi tạo VPC cần khai báo 1 lớp mạng CIDR IPv4 (bắt buộc) và IPv6 (tùy chọn). Giới hạn của VPC hiện tại là 5 VPC trên 1 AWS Region trên 1 AWS Account. Mục đích chính sử dụng VPC thường dùng để phân tách các môi trường.(Production/Dev/Test/Staging).

Lưu ý : Nếu muốn các tài nguyên tách biệt hẳn ( User không thể nhìn thấy một tài nguyên cụ thể thì cần tách thành nhiều AWS account , nhiều VPC không giải quyết được vấn đề này )

#### Amazon Virtual Private Cloud ( VPC ) – Subnet

Amazon VPC cho phép tạo nhiều mạng ảo và chia các mạng ảo này thành các mạng con (subnet ). VPC Subnet sẽ nằm trong 1 Availability Zone cụ thể. Khi tạo Subnet, chúng ta chỉ định CIDR cho mạng con đó và đây là một tập hợp con của khối VPC CIDR.

Trong mỗi Subnet , AWS sẽ giữ 5 địa chỉ IP. Ví dụ nếu Subnet có CIDR là 10.10.1.0/24
+ Địa chỉ network ( 10.10.1.0 )
+ Địa chỉ broadcast ( 10.10.1.255 )
+ Địa chỉ cho bộ định tuyến ( 10.10.1.1 )
+ Địa chỉ cho DNS ( 10.10.1.2 )
+ Địa chỉ cho tính năng tương lai ( 10.10.1.3 )

#### Amazon Virtual Private Cloud ( VPC ) – Route table

Route table ( Bảng định tuyến ) , tập hợp các Route , để xác định đường đi cho mạng. Khi tạo VPC , AWS sẽ tạo một Default Route table , Default Route table không thể bị xóa và chỉ chứa 1 Route duy nhất là Route cho phép tất cả các Subnet trong VPC liên lạc với nhau. Route table sẽ được gán vào Subnet. Chúng ta có thể tạo Custom Route table ( bảng định tuyến tùy chỉnh ) , tuy nhiên sẽ không thể xóa default route. (VPC CIDR – Local)

#### Amazon Virtual Private Cloud ( VPC ) – Elastic Network Interface ( ENI )

Elastic Network Interface ( ENI ) là một card mạng ảo, chúng ta có thể chuyển sang các EC2
Instance khác.
Khi chuyển sang một máy chủ mới, một card mạng ảo sẽ vẫn duy trì:

+ Địa chỉ IP Private
+ Địa chỉ Elastic IP address
+ Địa chỉ MAC

#### Amazon Virtual Private Cloud ( VPC ) – Elastic IP address ( EIP )

Elastic IP address ( EIP ) là một địa chỉ public IPv4 tĩnh, có thể liên kết với một Elastic Network Interface.
Khi không sử dụng , sẽ bị charge phí. (tránh lãng phí)

#### Amazon Virtual Private Cloud ( VPC ) – VPC Endpoint

VPC Endpoint cho phép chúng ta kết nối các tài nguyên nằm trong VPC tới các dịch vụ AWS được hỗ trợ ( AWS PrivateLink – đi qua mạng private của AWS) mà không cần thông qua kết nối internet.

Có 2 kiểu VPC Endpoint :

+ Interface Endpoint : Sử dụng một Elastic Network Interface trong VPC cũng với một địa chỉ
IP Private để kết nối tới 1 dịch vụ hỗ trợ.

+ Gateway Endpoint : Sử dụng một route table để định tuyến tới endpoint của dịch vụ hỗ trợ
( S3 và Dynamo DB )

#### Amazon Virtual Private Cloud ( VPC ) – Internet Gateway

Internet Gateway là một thành phần của Amazon VPC có khả năng mở rộng quy mô theo chiều ngang ( scale out ) cho phép các EC2 Instance trong VPC có thể truyền thông tin ra ngoài Internet. Internet Gateway được quản lý bởi AWS , chúng ta không cần cấu hình autoscale hoặc high availability.

#### Amazon Virtual Private Cloud ( VPC ) – NAT Gateway

NAT Gateway cho phép các EC2 instance trong subnet truy cập tới internet hoặc các dịch vụ AWS khác. Chỉ chấp nhận kết nối chiều ra và không chấp nhận kết nối chiều vào.

#### Amazon Virtual Private Cloud ( VPC ) – Security Group

Security Group ( SG ) là một tường lửa ảo có lưu giữ trạng thái ( stateful ) giúp kiểm soát lượng truy cập đến và đi trong tài nguyên của AWS.
Security Group rule được hạn chế theo giao thức, địa chỉ nguồn, cổng kết nối , hoặc một Security Group khác.
+ Security Group rule chỉ cho phép rule allow.
+ Security Group được áp dụng lên các Elastic Network Interface.
+ Mặc định Security Group chặn mọi truy cập đến và cho phép mọi truy cập đi.

#### Amazon Virtual Private Cloud ( VPC ) – Network Access Control List ( NACL )

Network Access Control List ( NACL ) là một tường lửa ảo không lưu giữ trạng thái (stateless) giúp kiểm soát lượng truy cập đến và đi trong tài nguyên của AWS.
+ NACL được hạn chế theo giao thức, địa chỉ nguồn, cổng kết nối.
+ Security Group được áp dụng lên các Amazon VPC Subnets
+ Mặc định NACL cho phép mọi truy cập đến và đi.

Rule đọc từ trên xuống dưới. Nếu thỏa rule nào thì lấy rule đó.

#### VPC Peering

VPC Peering là tính năng giúp kết nối hai hay nhiều VPC để các tài nguyên bên trong hai VPC đó có thể liên lạc trực tiếp với nhaukhông cần phải thông qua Internet , góp phần gia
tăng tính bảo mật cho VPC.
+ VPC Peering là kết nối cần tạo 1 : 1 giữa hai VPC thành viên , không hỗ trợ transitive routing.
+ VPC Peering không hỗ trợ khi 2 VPC bị overlap IP address space.

#### Transit Gateway

Transit Gateway được dùng để kết nối các VPC và mạng on-premises thông qua một hub trung tâm. Điều này đơn giản hoá mạng và kết thúc các mối quan hệ định tuyến phức
tạp.
+ Transit Gateway Attachment là một công cụ để gán các subnet của từng VPC cần kết nối với nhau vào một TGW đã được khởi tạo. Transit Gateway Attachment hoạt động ở quy
mô Availability Zone (AZ-level).
+ Trong VPC, khi một subnet ở một AZ có Transit Gateway Attachment với một TGW, các subnet khác trong cùng AZ đều có thể kết nối tới TGW đó.

#### VPN Site to Site

VPN Site to Site dùng trong mô hình hybrid để thiết lập kết nối liên tục giữa môi trường trung tâm dữ liệu truyền thống tới môi trường VPC của AWS. Việc thiết lập kết nối sẽ cần 2
đầu endpoint ở phía AWS và phía khách hàng :
+ Virtual Private Gateway : Được quản lý hoàn toàn bởi AWS ( chia 2 endpoints ở 2 đầu AZ ).
+ Customer Gateway : Đầu endpoint phía khách hàng, có thể là thiết bị phần cứng hoặc
software appliance.

#### AWS Direct Connect

AWS Direct Connect là dịch vụ cho phép tạo kết nối riêng từ trung tâm dữ liệu truyền thống tới AWS.
+ Độ trễ khoảng 20 ms – 30 ms.
+ AWS Direct Connect ở Việt Nam hiện tại sẽ thông qua AWS Direct Connect partners và hoạt động dưới dạng Hosted Connections. ( Nếu trực tiếp tới AWS thì là Dedicated Connections )
+ Băng thông Direct Connect có thể thay đổi lên / xuống tùy nhu cầu.

#### Elastic Load Balancing – Network Load Balancer

Network Load Balancer ( NLB ) là một dịch vụ cân bằng tải được quản lý bởi AWS , hoạt động ở Layer 4.
+ Sử dụng giao thức TCP , TLS.
+ Hỗ trợ tính năng set IP tĩnh.
+ Hỗ trợ hiệu năng cao nhất trong các loại Load Balancer có khả năng xử lý lên đến hàng triệu
request.
+ Cho phép route traffic tới cả target nằm ngoài VPC ( IP address ) , EC2 , Container (ECS,EKS).

#### Nội dung chính

1. [Giới thiệu](1-introduce/)
2. [Các bước chuẩn bị](2-prerequiste/)
3. [VPC Components Deep Dive](3-vpcs/)
4. [Transit Gateway và Site-to-Site VPNs](4-transitgatewayandvpn/)
5. [Route53 DNS Endpoints và Internal Hosted Zones](5-route53/)
6. [VPC Endpoints for AWS Services](6-vpcendpointaws/)
7. [VPC Endpoint Services](7-vpcendpointonpremise/)
8. [VPC Peering](8-vpcpeering/)
9. [Transit Gateway Network Manager](9-transitgatewaynetworkmanager/)
10. [Dọn dẹp tài nguyên](10-cleanup/)