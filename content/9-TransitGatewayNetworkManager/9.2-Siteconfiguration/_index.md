---
title : "Site Configuration"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 9.2 </b> "
---

#### Site Configuration

To help build a graphical picture of your global infrastructure we need to supply Network Manager with some additional details about the on-premises infrastructure. In this section we will create the following resources:

Site - This contains information about the physical sites we are connecting into AWS, for example datacentre details.
Link - This contains details about the link capabilities we are using to connect to AWS, e.g. link speed and provider name.
Devices - This stores details about the devices we are using to terminate our network connections from AWS into our on-premises facilities.

1. In the **Network Manager** interface

   - Select **Site**
   - Select **Create site**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00013.png?featherlight=false&width=90pc)

2. In the **Create site** interface

   - Perform site configuration, **Name** enter **On-premise-DC-A**
   - Enter **Description**
   - **Address**, hold **Somerset**
   - About **Latitude** and **Longitude** you enter your coordinates.
   - Select **Create Site**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00014.png?featherlight=false&width=90pc)

3. Create successful site.

![Transit Gateway Network Manager](/images/TGWNetworkManager/00015.png?featherlight=false&width=90pc)

4. Go to **Site** details, select **Links** and select **Create link**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00016.png?featherlight=false&width=90pc)

5. Configure **links**

   - Enter **Name**
   - Enter **Description**
   - **Upload speed (Mbps)** enter **1000**
   - **Download speed (Mbps)** enter **1000**
   - Enter **Provider** as **Awesome-ISP**
   - **Type** is **Broadband**
   - Select **Create link**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00017.png?featherlight=false&width=90pc)

6. Create successful links.

![Transit Gateway Network Manager](/images/TGWNetworkManager/00020.png?featherlight=false&width=90pc)

7. After configuring **Site** and **Links**, next we configure **Devices**

   - In the **Network Manager** interface, select **Devices**
   - Select **Create devices**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00021.png?featherlight=false&width=90pc)

8. Configure **Devices**

   - **Name**, enter **Edge-Route-A**
   - Enter **Description**
   - Select **Model** as **CSR1000V**
   - **Serial number** is **123456789**
   - **Type**, select **Router**
   - **Vendor**, select **Cisco**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00022.png?featherlight=false&width=90pc)

9. For **Location type**

    - Select **On-premise/Data Center/Other Cloud Provider**
    - **Address**, select **Somerset**
    - Enter **Latitude** and **Longitude**
    - Select **Create device**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00023.png?featherlight=false&width=90pc)

10. Configure **device** successfully. Then select **Associate site**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00024.png?featherlight=false&width=90pc)

11. In the **Edit site association** interface

    - Select **site** created.
    - Select **Edit site association**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00025.png?featherlight=false&width=90pc)

12. Select **Links**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00026.png?featherlight=false&width=90pc)

13. Implement **Associate link**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00027.png?featherlight=false&width=90pc)

14. Select the created link and select **Associate link**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00028.png?featherlight=false&width=90pc)

15. **Associate link** successful.

![Transit Gateway Network Manager](/images/TGWNetworkManager/00029.png?featherlight=false&width=90pc)

16. In the **EdgeEdge-Router-A** interface

    - Select **On-premise associations**
    - Select **Associate**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00030.png?featherlight=false&width=90pc)

17. In the **Create on-premises association** interface

    - Select **Customer gateway**
    - Select **link**
    - Select **Create on-premises association**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00031.png?featherlight=false&width=90pc)

18. Complete **on-premises association** creation

![Transit Gateway Network Manager](/images/TGWNetworkManager/00032.png?featherlight=false&width=90pc)