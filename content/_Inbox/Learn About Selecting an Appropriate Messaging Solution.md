-   [Skip to Content](https://docs.oracle.com/en/solutions/select-a-messaging-solution/index.html#maincontent)
-   [Skip to Search](https://docs.oracle.com/en/solutions/select-a-messaging-solution/index.html#skip_to_search_form)
-   [Home](https://docs.oracle.com/)

Learn about selecting an appropriate messaging solution

Try a different search query.

We are making updates to our Search system right now. Please try again later.

Learn about selecting an appropriate messaging solution

1.  [Learn about selecting an appropriate messaging solution](https://docs.oracle.com/en/solutions/select-a-messaging-solution/index.html)
2.  Learn About Selecting an Appropriate Messaging Solution

Learn about the evaluation factors for selecting an appropriate messaging solution that aligns with your business needs.

Oracle Cloud Infrastructure (OCI) provides you with a choice of technologies to support asynchronous brokered Interprocess Communication (IPC), such as microservice-to-microservice communication. Brokered services facilitate communication, so that the sender doesn't need to know about the consumer during deployment. The goal is to achieve lower levels of coupling for the client and consumer.

Different communication approaches offer different benefits. In this solution, you will learn about the different OCI services that you can use to enable brokered (and asynchronous) communication. You will consider orchestration because messaging is typically associated with choreography. You learn about the different considerations or factors that can impact product selection. For each factor, you learn how the service is impacted using a decision matrix. You can score the different factors against each service to identify the most appropriate service for your business needs. You will consider where the services can act as message sources or destinations using common and industry-standard protocols and their abstractions using brokered messaging. For example, brokered services such as HTTP/S (SOA, REST and so on) and JMS don't rely on consumer availability, location, and similar information.

### OCI Services that Enable IPC

You will consider the following OCI services that enable IPC:

-   Notifications
    
    The Oracle Cloud Infrastructure Notifications service broadcasts messages to distributed components through a publish-subscribe pattern, delivering secure, highly reliable, low latency, and durable messages for applications hosted on Oracle Cloud Infrastructure.
    
-   Integration
    
    Oracle Integration is a fully managed service that allows you to integrate your applications, automate processes, gain insight into your business processes, and create visual applications.
    
-   Queue
    
    Oracle Cloud Infrastructure Queue provides a scalable system to process messages while handling complex management tasks such as guaranteed at-least-once processing, tracking, and client isolation. This centralized service also manages message ordering and processing state, which allows stateless client processes to offload cursor tracking.
    
-   Streaming
    
    Oracle Cloud Infrastructure Streaming provides a fully managed, scalable, and durable storage solution for ingesting continuous, high-volume streams of data that you can consume and process in real time. You can use Streaming for ingesting high-volume data, such as application logs, operational telemetry, web click-stream data; or for other use cases where data is produced and processed continually and sequentially in a publish-subscribe messaging model.
    
-   Transactional Event Queues (TEQ) and Advanced Queuing (AQ)
    
    Transactional Event Queues (TEQ) and Advanced Queuing (AQ) are robust and feature-rich message queuing systems integrated with Oracle Database. Transactional Event Queues (TEQ) are a high performance partitioned in-memory implementation with multiple event streams per queue. Advanced Queuing (AQ) is suitable for simpler workflow use cases. These features leverage the Oracle Database to persist messages and provide high throughput and scalability.
    

### Excluded OCI Services

This solution excludes some OCI services for various reasons. The following list identifies those exclusions and the rationale:

-   Email: Intended for human consumption, but there are some rare legacy cases where email was used to deliver technical payloads with application clients.
-   Events: OCI generates messages for predefined events regardless of user permissions.
-   Event Hub: The Event Hub was deprecated in favor of Service Connector Hub.
-   Service Connector hub: Currently only supports Monitoring, Logging, and Streaming as sources and can't be called directly to broker message delivery. To use the Service Connector Hub, you must route a message through an OCI service it recognizes as a source, such as Streaming.
-   Oracle GoldenGate: Provides a means to broker the near real-time data movement. It enables data replication between different data sources and sinks rather than directly with clients. As a technology, it could be co-opted to support messaging processes, but currently, it doesn't directly offer interfacing mechanisms to support this.
-   Web Services (such as REST and SOAP): Use web services for implementation of such communication based on your application implementation strategies and whether you have configured networks to allow such traffic.
-   Oracle WebLogic Server: Provides a variety of technologies that can support IPC and messaging through the use of a JMS-compliant service. It is not provided as an OCI-native service, although the Oracle Cloud Marketplace provides various preconfigured images. Similarly, Oracle actively supports Java microprofile implementations in the form of Helidon and Micronaut, which support streaming API technologies such as GraphQL and gRPC.

Content on Oracle Architecture Center is published for your convenience. It is not part of the Product Documentation for any Oracle product or service.

Title and Copyright Information