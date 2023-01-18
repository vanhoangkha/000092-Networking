---
title : "Network Insights"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 9.3 </b> "
---

#### Network Insights

Now that we have all our site information created, we can walk through Network Manager to understand what information we can see for our network.

1. We will enter **Network Manager**

   - Select **Transit gateway network**
   - Select **Geography**
   - View a simulation of the location and connectivity between the local data center **(On-Premises-DC-A)** and the data center on AWS.
   - Details have 2 Transit Gateways and 4 VPCs.
   - Connectivity includes 2 VPNs.
   - In **On-Premises** includes 1 **Site** and 1 **Device**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00033.png?featherlight=false&width=90pc)

2. See details about **VPN connections** including

    - **VPN connection** is currently **UP**
    - **VPN ECMP connection** is currently **UP**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00034.png?featherlight=false&width=90pc)

3. Check status of **Route**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00035.png?featherlight=false&width=90pc)

4. View **Topology tree**. Here we can see the overall topology of the network. It details the Transit Gateway, VPCs and VPNs (taken from the Transit Gateway attachments). The links are contextual which enables us to quickly access detailed configuration details.

![Transit Gateway Network Manager](/images/TGWNetworkManager/00036.png?featherlight=false&width=90pc)

5. Implement **Monitoring**. In a single place you can view all sorts of metrics related to your Transit Gateway. You will also be able to switch between different Transit Gateways.

   - View **Bytes in**
   - View **Byte out**

![Transit Gateway Network Manager](/images/TGWNetworkManager/00037.png?featherlight=false&width=90pc)