---
aliases: (Advanced Queuing)
---
#Technology #definition #Integration #Oracle 
# Advanced Queuing (AQ)

## What Is Advanced Queuing?

When Web-based business applications communicate with each other, producer applications enqueue messages and consumer applications dequeue messages. Advanced Queuing provides database-integrated message queuing functionality. Advanced Queuing leverages the functions of the Oracle database so that messages can be stored persistently, propagated between queues on different machines and databases, and transmitted using Oracle Net Services, HTTP(S), and SMTP.

Since Oracle Advanced Queuing is implemented in database tables, all the operational benefits of high availability, scalability, and reliability are applicable to queue data. Standard database features such as recovery, restart, and security are supported in Advanced Queuing, and queue tables can be imported and exported. Refer to [Chapter 4, "Managing AQ"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qmanage.htm#58915) for more information. You can also use database development and management tools such as Oracle Enterprise Manager to monitor queues. Refer to ["Oracle Enterprise Manager Support"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qmanage.htm#64582)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qmanage.htm#64582).

### Advanced Queuing in Integrated Application Environments

Advanced Queuing provides the message management functionality and asynchronous communication needed for application integration. In an integrated environment, messages travel between the Oracle database server and the applications and users, as shown in [Figure 1-1](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#66090). Using Oracle Net Services, messages are exchanged between a client and the Oracle database server or between two Oracle databases. Oracle Net Services also propagates messages from one Oracle queue to another. Or, as shown in [Figure 1-1](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#66090), you can perform Advanced Queuing operations over the Internet using transport protocols such as HTTP, HTTPS, or SMTP. In this case, the client, a user or Internet application, produces structured XML messages. During propagation over the Internet, Oracle servers communicate using structured XML also. Refer to [Chapter 17, "Internet Access to Advanced Queuing"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintnet.htm#141421) for more information on Internet integration with Advanced Queuing.

Application integration also involves the integration of heterogeneous messaging systems. AQ seamlessly integrates with existing non-Oracle messaging systems like IBM MQSeries through Messaging Gateway, thus allowing existing MQSeries-based applications to be integrated into an Oracle AQ environment. Refer to [Chapter 18, "Messaging Gateway"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/mgw.htm#514690) for more information on AQ integration with non-Oracle messaging systems.

#### _Figure 1-1 Integrated Application Environment Using Advanced Queuing_

![Text description of adque437.gif follows](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/adque437.gif)[  
Text description of the illustration adque437.gif](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/img_text/adque437.htm)  
  

### Interfaces to Advanced Queuing

You can access Advanced Queuing functionality through the following interfaces:

-   PL/SQL using `DBMS_AQ`, `DBMS_AQADM,` `and` `DBMS_AQELM`. Refer to the _[Oracle9i Supplied PL/SQL Packages and Types Reference](https://docs.oracle.com/cd/B10500_01/appdev.920/a96612/toc.htm)_.
-   Visual Basic using Oracle Objects for OLE. Refer to the Online Help for Oracle Objects for OLE.
-   Java using the `oracle.AQ` Java package. Refer to the _[Oracle9i Supplied Java Packages Reference](https://docs.oracle.com/cd/B10500_01/appdev.920/a96609/toc.htm)_.
-   Java Message Service (JMS) using the `oracle.jms` Java package. Refer to the _[Oracle9i Supplied Java Packages Reference](https://docs.oracle.com/cd/B10500_01/appdev.920/a96609/toc.htm)_.
-   Internet access using HTTP, HTTPS, and SMTP

### Queuing System Requirements

Advanced Queuing meets queuing system requirements for performance, scalability, and persistence. Refer to [Chapter 5, "Performance and Scalability"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qperform.htm#59580) for more information.

#### Performance

Requests for service must be decoupled from supply of services to increase efficiency and provide the infrastructure for complex scheduling. Advanced Queuing exhibits high performance characteristics as measured by the following metrics:

-   Number of messages enqueued/dequeued per second
-   Time to evaluate a complex query on a message warehouse
-   Time to recover/restart the messaging process after a failure

#### Scalability

Queuing systems must be scalable. Advanced Queuing exhibits high performance as the number of programs using the application increases, as the number of messages increases, and as the size of the message warehouse increases.

#### Persistence for Security

Messages that constitute requests for service must be stored persistently, and processed exactly once, for deferred execution to work correctly in the presence of network, machine, and application failures. Advanced Queuing is able to meet requirements in the following situations:

-   Applications that do not have the resources to handle multiple unprocessed messages arriving simultaneously from external clients or from programs internal to the application.
-   Communication links between databases that are not available all the time or are reserved for other purposes. If the system falls short in its capacity to deal with these messages immediately, the application must be able to store the messages until they can be processed.
-   Eternal clients or internal programs that are not ready to receive messages that have been processed.

#### Persistence for Scheduling

Queuing systems need message persistence so they can deal with priorities: messages arriving later may be of higher priority than messages arriving earlier; messages arriving earlier may have to wait for messages arriving later before actions are executed; the same message may have to be accessed by different processes; and so on. Priorities also change. Messages in a specific queue can become more important, and so need to be processed with less delay or interference from messages in other queues. Similarly, messages sent to some destinations can have a higher priority than others.

#### Persistence for Accessing and Analyzing Metadata

Message persistence is needed to preserve message metadata, which can be as important as the payload data. For example, the time that a message is received or dispatched can be a crucial for business and legal reasons. With the persistence features of Advanced Queuing, you can analyze periods of greatest demand or evaluate the lag between receiving and completing an order.

## General Features of Advanced Queuing

The following general features are discussed:

-   [Point-to-Point and Publish-Subscribe Messaging](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#66632)
-   [Oracle Internet Directory](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#66938)
-   [Oracle Enterprise Manager Integration](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#67000)
-   [Message Format Transformation](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#68444)
-   [SQL Access](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#58772)
-   [Support for Statistics Views](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#67856)
-   [Structured Payloads](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#57425)
-   [Retention and Message History](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#62699)
-   [Tracking and Event Journals](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#67953)
-   [Queue-Level Access Control](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#62578)
-   [Nonpersistent Queues](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#57439)
-   [Support for Oracle9i Real Application Clusters](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#64877)
-   [XMLType Payloads](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#63874)
-   [Internet Integration and Internet Data Access Presentation](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#63876)

Refer to [Chapter 8, "A Sample Application Using AQ"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#83406) for a hypothetical scenario in which the messaging system for a hypothetical online bookseller, BooksOnLine, is described. Many features discussed here are exemplified in the BooksOnLine example.

### Point-to-Point and Publish-Subscribe Messaging

A combination of features allows publish-subscribe messaging between applications. These features include rule-based subscribers, message propagation, the listen feature, and notification capabilities.

Advanced Queuing sends and receives messages in the following ways:

-   Point-to-Point
-   Publish-Subscribe

#### Point-to-Point

A point-to-point message is aimed at a specific target. _S_enders and receivers decide on a common queue in which to exchange messages. Each message is consumed by only one receiver. [Figure 1-2](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#68496) shows that each application has its own message queue, known as a single-consumer queue**.**

#### _Figure 1-2 Point-to-Point Messaging_

![Text description of adque250.gif follows](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/adque250.gif)[  
Text description of the illustration adque250.gif](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/img_text/adque250.htm)  
  

#### Publish-Subscribe

A publish-subscribe message can be consumed by multiple receivers, as shown in [Figure 1-3](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#66841). Publish-subscribe messaging has a wide dissemination mode--broadcast--and a more narrowly aimed mode--multicast, also called point-to-multipoint.

Broadcasting is the equivalent of a radio station not knowing exactly who the audience is for a given program. The dequeuers are **subscribers** to **multiconsumer queues** In contrast, multicast is the same as a magazine publisher who knows who the subscribers are. Multicast is also referred to as point-to-multipoint because a single publisher sends messages to multiple receivers, called **recipients,** who may or may not be subscribers to the queues that serve as exchange mechanisms.

#### _Figure 1-3 Publish-Subscribe Mode_

![Text description of adque249.gif follows](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/adque249.gif)[  
Text description of the illustration adque249.gif](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/img_text/adque249.htm)  
  

### Oracle Internet Directory

Oracle Internet Directory is a native LDAPv3 directory service built on the Oracle database that centralizes a wide variety of information, including e-mail addresses, telephone numbers, passwords, security certificates, and configuration data for many types of networked devices. You can look up enterprise-wide queuing information--queues, subscriptions, and events--from one location, the Oracle Internet Directory. Refer to the _[Oracle Internet Directory Administrator's Guide](https://docs.oracle.com/cd/B10500_01/network.920/a96574/toc.htm)_ for more information.

### Oracle Enterprise Manager Integration

You can use Enterprise Manager to do the following:

-   Create and manage queues, queue tables, propagation schedules, and transformations
-   Monitor your AQ environment using the AQ topology at the databse and queue levels, and by viewing queue errors and queue and session statistics. Refer to ["Oracle Enterprise Manager Support"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qmanage.htm#64582)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qmanage.htm#64582).

### Message Format Transformation

The message format transformation feature supports applications that use data in different formats. A transformation defines a mapping from one Oracle data type to another. The transformation is represented by a SQL function that takes the source data type as input and returns an object of the target data type.

A transformation can be specified as follows:

-   During enqueue, to transform the message to the correct type before inserting it into the queue.
    
    You can convert a message to the payload type of the queue at enqueue time. Thus, the type of the message to be enqueued need not match the payload type of the queue.
    
-   During dequeue, to receive the message in the desired format
    
    A message can be transformed to the desired format before returning it to the dequeuer.
    
-   By a remote subscriber, who can choose to receive a message in a format different from the format of the source queue
    
    Before propagating the message to the remote subscriber, the message is transformed according to the transformation that the remote subscriber specified when subscribing to the queue.
    

As [Figure 1-4](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#67057) shows, queuing, routing, and transformation are essential building blocks to an integrated application architecture. The figure shows how data from the Out queue of a CRM application is routed and transformed in the integration hub and then propagated to the In queue of the Web application. The transformation engine maps the message from the format of the Out queue to the format of the In queue.

#### _Figure 1-4 Transformations in Application Integration_

![Text description of adque448.gif follows](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/adque448.gif)[  
Text description of the illustration adque448.gif](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/img_text/adque448.htm)  
  

Refer to ["Message Format Transformation"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#89776)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#89776) for more information.

### SQL Access

Messages are placed in normal rows in a database table, and so can be queried using standard SQL. This means that you can use SQL to access the message properties, the message history, and the payload. With SQL access you can also do auditing and tracking. All available SQL technology, such as indexes, can be used to optimize access to messages.

### Support for Statistics Views

Basic statistics about queues are available using the `GV$AQ` view.

### Structured Payloads

You can use object types to structure and manage message payloads. RDBMSs in general have a richer typing system than messaging systems. Since Oracle is an object-relational DBMS, it supports both traditional relational types as well as user-defined types. Many powerful features are enabled as a result of having strongly typed content, such as content whose format is defined by an external type system. These include:

-   Content-based routing: Advanced Queuing can examine the content and automatically route the message to another queue based on the content.
-   Content-based subscription: a publish and subscribe system is built on top of a messaging system so that you can create subscriptions based on content.
-   Querying: the ability to execute queries on the content of the message enables message warehousing.

To see this feature applied in the context of the BooksOnLine scenario, refer to ["Structured Payloads"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#89639) [](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#89639).

### Retention and Message History

The systems administrator specifies the retention duration to retain messages after consumption. Advanced Queuing stores information about the history of each message, preserving the queue and message properties of delay, expiration, and retention for messages destined for local or remote receivers. The information contains the enqueue and dequeue times and the identification of the transaction that executed each request. This allows users to keep a history of relevant messages. The history can be used for tracking, data warehouse, and data mining operations, as well as specific auditing functions.

To see this feature applied in the context of the `BooksOnLine` scenario, refer to [Retention and Message History](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#158007)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#158007).

### Tracking and Event Journals

If messages are retained, they can be related to each other. For example, if a message `m2` is produced as a result of the consumption of message `m1`, `m1` is related to `m2`. This allows users to track sequences of related messages. These sequences represent event journals, which are often constructed by applications. Advanced Queuing is designed to let applications create event journals automatically.

When an online order is placed, multiple messages are generated by the various applications involved in processing the order. Advanced Queuing offers features to track interrelated messages independent of the applications that generated them. You can determine who enqueued and dequeued messages, who the users are, and who did what operations.

With Advanced Queuing tracking features, you can use SQL `SELECT` and `JOIN` statements to get order information from `AQ$QUETABLENAME` and the views `ENQ_TRAN_ID`, `DEQ_TRAN_ID`, `USER_DATA` (the payload), `CORR_ID`, and `MSG_ID`. These views contain the following data used for tracking:

-   Transaction IDs--from `ENQ_TRAN_ID` and `DEQ_TRAN_ID`, captured during enqueuing and dequeuing.
-   Correlation IDs--from `CORR_ID`, part of the message properties
-   Message content that can be used for tracking--`USER_DATA`

### Queue-Level Access Control

The owner of an 8.1-style queue can grant or revoke queue-level privileges on the queue. Database administrators can grant or revoke new AQ system-level privileges to any database user. Database administrators can also make any database user an AQ administrator.

To see this feature applied in the context of the BooksOnLine scenario, refer to ["Queue-Level Access Control"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#157908)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#157908).

### Nonpersistent Queues

Advanced Queuing can deliver nonpersistent messages asynchronously to subscribers. These messages can be event-driven and do not persist beyond the failure of the system (or instance). Advanced Queuing supports persistent and nonpersistent messages with a common API.

To see this feature applied in the context of the BooksOnLine scenario, refer to ["Nonpersistent Queues"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#81450)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#81450).

### Support for Oracle9_i_ Real Application Clusters

An application can specify the instance affinity for a queue table. When Advanced Queuing is used with Real Application Clusters and multiple instances, this information is used to partition the queue tables between instances for queue-monitor scheduling. The queue table is monitored by the queue monitors of the instance specified by the user. If an instance affinity is not specified, the queue tables is arbitrarily partitioned among the available instances. There can be pinging between the application accessing the queue table and the queue monitor monitoring it. Specifying the instance affinity does not prevent the application from accessing the queue table and its queues from other instances.

This feature prevents pinging between queue monitors and Advanced Queuing propagation jobs running in different instances. If compatibility is set to Oracle8_i_, release 8.1.5 or higher, an instance affinity (primary and secondary) can be specified for a queue table. When Advanced Queuing is used with Real Application Clusters and multiple instances, this information is used to partition the queue tables between instances for queue-monitor scheduling as well as for propagation. At any time, the queue table is affiliated to one instance. In the absence of an explicitly specified affinity, any available instance is made the owner of the queue table. If the owner of the queue table is terminated, the secondary instance or some available instance takes over the ownership for the queue table.

To see this feature applied in the context of the BooksOnLine scenario, refer to ["Support for Oracle Real Application Clusters"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#73703)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#73703).

### XMLType Payloads

You can create queues that use the new opaque type, `XMLType.` These queues can be used to transmit and store messages that are XML documents. Using `XMLType`, you can do the following:

-   Store any type of message in a queue
-   Store `d`ocuments internally as CLOBs
-   Store `m`ore than one type of payload in a queue
-   Query XMLType columns using the operators `ExistsNode()` and `SchemaMatch()`
-   Specify the operators in subscriber rules or dequeue conditions

### Internet Integration and Internet Data Access Presentation

You can access AQ over the Internet by using Simple Object Access Protocol (SOAP). Internet Data Access Presentation (IDAP) is the SOAP specification for AQ operations. IDAP defines the XML message structure for the body of the SOAP request. An IDAP-structured message is transmitted over the Internet using transport protocols such as HTTP or SMTP. Refer to ["Propagation over the Internet: HTTP and SMTP"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#68209)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#68209) and [Chapter 17, "Internet Access to Advanced Queuing"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintnet.htm#141421) for more information.

#### Propagation over the Internet: HTTP and SMTP

[Figure 1-5](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#68224) shows the architecture for performing AQ operations over HTTP. The major components are:

-   The AQ client program
-   The Web server/ServletRunner hosting the AQ servlet
-   The Oracle database server

The AQ client program sends XML messages (conforming to IDAP) to the AQ servlet, which understands the XML message and performs AQ operations. Any HTTP client, for example Web browsers, can be used. The Web server/ServletRunner hosting the AQ servlet interprets the incoming XML messages. Examples include Apache/Jserv or Tomcat. The AQ servlet connects to the Oracle database server and performs operations on the users' queues.

#### _Figure 1-5 Architecture for Performing AQ Operations Using HTTP_

![Text description of adque430.gif follows](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/adque430.gif)[  
Text description of the illustration adque430.gif](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/img_text/adque430.htm)  
  

[Figure 1-6](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#68594) shows additional components in the architecture for sending AQ messages over SMTP:

-   E-mail server
-   LDAP server (Oracle Internet Directory)

The e-mail server verifies client signatures using certificates stored in LDAP and then routes the request to the AQ servlet.

#### _Figure 1-6 Architecture for Performing AQ Operations Using SMTP_

![Text description of adque431.gif follows](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/adque431.gif)[  
Text description of the illustration adque431.gif](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/img_text/adque431.htm)  
  

#### The Internet Data Access Presentation (IDAP)

The Internet Data Access Presentation (IDAP) uses the Content-Type of `text/xml` to specify the body of the SOAP request. XML provides the presentation for IDAP request and response messages as follows:

-   All request and response tags are scoped in the SOAP namespace.
-   AQ operations are scoped in the IDAP namespace.
-   The sender includes namespaces in IDAP elements and attributes in the SOAP body.
-   The receiver processes IDAP messages that have correct namespaces; for the requests with incorrect namespaces, the receiver returns an invalid request error.
-   The SOAP namespace has the value `http://schemas.xmlsoap.org/soap/envelope/`
-   The IDAP namespace has the value http://ns.oracle.com/AQ/schemas/access

Refer to [Chapter 17, "Internet Access to Advanced Queuing"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintnet.htm#141421) for more information about IDAP.

### Nonrepudiation and the AQ$<QueueTableName> View

Advanced Queuing maintains the entire history of information about a message along with the message itself. You can look up history information by using the `AQ$<QueueTableName>` view. This information serves as the proof of sending and receiving of messages and can be used for nonrepudiation of the sender and nonrepudiation of the receiver. Refer to [Chapter 10, "Administrative Interface: Views"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qadfacev.htm#3136) for more information about the `AQ$<QueueTableName>` view.

The following information is kept at enqueue for nonrepudiation of the enqueuer:

-   AQ agent doing the enqueue
-   Database user doing the enqueue
-   Enqueue time
-   Transaction ID of the transaction doing the enqueue

The following information is kept at dequeue for nonrepudiation of the dequeuer:

-   AQ agent doing dequeue
-   Database user doing dequeue
-   Dequeue time
-   Transaction ID of the transaction doing dequeue

After propagation, the `Original_Msgid` field in the destination queue of propagation corresponds to the message ID of the source message. This field can be used to correlate the propagated messages. This is useful for nonrepudiation of the dequeuer of propagated messages.

Stronger nonrepudiation can be achieved by enqueuing the digital signature of the sender at the time of enqueue with the message and by storing the digital signature of the dequeuer at the time of dequeue.

## Enqueue Features

The following features apply to enqueuing messages.

### Correlation Identifiers

Users can assign an identifier to each message, thus providing a means to retrieve specific messages at a later time.

### Subscription and Recipient Lists

A single message can be designed to be consumed by multiple consumers. A queue administrator can specify the list of subscribers who can retrieve messages from a queue. Different queues can have different subscribers, and a consumer program can be a subscriber to more than one queue. Further, specific messages in a queue can be directed toward specific recipients who may or may not be subscribers to the queue, thereby overriding the subscriber list.

You can design a single message for consumption by multiple consumers in a number of different ways. The consumers who are allowed to retrieve the message are specified as explicit recipients of the message by the user or application that enqueues the message. Every explicit recipient is an agent identified by name, address, and protocol.

A queue administrator may also specify a default list of recipients who can retrieve all the messages from a specific queue. These implicit recipients become subscribers to the queue by being specified in the default list. If a message is enqueued without specifying any explicit recipients, the message is delivered to all the designated subscribers.

A rule-based subscriber is one that has a rule associated with it in the default recipient list. A rule-based subscriber will be sent a message with no explicit recipients specified only if the associated rule evaluated to TRUE for the message. Different queues can have different subscribers, and the same recipient can be a subscriber to more than one queue. Further, specific messages in a queue can be directed toward specific recipients who may or may not be subscribers to the queue, thereby overriding the subscriber list.

A recipient may be specified only by its name, in which case the recipient must dequeue the message from the queue in which the message was enqueued. It may be specified by its name and an address with a protocol value of 0. The address should be the name of another queue in the same database or another Oracle database (identified by the database link), in which case the message is propagated to the specified queue and can be dequeued by a consumer with the specified name. If the recipient's name is NULL, the message is propagated to the specified queue in the address and can be dequeued by the subscribers of the queue specified in the address. If the protocol field is nonzero, the name and address are not interpreted by the system and the message can be dequeued by a special consumer. To see this feature applied in the context of the BooksOnLine scenario, refer to ["Elements of Advanced Queuing"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#64906)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#64906).

### Priority and Ordering of Messages in Enqueuing

It is possible to specify the priority of the enqueued message. An enqueued message can also have its exact position in the queue specified. This means that users have three options to specify the order in which messages are consumed: (a) a sort order specifies which properties are used to order all message in a queue; (b) a priority can be assigned to each message; (c) a sequence deviation allows you to position a message in relation to other messages. Further, if several consumers act on the same queue, a consumer will get the first message that is available for immediate consumption. A message that is in the process of being consumed by another consumer will be skipped.

To see this feature applied in the context of the BooksOnLine scenario, refer to ["Priority and Ordering of Messages"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#64828)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#64828).

### Message Grouping

Messages belonging to one queue can be grouped to form a set that can only be consumed by one user at a time. This requires that the queue be created in a queue table that is enabled for message grouping. All messages belonging to a group have to be created in the same transaction and all messages created in one transaction belong to the same group. This feature allows users to segment complex messages into simple messages; for example, messages directed to a queue containing invoices can be constructed as a group of messages starting with the header message, followed by messages representing details, followed by the trailer message.

To see this feature applied in the context of the BooksOnLine scenario, refer to ["Message Grouping"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#81528)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#81528).

### Propagation

This feature enables applications to communicate with each other without having to be connected to the same database or the same queue. Messages can be propagated from one Oracle AQ to another, irrespective of whether the queues are local or remote. Propagation is done using database links and Oracle Net Services.

To see this feature applied in the context of the BooksOnLine scenario, refer to ["Propagation"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#75698)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#75698).

### Sender Identification

Applications can mark the messages they send with a custom identification. Oracle also automatically identifies the queue from which a message was dequeued. This allows applications to track the pathway of a propagated message or a string messages within the same database.

### Time Specification and Scheduling

Delay interval or expiration intervals can be specified for an enqueued message, thereby providing windows of execution. A message can be marked as available for processing only after a specified time elapses (a delay time) and has to be consumed before a specified time limit expires.

### Rule-Based Subscribers

A message can be delivered to multiple recipients based on message properties or message content. Users define a rule-based subscription for a given queue as the mechanism to specify interest in receiving messages of interest. Rules can be specified based on message properties and message data (for object and raw payloads). Subscriber rules are then used to evaluate recipients for message delivery.

To see this feature applied in the context of the BooksOnLine scenario, refer to ["Rule-Based Subscription"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#81551)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#81551).

### Asynchronous Notification

The asynchronous notification feature allows clients to receive notification of a message of interest. The client can use it to monitor multiple subscriptions. The client does not have to be connected to the database to receive notifications regarding its subscriptions.

Clients can use the OCI function, `LNOCISubcriptionRegister`, or the PL/SQL procedure DBMS_AQ.REGISTER to register interest in messages in a queue. Refer to ["Registering for Notification"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qopface.htm#64124) in [Chapter 11, "Operational Interface: Basic Operations"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qopface.htm#57806) for more information.

To see this feature applied in the context of the BooksOnLine scenario, refer to ["Asynchronous Notifications"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#86109)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#86109).

## Dequeue Features

The following features apply to dequeuing messages.

### Recipients

A message can be retrieved by multiple recipients without the need for multiple copies of the same message. To see this feature applied in the context of the BooksOnLine scenario, refer to ["Multiple Recipients"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#65610)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#65610).

Designated recipients can be located locally or at remote sites. To see this feature applied in the context of the BooksOnLine scenario, refer to ["Local and Remote Recipients"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#65696)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#65696).

### Navigation of Messages in Dequeuing

Users have several options to select a message from a queue. They can select the first message or once they have selected a message and established a position, they can retrieve the next. The selection is influenced by the ordering or can be limited by specifying a correlation identifier. Users can also retrieve a specific message using the message identifier.

To see this feature applied in the context of the BooksOnLine scenario, refer to ["Message Navigation in Dequeue"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#65717)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#65717).

### Modes of Dequeuing

A DEQUEUE request can either browse or remove a message. If a message is browsed, it remains available for further processing. If a message is removed, it is not available more for DEQUEUE requests. Depending on the queue properties, a removed message may be retained in the queue table.

To see this feature applied in the context of the BooksOnLine scenario, refer to ["Modes of Dequeuing"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#65833)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#65833).

### Optimization of Waiting for the Arrival of Messages

A DEQUEUE can be issued against an empty queue. To avoid polling for the arrival of a new message, a user can specify if and for how long the request is allowed to wait for the arrival of a message.

To see this feature applied in the context of the BooksOnLine scenario, refer to ["Optimization of Waiting for Arrival of Messages"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#81535)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#81535).

### Retries with Delays

A message must be consumed exactly once. If an attempt to dequeue a message fails and the transaction is rolled back, the message will be made available for reprocessing after some user-specified delay elapses. Reprocessing will be attempted up to the user-specified limit.

To see this feature applied in the context of the BooksOnLine scenario, refer to ["Retry with Delay Interval"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#81428)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#81428).

### Optional Transaction Protection

ENQUEUE and `DEQUEUE` requests are normally part of a transaction that contains the requests, thereby providing the desired transactional behavior. You can, however, specify that a specific request is a transaction by itself, making the result of that request immediately visible to other transactions. This means that messages can be made visible to the external world as soon as the ENQUEUE or DEQUEUE statement is issued or after the transaction is committed.

### Exception Handling

A message may not be consumed within given constraints, such as within the window of execution or within the limits of the retries. If such a condition arises, the message will be moved to a user-specified exception queue.

To see this feature applied in the context of the BooksOnLine scenario, refer to ["Exception Handling"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#81498)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#81498).

### Listen Capability (Wait on Multiple Queues)

The listen call is a blocking call that can be used to wait for messages on multiple queues. It can be used by a gateway application to monitor a set of queues. An application can also use it to wait for messages on a list of subscriptions. If the listen returns successfully, a dequeue must be used to retrieve the message.

To see this feature applied in the context of the BooksOnLine scenario, refer to ["Listen Capability"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#93697)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#93697).

### Dequeue Message Header with No Payload

The dequeue mode REMOVE_NODATA can be used to remove a message from a queue without retrieving the payload. Use this mode to delete a message with a large payload whose content is irrelevant.

## Propagation Features

The following features apply to propagating messages. Refer to ["Internet Integration and Internet Data Access Presentation"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#63876)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#63876) for information on propagation over the Internet.

### Automated Coordination of Enqueuing and Dequeuing

Recipients can be local or remote. Because Oracle does not support distributed object types, remote enqueuing or dequeuing using a standard database link does not work. However, you can use AQ message propagation to enqueue to a remote queue. For example, you can connect to database X and enqueue the message in a queue, `DROPBOX`, located in database X. You can configure AQ so that all messages enqueued in `DROPBOX` will be automatically propagated to another queue in database Y, regardless of whether database Y is local or remote. AQ will automatically check if the type of the remote queue in database Y is structurally equivalent to the type of the local queue in database X and propagate the message.

Recipients of propagated messages can be applications or queues. If the recipient is a queue, the actual recipients are determined by the subscription list associated with the recipient queue. If the queues are remote, messages are propagated using the specified database link. Only AQ-to-AQ message propagation is supported.

### Propagation of Messages with LOBs

Propagation handles payloads with `LOB` attributes. To see this feature applied in the context of the BooksOnLine scenario, refer to ["Propagation of Messages with LOB Attributes"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#80847)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#80847).

### Propagation Scheduling

Messages can be scheduled to propagate from a queue to local or remote destinations. Administrators can specify the start time, the propagation window, and a function to determine the next propagation window (for periodic schedules).

### Enhanced Propagation Scheduling Capabilities

Detailed run-time information about propagation is gathered and stored in the `DBA_QUEUE_SCHEDULES` view for each propagation schedule. This information can be used by queue designers and administrators to fix problems or tune performance. For example, available statistics about the total and average number of message/bytes propagated can be used to tune schedules. Similarly, errors reported by the view can be used to diagnose and fix problems. The view also describes additional information such as the session ID of the session handling the propagation, and the process name of the job queue process handling the propagation.

To see this feature applied in the context of the BooksOnLine scenario, refer to ["Enhanced Propagation Scheduling Capabilities"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#81444)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qsample.htm#81444).

### Third-Party Support

AQ allows messages to be enqueued in queues that can then be propagated to different messaging systems by third-party propagators. If the protocol number for a recipient is in the range 128 - 255, the address of the recipient is not interpreted by AQ and so the message is not propagated by the AQ system. Instead, a third-party propagator can then dequeue the message by specifying a reserved consumer name in the dequeue operation. The reserved consumer names are of the form `AQ$_P#,` where # is the protocol number in the range 128-255. For example, the consumer name `AQ$_P128` can be used to dequeue messages for recipients with protocol number 128. The list of recipients for a message with the specific protocol number is returned in the `recipient_list` message property on dequeue.

Another way for Advanced Queuing to propagate messages to and from third-party messaging systems is through Messaging Gateway, an Enterprise Edition feature of Advanced Queuing. Messaging Gateway dequeues messages from an AQ queue and guarantees delivery to a third-party messaging system like MQSeries. Messaging Gateway can also dequeue messages from third-party messaging systems and enqueue them to an AQ queue. Refer to [Chapter 18, "Messaging Gateway"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/mgw.htm#514690) for more information.

## Elements of Advanced Queuing

By integrating transaction processing with queuing technology, persistent messaging in the form of Advanced Queuing is possible. This section defines a number of Advanced Queuing terms.

### Message

A message is the smallest unit of information inserted into and retrieved from a queue. A message consists of the following:

-   Control information (metadata)
-   Payload (data)

The control information represents message properties used by AQ to manage messages. The payload data is the information stored in the queue and is transparent to Oracle AQ. A message can reside in only one queue. A message is created by the enqueue call and consumed by the dequeue call.

### Queue

A queue is a repository for messages. There are two types of queues: user queues, also known as normal queues, and exception queues. The user queue is for normal message processing. Messages are transferred to an exception queue if they cannot be retrieved and processed for some reason. Queues can be created, altered, started, stopped, and dropped by using the Oracle AQ administrative interfaces. Refer to [Chapter 9, "Administrative Interface"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qadface.htm#58915) for more information.

User queues can be persistent (the default) or nonpersistent queues. Persistent queues store messages in database tables. These queues provide all the reliability and availability features of database tables. Nonpersistent queues store messages in memory. They are generally used to provide an asynchronous mechanism to send notifications to all users that are currently connected.

### Queue Table

Queues are stored in queue tables. Each queue table is a database table and contains one or more queues. Each queue table contains a default exception queue. [Figure 7-1, "Basic Queues"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qmodel.htm#78159)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qmodel.htm#78159) shows the relationship between messages, queues, and queue tables.

### Agent

An agent is a queue user. This can be an end user or an application. There are two types of agents:

-   Producers who place messages in a queue (enqueuing)
-   Consumers who retrieve messages (dequeuing)

Any number of producers and consumers may be accessing the queue at a given time. Agents insert messages into a queue and retrieve messages from the queue by using the Oracle AQ operational interfaces. Refer to [Chapter 11, "Operational Interface: Basic Operations"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qopface.htm#57806) for more information.

An agent is identified by its `name`, `address` and `protocol.` Refer to ["Agent Type (aq$_agent)"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qbascmpt.htm#77328)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qbascmpt.htm#77328) in [Chapter 2, "Basic Components"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qbascmpt.htm#78084) for a formal description of this data structure.

-   The name of the agent may be the name of the application or a name assigned by the application. A queue may itself be an agent--enqueuing or dequeuing from another queue.
-   The address field is a character field of up to 1024 bytes that is interpreted in the context of the protocol. For instance, the default value for the protocol is 0, signifying a database link addressing. In this case, the address for this protocol is of the form
    
    `queue_name@dblink`
     
    
    where `queue_name` is of the form `[schema.]queue` and `dblink` may either be a fully qualified database link name or the database link name without the domain name.
    

### Recipient

The recipient of a message may be specified by its name only, in which case the recipient must dequeue the message from the queue in which the message was enqueued. The recipient may be specified by name and an address with a protocol value of 0. The address should be the name of another queue in the same database or another Oracle database (identified by the database link) in which case the message is propagated to the specified queue and can be dequeued by a consumer with the specified name. If the recipient's name is `NULL`, the message is propagated to the specified queue in the address and can be dequeued by the subscribers of the queue specified in the address. If the protocol field is nonzero, the name and address are not interpreted by the system and the message can be dequeued by a special consumer (refer to ["Third-Party Support"](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#57509)[](https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm#57509)).

### Recipient and Subscription Lists

Multiple consumers can consume a single message:

-   The enqueuer can explicitly specify the consumers who may retrieve the message as recipients of the message. A recipient is an agent identified by a name, address, and protocol.
-   A queue administrator can specify a default list of recipients who can retrieve messages from a queue. The recipients specified in the default list are known as subscribers. If a message is enqueued without specifying the recipients, the message is sent to all the subscribers.

Different queues can have different subscribers, and the same recipient can be a subscriber to more than one queue. Further, specific messages in a queue can be directed toward specific recipients who may or may not be subscribers to the queue, thereby overriding the subscriber list.

### Rule

A rule is used to define one or more subscribers' interest in subscribing to messages that conform to that rule. The messages that meet the rule criterion are delivered to the interested subscribers. A rule is specified as a boolean expression (one that evaluates to true or false) using syntax similar to the `WHERE` clause of a SQL query. The boolean expression can include conditions on the following:

-   Message properties (currently priority and correlation identifier)
-   User data properties (object payloads only)
-   Functions (as specified in the `WHERE` clause of a SQL query)

### Rule-Based Subscribers

A rule-based subscriber is a subscriber with associated rules in the default recipient list. If an associated rule evaluates to `TRUE` for a message, the message is sent to the rule-based subscriber even if the message has no specified recipients.

### Transformation

A transformation defines a mapping from one Oracle data type to another. The transformation is represented by a SQL function that takes the source data type as input and returns an object of the target data type. A transformation can be specified during enqueue, to transform the message to the correct type before inserting it into the queue. It can be specified during dequeue to receive the message in the desired format. If specified with a remote subscriber, the message will be transformed before propagating it to the destination queue.

### Queue Monitor

The queue monitor (QMNn) is a background process that monitors messages in queues. It provides the mechanism for message delay, expiration, and retry delay. The QMNn also performs garbage collection for the queue table and its indexes and index-organized tables (IOTs). For example, the QMNn determines when all subscribers of multiconsumer queues have received a message and subsequently removes the message from the queue table and supporting indexes and IOTs.

You can start a maximum of 10 multiple queue monitors at the same time. You start the queue monitors by setting the dynamic `init.ora` parameter `aq_tm_processes`. The queue monitor wakes up every minute, or whenever there is work to do, for instance, if a message is marked expired or ready to be processed.

## Java Message Service Terminology

When using the `oracle.jms` Java package, keep in mind the following:

-   The JMS equivalent of enqueue is **send**.
-   The destination of messages is a **queue**, without any qualification.
-   The container of messages is a **topic**, and each application can **publish** on or **subscribe** to a given topic.
-   **Topic** in JMS maps to a **multiconsumer queue** in the other AQ interfaces.
-   The Java package `oracle.jms` has classes and interfaces to implement Oracle extensions to the public JMS standard.
## Reference
- https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm