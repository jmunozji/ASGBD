---
layout: post
title:  "Unit 0. Introduction."
date:   2023-03-17 14:00:00 +0100
categories: Unit0
permalink: /:categories/:title.html
---

# Introduction

In this unit we will focus on creating the environment we will use in future units to install the Oracle database server and clients, and perform all the tasks we will learn. We could use a real server, should we have one. But that is not likely the case, so it is better and less expensive to work with virtual machines.

Among all the possible options you can choose between the following two:

- VMs in VirtualBox
- VM in Microsoft Azure Cloud

If you decide to use VirtualBox, I will provide you the .ova files to create the virtual machines in your computer. If you decide to use Ms Azure, I will show you how to create the VM in Azure cloud. Each solution has advantages and disadvantages. The following table shows you some of them to help you take the decision:

| Item                              | VirtualBox | Azure                                              |
| --------------------------------- | ---------- | -------------------------------------------------- |
| PC Hard disk usage                | High       | Very low                                           |
| PC CPU requirement                | High       | Very low                                           |
| Network usage                     | Low        | High                                               |
| Use from different PC's           | Difficult  | Very easy                                          |
| Number of simultaneous running VM | Low        | Unlimited                                          |
| Velocity to create a VM           | Low        | Very High                                          |
| Usage charges                     | No         | Yes when Azure for students credit (100$) finished |
| Platform complexity | Low | High |
| Know how to use it to get a job | Medium | Very high |

As a conclusion I would say that if you don't have a very powerful PC, Azure would be your choice. In other cases, just decide considering which characteristics are more important to you: disk usage, mobility, learning new systems...

In any case you are going to need a Windows Server to install the Oracle 11g DBMS. In a real environment the DMBS is installed in a machine inside a data center or in the cloud. The DBMS administrators rarely connect directly to this server, but they access the DBMS remotely. Thus, we will learn to connect to the DMBS from a different PC. 

Depending on your PC operating system and the availability of the client programs for it, you can decide to install the client programs in your own PC or create a client VM to install these programs. Therefore we will need:

- Windows Server 2008 or higher
- Windows 7 or higher as client (optional as client)

## VM's in VirtualBox

At this point you might know quite well how to work with VirtualBox. If you decide to use this system, you have to create these virtual machines:

- Windows Server 2008
- Windows 7 (optional as client)

You can find the .ova files [here](https://gvaedu-my.sharepoint.com/:f:/g/personal/j_munozjimeno_edu_gva_es/Etr345tDiSlDsyGdSrelkZIBSFHwZSd1TLmdrYH9Ov8dEw?e=Dev4Br).

Create both machines, configure them with "bridged network" and create a shared folder with your host machine to easily change files between them.

## VM's in Ms Azure

If you decide to use Ms Azure, we can use newer versions of the operatint systems, as they are available in the platform. In this case we will use:

- Windows Server 2012
- Windows 10 (optional as client)

In the following post you have all the information you need to install the Windows Server:

- [Windows Server in Azure](../unit0/Windows_Server_in_Azure.html)