---
title : "Network Manager Setup"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 9.1 </b> "
---

#### Network Manager Setup

We will first create a Global Network, which acts as a container for all the objects within your network (Transit Gateways, Sites, Devices, etc). Some of these objects already exist (Transit Gateway) whereas other objets will be created in the next section of the lab (Sites, Devices...)

1. Access to **VPC**

   - Select **Network Manager**
   - Select **Get started**

![Transit Gateway Network Manager](/images/TGWNetworkManager/0001.png?featherlight=false&width=90pc)

2. In the **Network Manager** interface

   - Select **Global networks**
   - Select **Create global network**

![Transit Gateway Network Manager](/images/TGWNetworkManager/0002.png?featherlight=false&width=90pc)

3. In the **Create global network** interface

    - Enter **Name**
    - Enter **Description**
    - Select **Next**

![Transit Gateway Network Manager](/images/TGWNetworkManager/0003.png?featherlight=false&width=90pc)

4. Select **Create global network**

![Transit Gateway Network Manager](/images/TGWNetworkManager/0004.png?featherlight=false&width=90pc)

5. Create **Global networks** successfully.

![Transit Gateway Network Manager](/images/TGWNetworkManager/0005.png?featherlight=false&width=90pc)

6. Go to **Dashboard** and there are currently no resources available.

![Transit Gateway Network Manager](/images/TGWNetworkManager/0006.png?featherlight=false&width=90pc)

7. Select **Transit gateways**. Then select **Register transit gateway**

![Transit Gateway Network Manager](/images/TGWNetworkManager/0007.png?featherlight=false&width=90pc)

8. In the **Register transit gateway** interface

   - Select **Account**
   - Select transit gateways
   - Select **Register transit gateway**

![Transit Gateway Network Manager](/images/TGWNetworkManager/0008.png?featherlight=false&width=90pc)

9. Complete **Register transit gateway**

![Transit Gateway Network Manager](/images/TGWNetworkManager/0009.png?featherlight=false&width=90pc)

10. Then select **Transit gateway network**

    - Select **Overview**
    - Observe will see 2 **Transit gateways**
    - **Transit gateways VPN status** now **UP VPN** 100%.

![Transit Gateway Network Manager](/images/TGWNetworkManager/00010.png?featherlight=false&width=90pc)