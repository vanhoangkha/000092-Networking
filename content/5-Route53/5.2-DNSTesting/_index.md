---
title : "DNS Testing"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 5.2 </b> "
---

#### DNS Testing

#### DNS between Datacenter and VPCs

1. Access **AWS System Manager**

    - Select **Session Manager**
    - Select **Start session**

![DNS Components Deployment](/images/Lab-2-DNS/1/0003.png?featherlight=false&width=90pc)

2. In the **Start session** interface

   - Select **NP1-tgw-Server**
   - Select **Start session**

![DNS Components Deployment](/images/Lab-2-DNS/1/0004.png?featherlight=false&width=90pc)

3. In the **Session** interface, do a ping **np1.your_domain_name**

```
ping np1.aws.example.com
```

![DNS Components Deployment](/images/Lab-2-DNS/1/0005.png?featherlight=false&width=90pc)

4. Continue with the command:

```
dig aws.example.com
```

![DNS Components Deployment](/images/Lab-2-DNS/1/0006.png?featherlight=false&width=90pc)

5. In the **AWS Management Console** interface

   - Find **Route 53**
   - Select **Route 53**

![DNS Components Deployment](/images/Lab-2-DNS/1/0007.png?featherlight=false&width=90pc)

6. Select **Outbound endpoints**


![DNS Components Deployment](/images/Lab-2-DNS/1/0008.png?featherlight=false&width=90pc)

7. Select **tgw-dns-dc1outendpoint**


![DNS Components Deployment](/images/Lab-2-DNS/1/0009.png?featherlight=false&width=90pc)

8. Select **rule** to display

![DNS Components Deployment](/images/Lab-2-DNS/1/00010.png?featherlight=false&width=90pc)

9. Start session with **DC1-tgw-BIND**, select **Start session**

![DNS Components Deployment](/images/Lab-2-DNS/1/00011.png?featherlight=false&width=90pc)

10. Execute the following commands:

```
sudo su
```

```
cat /etc/named.conf
```

![DNS Components Deployment](/images/Lab-2-DNS/1/00012.png?featherlight=false&width=90pc)

11. Go to **Inbound Endpoint**, select **Ednpoint** to display.

![DNS Components Deployment](/images/Lab-2-DNS/1/00013.png?featherlight=false&width=90pc)

12. View details **Inbound Endpoint**

![DNS Components Deployment](/images/Lab-2-DNS/1/00014.png?featherlight=false&width=90pc)

13. Go to **Route 53**, select **Hosted zones**, we will see the created domain names.

![DNS Components Deployment](/images/Lab-2-DNS/1/00015.png?featherlight=false&width=90pc)