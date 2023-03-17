---
layout: post
title:  "Introduction to DBMS."
date:   2023-03-17 14:00:00 +0100
categories:
---
# Introduction to DMBS.

Last year, in the Database Management module we learned how to design, create and manipulate databases using SQL DDL (Data Definition Language) and DML (Data Manipulation Language). In this module we will learn how to use the tool that allows us to implement databases, that is a DataBase Management System or DBMS.

# Functions of the database management system (DBMS).

The functions of the database management system (DBMS) are as follows:

- **Data storage and retrieval**: The DBMS is responsible for storing and retrieving data from the database. It provides a mechanism for creating, reading, updating, and deleting data.

- **Concurrency control**: The DBMS must ensure that multiple users can access the database at the same time without interfering with each other. To do this, the DBMS uses concurrency control techniques to ensure that each user can work with the data safely.

- **Integrity control**: The DBMS is responsible for maintaining the integrity of the data in the database. This means that the data must be accurate and consistent at all times. The DBMS must ensure that the data is not corrupted or becomes inaccurate due to system failures or human errors.

- **Security control**: The DBMS is responsible for ensuring that the data in the database is protected against unauthorized access. This includes user authentication, authorization of database access, and implementation of security policies.

# Components.

We could summarize the components of a DBMS are as follows:

- **Database engine**: It is the core of the DBMS. It controls all database operations, including data storage and retrieval, concurrency control, integrity control, and security control.

- **Query language**: Allows users to perform queries and data manipulations in the database. Examples of query languages are SQL, PL/SQL, T-SQL, etc.

- **User interface**: Allows users to interact with the DBMS. It can be a graphical user interface (GUI), a command line, an API, etc.

- **Administration tools**: Allow database administrators to manage the database and perform tasks such as creating and modifying tables, assigning user permissions, performing backups, etc.

# Types.

There are different types of DBMS, among which are:

- Relational DBMS: Store data in relational tables and use SQL as query language. Examples of relational DBMS are Oracle, MySQL, Microsoft SQL Server, etc.

- NoSQL DBMS: Do not use relational tables to store data. Instead, they use non-relational data structures such as documents, graphs, or columns. Examples of NoSQL DBMS are MongoDB, Cassandra, Couchbase, etc.

- Desktop DBMS: Are DBMS that run on a desktop or laptop computer. Examples of desktop DBMS are Microsoft Access, FileMaker Pro, etc.

- Cloud DBMS: Are DBMS that run in the cloud and are accessible over the Internet. Examples of cloud DBMS are Amazon RDS, Microsoft Azure SQL Database, Google Cloud SQL, etc.

#DBMS Architecture.

We could also make a classification of DBMS according to the number of layers between the user and the database. There are three types of DBMS (Database Management System):

- **Single Layer DBMS**: there is only one layer between the user and the database. This layer provides an interface to the user to access the database. The user interacts with the database directly. The database is managed by a single program that provides an interface for the user to manipulate the data. Examples of single-layer DBMS include dBase, FileMaker, and FoxPro.

- **Two Layer DBMS**: there are two layers between the user and the database. The first layer is the user interface layer, which provides an interface to the user to access the database. The second layer is the database management layer, which manages the database and provides functions to the user interface layer.  Examples of two-layer DBMS include MySQL, PostgreSQL, Oracle, and SQL Server.

- **Three Layer DBMS**: there are three layers between the user and the database. The first layer is the user interface layer, which provides an interface to the user to access the database. The second layer is the application layer, which manages the application and provides functions to the user interface layer. The third layer is the database management layer, which manages the database and provides functions to the application layer. Examples of three-layer DBMS include IBM DB2, SAP Sybase, and Informix.