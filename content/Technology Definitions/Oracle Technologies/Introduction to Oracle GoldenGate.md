#Oracle #definition #Replication #CDC #Change_Data_Capture 

Learn aboutOracle GoldenGate concepts, why and when should you use it, and get familiar with some of the basic terminology and keywords associated with Oracle GoldenGate.

Topics:

-   [What is Oracle GoldenGate?](https://docs.oracle.com/goldengate/c1230/gg-winux/GGCON/introduction-oracle-goldengate.htm#GUID-D7F54B8E-BA10-4778-AA1D-886B3EC7DBAD)  
    Oracle GoldenGate is a software product that allows you to replicate, filter, and transform data from one database to another database.
-   [Why Do You Need Oracle GoldenGate?](https://docs.oracle.com/goldengate/c1230/gg-winux/GGCON/introduction-oracle-goldengate.htm#GUID-68DD858A-1085-406C-A171-37AFFD885AEC)  
    Enterprise data is typically distributed across the enterprise in heterogeneous databases. To get data between different data sources, you can use Oracle GoldenGate to load, distribute, and filter transactions within your enterprise in real-time and enable migrations between different databases in near zero-downtime.
-   [When Do You Use Oracle GoldenGate?](https://docs.oracle.com/goldengate/c1230/gg-winux/GGCON/introduction-oracle-goldengate.htm#GUID-FC1D8354-3844-4FE0-B71E-9F5AF8322728)  
    Oracle GoldenGate meets almost any data movement requirements you might have. Some of the most common use cases are described in this section.
-   [How Do You Use Oracle GoldenGate?](https://docs.oracle.com/goldengate/c1230/gg-winux/GGCON/introduction-oracle-goldengate.htm#GUID-9EF27F3E-984B-4798-9236-2A51CD8C145A)  
    After installation, Oracle GoldenGate can be configured to meet your organization's business needs.
-   [Oracle GoldenGate Product Family](https://docs.oracle.com/goldengate/c1230/gg-winux/GGCON/introduction-oracle-goldengate.htm#GUID-794696C5-9241-42A2-88C4-2EB54F237AF4)  
    There are numerous products in the Oracle GoldenGate product family.

## 1.1 What is Oracle GoldenGate?

Oracle GoldenGate is a software product that allows you to replicate, filter, and transform data from one database to another database.

Using Oracle GoldenGate, you can move committed transactions across multiple heterogeneous systems in your enterprise. Oracle GoldenGate enables you to replicate data between Oracle databases to other supported heterogeneous database, and between heterogeneous databases. In addition, you can replicate to Java Messaging Queues, Flat Files, and to Big Data targets in combination with Oracle GoldenGate for Big Data.

## 1.2 Why Do You Need Oracle GoldenGate?

Enterprise data is typically distributed across the enterprise in heterogeneous databases. To get data between different data sources, you can use Oracle GoldenGate to load, distribute, and filter transactions within your enterprise in real-time and enable migrations between different databases in near zero-downtime.

To do this, you need a means to effectively move data from one system to another in real-time and with zero-downtime. Oracle GoldenGate is Oracle’s solution to replicate and integrate data.

Oracle GoldenGate has the following key features:

-   Data movement is in real-time, reducing latency.
    
-   Only committed transactions are moved, enabling consistency and improving performance.
    
-   Different versions and releases of Oracle Database are supported along with a wide range of heterogeneous databases running on a variety of operating systems. You can replicate data from an Oracle Database to a different heterogeneous database.
    
-   Simple architecture and easy configuration.
    
-   High performance with minimal overhead on the underlying databases and infrastructure.
    

## 1.3 When Do You Use Oracle GoldenGate?

Oracle GoldenGate meets almost any data movement requirements you might have. Some of the most common use cases are described in this section.

You can use Oracle GoldenGate to meet the following business requirements:

Business Continuity and High Availability

Business Continuity is the ability of an enterprise to provide its functions and services without any lapse in its operations. High Availability is the highest possible level of fault tolerance. To achieve business continuity, systems are designed with multiple servers, multiple storage, and multiple data centers to provide high enough availability to support the true continuity of the business. To establish and maintain such an environment, data needs to be moved between these multiple servers and data centers, which is easily done using Oracle GoldenGate.

Consider a scenario where you are working in a multinational bank that has its headquarters in London, UK. You work in one of the banks’ branches in Bangalore, India. This bank uses a specific account for its financial application that is used globally at all the branches. You have been asked by your manager to daily synchronize the transactions that have happened for this account in the database in the Bangalore branch with the centralized database situated at the UK. The volume of transactions is massive, and even the slightest delay can greatly impact the business. This same process is required at multiple destinations for every database in all the branches of the bank worldwide. This process has to be monitored continuously, preferably through some sort of GUI-based tool for the ease of management. Additionally, the bank has several other, non-critical applications used at all the branches. These applications are based on heterogeneous databases, such as MySQL, but the transactions done over these databases also must be loaded into an Oracle Database located at the headquarters. The replication technology used must support both Oracle and heterogeneous databases so that they can talk to each other. Oracle GoldenGate is an apt solution in such a scenario.

Initial Load and Database Migration

Initial load is a process of extracting data records from a source database and loading those records onto a target database. Initial load is a data migration process that is performed only once. Oracle GoldenGate allows you to perform initial load data migrations without taking your systems offline.

Data Integration

Data integration involves combining data from several disparate sources, which are stored using various technologies, and provide a unified view of the data. Oracle GoldenGate provides real-time data integration.

## 1.4 How Do You Use Oracle GoldenGate?

After installation, Oracle GoldenGate can be configured to meet your organization's business needs.

There are many different architectures that can be configured; which range from a simple uni-directional architecture to the more complex peer-to-peer. No matter the architecture, Oracle GoldenGate provides similarities between them, making administration easier.

Figure 1-1 Oracle GoldenGate Supported Topologies

![The image shows the six supported types of Oracle GoldenGate data replication.](https://docs.oracle.com/goldengate/c1230/gg-winux/GGCON/img/configurations.png "The image shows the six supported types of Oracle GoldenGate data replication.")

For full information about processing methodology, supported topologies and functionality, and configuration requirements, see the Oracle GoldenGate documentation for your database.

## 1.5 Oracle GoldenGate Product Family

There are numerous products in the Oracle GoldenGate product family.

-   Oracle GoldenGate Veridata : Oracle GoldenGate Veridata compares one set of data to another and identifies data that is out-of-sync, and allows you to repair any data that is found out-of-sync.
    
-   Oracle GoldenGate Plug-in for EMCC: The Enterprise Manager Plug-in for Oracle GoldenGate extends the Oracle Enterprise Manager Cloud Control and provides visual support for monitoring and managing Oracle GoldenGateprocesses.
    
-   Oracle GoldenGate Monitor: Oracle GoldenGate Monitor is a real-time, Web-based monitoring console that delivers an at-a-glance, graphical view of all of the Oracle GoldenGate instances and their associated databases within your enterprise.
    
-   Oracle GoldenGate for Big Data: Oracle GoldenGate for Big Data contains built-in support to write operation data from Oracle GoldenGate trail records into various Big Data targets (such as, HDFS, HBase, Kafka, Flume, JDBC, Cassandra, and MongoDB).
    
-   Oracle GoldenGate Application Adapters: Oracle GoldenGate Application Adapters integrate with installations of the Oracle GoldenGatecore product to bring in Java Message Service (JMS) information or to deliver information as JMS messages or files.
    
-   Oracle GoldenGate for HP NonStop (Guardian): Oracle GoldenGate for HP NonStop enables you to manage business data at a transactional level by extracting and replicating selected data records and transactional changes across a variety of heterogeneous applications and platforms.
    
-   Oracle GoldenGate Studio: Oracle GoldenGate Studio enables you to design and deploy high-volume, real-time replication by automatically handling table and column mappings, allowing drag and drop custom mappings, generating best practice configurations from templates, and contains context sensitive help.