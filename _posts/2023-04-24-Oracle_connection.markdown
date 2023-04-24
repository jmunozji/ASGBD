---
layout: post
title:  "Unit 2. Oracle connection."
date:   2023-04-24 12:00:00 +0100
categories: Unit2
permalink: /:categories/:title.html
---
# Connect to de database

In the previous notes we have installed the Oracle Server and the tools we can use to connect to the database in the same machine:

- Command Line Mode
- OEM - Oracle Enterprise Manager
- SQL Developer

But in a real situation we as database administrators will not be directly connected to the server, but rather on a completely different computer in our office far away. We are going to see in this section how to connect to the database in this situation. We will see it in order of complexity.

## Connect using OEM - Oracle Enterprise Manager

As we saw in the previous section, in Oracle 11g the OEM is a web page we can access using any web browser. So it shouldn't have to be difficult to connect to it. When we were directly connected to the server we used this address "https://localhost:1158/em", so now, in a different computer we just have to change the IP address from "localhost" to the public IP address of the server. The way to get the IP address can be different if we have our server in Azure or on a local VirtualBox VM. Read the following section that fits your situation. You can ignore the other one.

**VirtualBox VM**

In this case you have to make sure to select your network adapter as "Bridged adapter".

![connection](../assets/Oracle_connection/connection01.png)

When you run the VM you will see the IP address just keeping the cursor over the network icon in the down right area of the window.

![connection](../assets/Oracle_connection/connection02.png)

**VM in Azure**

If your VM is in Azure we saw how to get the public IP address when we created the VM. Just to remember it, it is in the VM page.

![WindowsServerInstallation](../assets/Windows_Server_in_Azure/16.png)

Well, we already have the public IP address in eithe case so we continue the same way no matter where the VM is located. We just have to open a web browser in our computer and go to: "https://*publicIPaddress*:1158/em" changing *publicIPaddress* for the IP of the server. If we do it well probably get nothing. That's because the server firewall is blocking the connection. We have to open this ports:

- TCP 1158
- TCP 1521

Open the server and find "Windows Firewall". Create a new "Inbond rule".

Open by port.
![connection](../assets/Oracle_connection/connection03.png)

Open those TCP ports
![connection](../assets/Oracle_connection/connection04.png)

You can leave the rest of options without changing anything. Give the rule the name you want.
![connection](../assets/Oracle_connection/connection05.png)

Now try to open the OEM again.

> Remember *Orace Enterprise Manager 11g* uses TLS 1.0 and 1.1. which are disabled by default in web browsers nowadays. In Mozilla Firefox last versions you can learn how to do it [here](https://support.mozilla.org/en-US/questions/1101896).

Once the TLS problem is solved you will have access to the OEM.
![connection](../assets/Oracle_connection/connection06.png)

