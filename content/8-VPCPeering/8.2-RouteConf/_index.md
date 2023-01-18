---
title : "Routing Configuration"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 8.2 </b> "
---

#### Routing Configuration

#### Configuring VPC Routing - NP1 Private Subnets

1. After successfully creating **Peering Connection**. Select and view details.

![VPC Peering](/images/Lab-VPC-Peering/0009.png?featherlight=false&width=90pc)

2. Return to **VPC** page, select **Route tables**

![VPC Peering](/images/Lab-VPC-Peering/00010.png?featherlight=false&width=90pc)

3. Find **NP1-tgw-Private Route Table**

![VPC Peering](/images/Lab-VPC-Peering/00011.png?featherlight=false&width=90pc)

4. In the **NP1-tgw-Private Route Table** interface

    - Select **Routes**
    - Select **Edit routes**

![VPC Peering](/images/Lab-VPC-Peering/00012.png?featherlight=false&width=90pc)

5. In the **Edit routes** interface

   - Select **Add route**
   - **Destination: 10.17.0.0/16**
   - **Target** select the **Peering Connection** created
   - Then remove **default route 0.0.0.0/0**, don't use **Transit gateway**
   - Select **Save routes**

![VPC Peering](/images/Lab-VPC-Peering/00013.png?featherlight=false&width=90pc)

6. Complete Route configuration for **VPC Peering**

![VPC Peering](/images/Lab-VPC-Peering/00014.png?featherlight=false&width=90pc)

#### Configuring VPC Routing - NP2 Private Subnets

1. We return to the **VPC** interface, select **Route tables**. Then find **NP2** and select **NP2-tgw-Private Route Table**

![VPC Peering](/images/Lab-VPC-Peering/00015.png?featherlight=false&width=90pc)

2. In the **NP2-tgw-Private Route Table** interface

   - Select **Routes**
   - Select **Edit routes**

![VPC Peering](/images/Lab-VPC-Peering/00016.png?featherlight=false&width=90pc)

3. In the **Edit route** interface

   - Select **Add Route**
   - **Destination: 10.16.0.0/16**
   - **Target**, select **Peering Connection**
   - Perform remove default route 0.0.0.0/0, do not use **Transit Gateway**
   - Select **Save Routes**

![VPC Peering](/images/Lab-VPC-Peering/00017.png?featherlight=false&width=90pc)

4. Complete Route configuration.

![VPC Peering](/images/Lab-VPC-Peering/00018.png?featherlight=false&width=90pc)
