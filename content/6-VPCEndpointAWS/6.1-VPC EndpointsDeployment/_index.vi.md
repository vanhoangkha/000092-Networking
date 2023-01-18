---
title : "Triển khai VPC Endpoint"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 6.1 </b> "
---

#### Triển khai VPC Endpoint

Trong môi trường nhiều VPC, chúng ta có lựa chọn thời điểm  xác định  nơi các VPC Endpoint này: Trong local VPC đang truy cập vào dịch vụ AWS hoặc trong một VPC chung, được chia sẻ. Trong một số trường hợp, bạn có thể cung cấp một số VPC Endpoint  ở VPC trung tâm  và  một số VPC Endpoint ở local. Trong bài lab này, chúng ta sẽ thêm KMS VPC Endpoint  trong DCS1 VPC và các VPC khác  sẽ có thể sử dung Endpoint trung tâm này.

1. Truy cập vào **AWS System Manager**

- Chọn **Session Manager**
- Chọn **Start Session**
- Chọn **NP2 Instance**
- Chọn **Start session**

![VPC Endpoint](/images/Lab-VPC-Endpoint-AWS/1/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **Session**

Sử dụng lệnh sau:

```
dig kms.your_region.amazonaws.com
```

![VPC Endpoint](/images/Lab-VPC-Endpoint-AWS/1/0002.png?featherlight=false&width=90pc)

Như bạn có thể đoán, trước khi VPC Endpoint được cấp phép, giao tiếp hướng tới dịch vụ KMS từ NP2 instance sẽ truyền qua DCS1 NAT Gateway (cũng sẽ tận dụng nternet Gateway bên trong VPC). Đây là kết quả trực tiếp của việc KMS phân giải public ip addresses. Đây là luồng lưu lượng truy cập trông như thế này:

![VPC Deployment](/images/kms-noendpoint.png?featherlight=false&width=70pc)

Nhưng bây giờ chúng tôi muốn quên việc quản lý kết nối công cộng và sử dụng  KMS VPC Endpoint trung tâm này bất cứ khi nào có thể. Để làm được điều đó, chúng ta sẽ cung cấp:

- KMS VPC Endpoint trong DCS1 VPC
- Route 53 Private Hosted Zone được liên kết với NP2 VPC để mọi truy vấn DNS cho dịch vụ KMS đều được chuyển đến VPC Endpoint trong DCS1 VPC.

![VPC Deployment](/images/kms-endpoint.png?featherlight=false&width=70pc)

#### VPC Endpoints - Deployment

1. Truy cập vào giao diện tạo [stack CloudFormation](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?stackName=tgw-kms&templateURL=https://ee-assets-prod-us-east-1.s3.amazonaws.com/modules/c1bed8fa7fe74c40bcf1d5397530fdcb/v1/IntermediateLab.5.tgw-endpoints.yaml&param_ParentStack=tgw)

- Chọn tất cả mặc định
- Chọn **Create stack**

![VPC Endpoint](/images/Lab-VPC-Endpoint-AWS/1/0003.png?featherlight=false&width=90pc)

2. Đợi 20 phút sau, hoàn thành tạo stack.

![VPC Endpoint](/images/Lab-VPC-Endpoint-AWS/1/0004.png?featherlight=false&width=90pc)



