---
title : "VPC Peering Request"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 8.1 </b> "
---

#### VPC Peering Request

1. Access to **VPC**

    - Select **Peering connections**

![VPC Peering](/images/Lab-VPC-Peering/0001.png?featherlight=false&width=90pc)

Peering Connections allow us to connect two VPCs, even in other AWS Accounts. We will focus on the local region, but you can also create cross-region VPC peering.

2. In the **Peering Connection** interface

   - Select **Create Peering connection**

![VPC Peering](/images/Lab-VPC-Peering/0002.png?featherlight=false&width=90pc)

3. In the interface **Create peering connection**

   - Enter **Name** **NP1toNP2**
   - Select **VPC ID** select **NP1-tgw**

![VPC Peering](/images/Lab-VPC-Peering/0003.png?featherlight=false&width=90pc)

4. Continue configuration

   - In the **Select another VPC to peer with** section, select **My account**
   - Region, select 5 **us-east-1**
   - Select **VPC ID**, select **NP2-tgw**
   - Select **Create peering connection**

![VPC Peering](/images/Lab-VPC-Peering/0004.png?featherlight=false&width=90pc)

5. Create VPC Peering successfully.

![VPC Peering](/images/Lab-VPC-Peering/0005.png?featherlight=false&width=90pc)

6. We will make **Accept request**

![VPC Peering](/images/Lab-VPC-Peering/0006.png?featherlight=false&width=90pc)

7. Select **Accept request**

![VPC Peering](/images/Lab-VPC-Peering/0007.png?featherlight=false&width=90pc)

8. Complete initialization of **Peering Connect** between **NP1** and **NP2**

![VPC Peering](/images/Lab-VPC-Peering/0008.png?featherlight=false&width=90pc)