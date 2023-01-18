---
title : "Triển khai VPC"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 2.1 </b> "
---
#### Triển khai VPC

#### Kiểm tra đã xóa VPC Default 

1. Truy cập vào giao diện [VPC](https://us-east-1.console.aws.amazon.com/vpc/home?region=us-east-1#Home:)

![VPC Deployment](/images/Lab-1/1/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **VPC**

   + Chọn **Your VPC**
   + Kiểm tra số VPC hiện tại là 0.

![VPC Deployment](/images/Lab-1/1/0002.png?featherlight=false&width=90pc)

#### Tạo AWS Key Pair

Đối với Bộ định tuyến trung tâm dữ liệu mô phỏng của chúng ta, chúng ta sẽ cần sử dụng cặp khóa để truy cập SSH an toàn. Khi bạn tạo một cặp khóa trong AWS, khóa công khai sẽ được lưu trữ trong tài khoản của bạn ở khu vực mà bạn tạo. Khóa riêng tư có thể tải xuống ngay lập tức; trên thực tế, đây là lần duy nhất khóa riêng tư sẽ có sẵn, vì vậy hãy tải xuống và lưu trữ nó một cách an toàn.

1. Truy cập vào giao diện [Key Pair](https://us-east-1.console.aws.amazon.com/ec2/v2/home?region=us-east-1#KeyPairs:)

   + Chọn **Create Key pair**

![VPC Deployment](/images/Lab-1/2/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **Create Key Pair**

   - Nhập tên của **Key Pair**
   - Chọn kiểu key pair là **RSA**
   - Chọn **format** là **.pem**
   - Chọn **Create Key Pair**

![VPC Deployment](/images/Lab-1/2/0002.png?featherlight=false&width=90pc)

#### Triển khai VPC

Trong bước này chúng ta sẽ sử dụng CloudFormation để triển khai hạ tầng, cụ thể là triển khai 5 VPC. 

1. Truy cập vào giao diện tạo [Stack CloudFormation](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?stackName=tgw&templateURL=https://ee-assets-prod-us-east-1.s3.amazonaws.com/modules/c1bed8fa7fe74c40bcf1d5397530fdcb/v1/IntermediateLab.1.tgw-vpcs.yaml&param_AvailabilityZoneA=us-east-1a&param_AvailabilityZoneB=us-east-1b) 

   - Trong giao diện tạo stack, chúng ta sẽ nhập stack name
   - Sau đó, chọn các parameter. Đối với **VPC Parameters**, Chọn các AZ. 
   - Chọn **Capabilities**
   - Chọn **Create stack**

![VPC Deployment](/images/Lab-1/3/0001.png?featherlight=false&width=90pc)

2. Đợi khoảng 20 phút sau, chúng ta sẽ hoàn thành tạo stack.

![VPC Deployment](/images/Lab-1/3/0002.png?featherlight=false&width=90pc)

3. Chi tiết stack được tạo gồm 5 VPC trong 2 AZ và sử dụng IP **10.0.0.0/8** và môi trường **AWS Cloud9**

![VPC Deployment](/images/Lab-1/3/0003.png?featherlight=false&width=90pc)






