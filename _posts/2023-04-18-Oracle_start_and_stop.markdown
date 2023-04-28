---
layout: post
title:  "Unit 2. Start and stop Oracle."
date:   2023-03-25 14:00:00 +0100
categories: Unit2
permalink: /:categories/:title.html
---
Usually the booting of all DBMS is automatic. When the Operating System starts, it starts the Database Engine. The stop is also automatic. In any case, it is convenient to know the usual steps to start and stop it.

The steps that Oracle actually needs to boot are 3:

- **Startup**: Starts the instance. This involves the allocation of memory for the SGA and the initiation of system processes, the so-called background processes (they are in the background, without us noticing them). Also at this point the parameter file, which in earlier versions of Oracle is called INIT.ORA, is used to start the instance. From version 9i, in addition to the INIT.ORA parameter file, the Server Parameter File (SPFile) can also be used, which allows the server to be started even if the command is given from another machine (and in principle not INIT.ORA parameter file would be available). This SPFile is named SPFILEORCL.ORA (if ORCL is the instance SID). This is a non-editable file. The Startup state is also called **NoMount**.
- **Mount**: Mount the Database. This involves opening the control file, which is a file that has critical information for the database, such as its own name, when it was created, and the name and location of all files that are used when it is working. It's so important that it's even a good idea to have a backup control file that works as a mirror (in fact Oracle creates 3 by default).
- **Open**: open the database. The actual database files will open. When this phase is completed, you can access the Database and use its objects.
  
In the **NoMount** or **Mount** phase, that is the first two states, only the DBA can connect to the Database, to perform administration tasks.

Apart from the automatic start and stop (the usual) with which the three steps are always done, unless there is a problem, let's see how to do it manually with the administrative tools.

We will also take the opportunity to see other things that can be done with the Instance Manager, such as changing parameters, managing sessions connected to the Database, etc.

## Oracle Enterprise Manager OEM - Instance Manager

We have to enter OEM as user SYS user, and connecting as SYSDBA. We can also enter as SYSTEM, by then we won't have permission to do everything.

![StartStop](../assets/Oracle_start_stop/1.png)

Started
In the General tab, when the Database is selected, choose the Started, Mounted or Open options to get to the first, second or third step, respectively (with the Mostrar todos los estados option activated).

stop
In the same tab choose Cerrada (Shutdown). We will have 4 ways to do it, which are ordered from least to strongest:



Normal: Wait for all users to log out, then close the B.D.
Transactional: Wait for users with pending transactions to Commit or Rollback, then close the sessions and the B.D.
Immediate: closes sessions automatically, rolling back all transactions, and then closes the B.D.
Abort: close the B.D. in a fulminating manner. It is not advisable to be too strong.
The most advisable is the third, since some users may take forever to close their sessions.

When we restart an instance it will ask us for some options, in case we want restricted access to the Database (and do administrative tasks; for example only the administrator can enter to be able to make a backup...), or if we want it to be in read-only mode. Finally, it also allows us to start by taking the parameters from the SPFile, or vice versa using a traditional parameter file, from previous versions of Oracle. In this second way we can specify a parameter file modified by us. But we must note that this file must be available from the machine where the boot command is launched, in case we do it from a remote machine. On the other hand, if we use SPFile, it will start with the parameters located on the machine where the server is.



Information and parameters
From the INSTANCE MANAGER you can also view information about the SGA and operating mode.



Initialization parameters can also be viewed.



The parameters can be modified, and some of these, the dynamic ones, the modification will immediately take effect. But the modification of the non-dynamic ones will not take effect until the instance is restarted. In these cases, when the Apply button is pressed, an attempt is made to stop and restart it.

And we must not forget to save the parameters file if we want the changes made to take effect the next day. Then it would be convenient to arrlaunch next time without using the SPFile.

Session management
You can also manage the sessions connected to the instance, to see the characteristics of the session and even to close them if they are not wanted. Among other things, it tells us the connected users, as which user of the Operating System they have authenticated, the name of the machine from which they have connected and through which program.

In the image you can see how there were 3 connections, apart from processes of the same system.

The SYS user has connected from the same server machine (VWindows2003) and having entered as the Operating System Administrator user. The program used is called jrew.exe. It is the Oracle console connection itself.
The SCOTT user has connected from the same server machine (VWindows2003) and having entered as the Operating System Administrator user. The program used is sqlplusw.exe (it's SQL*Plus, obviously).
The user SCOTT, has also connected from the other machine (my real machine) and having entered as user ?lvar (Àlvar). The program used is TOAD.


In the next image we are going to disconnect the SCOTT user from the SQL*Plus session. We just have to press the right button on the session we want to "kill".



The disconnection can be immediate (rolls back the transactions in progress) or post-transaction (waits to confirm or revoke the transaction in progress and then closes it). Notice how after closing this session, nothing can be done from SQL*Plus anymore (and it says so very graphically).



 

 

LINE MODE (SYS user)
Started
Giving the STARTUP command. If we wanted to start in three steps:

STARTUP NOMOUNT;
ALTER DATABASE MOUNT;
ALTER DATABASE OPEN;
Or in two:

STARTUP MOUNT;
ALTER DATABASE OPEN;
stop
Give the SHUTDOWN command.

The parameters can be set: NORMAL (default), TRANSACTIONAL, IMMEDIATE or ABORT.

Initialized parameters
To be able to see the list of initialized parameters, we will issue the SHOW PARAMETERS command.

If we want to modify a parameter without stopping the B.D., we will have to use the ALTER DATABASE statement, but it does not work with all parameters.

If we want to modify any parameter, the simplest and most foolproof way is the one mentioned before: modify an INIT.ORA file, stop the instance and start it again.

Sessions
To control the sessions, more specifically, to terminate them, it would be done by means of the ALTER SYSTEM KILL SESSION command, followed by the session number. We can find this out by consulting a view called V$SESSION, accessible only to administrators (for example SYS):


If we assume that these are the sessions in progress, and we want to close the session of the user SCOTT, we would do it with the sentence you have at the end of the image:
ALTER SYSTEM KILL SESSION '12.42';
Before closing the session, a Rollback will automatically be made, leaving any ongoing transactions without effect. If we don't want to be so drastic, we can do:

ALTER SYSTEM DISCONNECT SESSION '12,42' POST_TRANSACTION;
The system will then wait for the user to confirm (or reverse) the transaction, and then disconnect the user.