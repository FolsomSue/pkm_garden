-   [Cloud](https://www.oracle.com/cloud/)

## Queue

**A Serverless Messaging Service**

Oracle Cloud Infrastructure (OCI) Queue is a service for enabling asynchronous (decoupled) communication in a serverless manner. OCI Queue handles high-volume transactional data that requires independent processing without loss or duplication. The service uses open standards (STOMP and OpenAPI-defined REST) endpoints to communicate with any client.

![](https://www.oracle.com/a/ocom/img/yt-thumbnail-4rma-emjyfo.jpg)

OCI Queue Overview (12:04)

## Why OCI Queue?

-   ### Application decoupling
    
    OCI Queue enables the decoupling of services through asynchronous connectivity. This ensures that components can scale independently and designs can be future-proofed, so as new components are built, they can publish or subscribe to the queue transparently.
    
-   ### Reliable, fair message processing
    
    OCI Queue guarantees that a message is persistent until it's either deleted or expired. The service guarantees a message is delivered to the consumer application at least once. Messages can be consumed from a random channel within a queue to increase processing fairness and protect against “noisy” neighbors.
    
-   ### Autoscaling
    
    OCI Queue handles fluctuations in service demand transparently. This means OCI Queue can ingest any volume of messages over a short period of time (managing peak loads) and allow messages to be processed more slowly with a limited number of consumers.
    
-   ### Open standards
    
    OCI Queue is very easy and efficient to use because it supports open standards, including RESTful APIs (with an OpenAPI specification) and the industry-standard STOMP protocol.
    

## OCI Queue features

OCI Queue includes the following features:

-   **Scalability**—OCI Queue handles unexpected traffic spikes by automatically adding resources based on demand and distributing the workload to the available consumers.
-   **High throughput**—OCI Queue can support a nearly unlimited number of transactions per second per API action.
-   **At-least-once delivery**—A message is guaranteed to be delivered to the consumer at least once unless the message is either deleted or expires.
-   **Best-effort ordering**—Messages are delivered to the consumers in the same sequence they are received from the producers. But occasionally, messages might be delivered in a different order to avoid adding latency for order correction.
-   **Message locking**—A message is locked to avoid duplicate reads while a consumer processes it or until the visibility timeout period ends.
-   **Message batching**—Send, receive, update, or delete messages in batches of up to 20 messages to optimize cost.
-   **Delivery attempts and dead-letter queues**—You can define the number of attempts to deliver a message. If a message can't be consumed successfully, it can be sent to a dead-letter-queue (DLQ). DLQs let you isolate messages for troubleshooting.
-   **Messaging processing fairness**—Messages can be published and consumed from a random channel, thereby increasing fairness and protecting against sudden volume spikes.
-   **Message selection**—Messages can be delivered to consumers interested in receiving only certain types of messages or those coming from a specific producer.
-   **Ephemeral destinations**—Channels enable a request-reply messaging pattern by sending messages over short-lived, temporary channels under a queue. Channels are created on the fly without requiring explicit creation or deletion API calls.
-   **Encryption**—Messages are encrypted end to end.
-   **STOMP protocol**—STOMP is an open protocol designed for messaging that can boost efficiency as authentication and authorization are done once per connection rather than per HTTP request.
-   **REST APIs**—OCI Queue can be used with true REST APIs, supported with an OpenAPI specification.

![OCI Queue features diagram, description below](https://www.oracle.com/a/ocom/img/rc24full-oci-queue.png)

Enables Scaling : OCI Queue can enable scaling by having as many consumers as necessary reading from a queue. Enables Decoupling: The Queue client puts messages onto a queue defined for a particular purpose but remains unaware of who the consumer will be, where and how they are deployed. Enables Reliable Delivery: A queue consumer can't process a message from the queue, so rather than the message being lost it is placed into the Dead Letter Queue for remediation.