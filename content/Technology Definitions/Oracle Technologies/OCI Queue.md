#Integration #Technology #Oracle 
We’re excited to announce the upcoming release of a new serverless messaging service: [Oracle Cloud Infrastructure (OCI) Queue](https://www.oracle.com/cloud/cloud-native/queue/). Queue is currently in limited availability and is generally available soon. [Sign up to be notified](https://go.oracle.com/LP=131383?elqCampaignId=364417) when the service goes live.

OCI Queue is a fully managed, serverless message delivery service that automatically scales to meet your workload demand. OCI Queue helps to decouple your applications and build an asynchronous event-driven architecture.

## OCI Queue overview

OCI Queue is based on the following fundamental principles:

-   Application decoupling
    
-   Payload security
    
-   Technology and vendor agnostic interfaces
    

### Application decoupling

OCI Queue helps you to decouple applications and systems to build a modern cloud native or cloud-agnostic (micro)services-based architecture. Decoupling ensures that individual application components can scale independently and, as new application components are built, they can publish or subscribe to the appropriate queues.

![Queue - Application Decouple](https://blogs.oracle.com/content/published/api/v1.1/assets/CONTA1419D0C848845EBBDE7895AB4C21A91/Medium?cb=_cache_943b&format=jpg&channelToken=f7814d202b7d468686f50574164024ec)

### Payload security

The content of the queues is always protected. Queue messages are encrypted during transmission with TLS and the application of AES 128 encryption while the messages are being held at rest awaiting consumption. For customers who want more security, the service is built to enable the provider and consumer to further encrypt and decrypt the payload themselves. Connecting with OCI Queue also requires using one of OCI’s [authentication and authorization mechanisms](https://docs.oracle.com/en-us/iaas/Content/API/Concepts/sdk_authentication_methods.htm).

![Queue - Payload Security](https://blogs.oracle.com/content/published/api/v1.1/assets/CONT9D05AF1CF8154EB8B30461A11CC531D1/Medium?cb=_cache_943b&format=jpg&channelToken=f7814d202b7d468686f50574164024ec)

### Technology and vendor agnostic interfaces

OCI Queue allows you to communicate using a RESTful webservice with all its operations and payloads defined through an OpenAPI specification. But more powerful is the ability for OCI Queue to send and receive messages using the simple text oriented messaging protocol (STOMP).

STOMP is an open protocol designed for messaging that can boost efficiency because AuthN/Z is done once per connection instead of per request, as HTTP does. Any existing client supporting STOMP can connect OCI Queues by configuring the queue endpoint and authentication details.

## Customer benefits

### Fully managed and pay-per-use solution

OCI Queue provides the customer with an asynchronous messaging service that doesn’t need any infrastructure management, helping you to innovate more and focus on the wider design and implementation decisions.

OCI Queue’s pay-per-use model helps reduce administrative costs and the effort of provisioning and maintaining messaging infrastructures. OCI also manages the allocation of resources like servers and storage automatically with other housekeeping activities traditionally associated with deploying other messaging solutions from [WebLogic JMS](https://docs.oracle.com/cd/E13222_01/wls/docs103/jms/fund.html) to Kafka. OCI Queue’s pay-per-use model provides you with everything from monitoring, reporting, support, and maintenance.

![Queue - Fully Managed](https://blogs.oracle.com/content/published/api/v1.1/assets/CONT3E41897A929C44BFBA7D82996057911E/Medium?cb=_cache_943b&format=jpg&channelToken=f7814d202b7d468686f50574164024ec)

### Delivery assurance

OCI Queue protects against message delivery issues and ensures that messages are never lost, even if the consumer is unavailable.

OCI Queue provides dead letter queues (DLQs) by default so that if a message fails to reach its consumer after a configurable number of times, the message goes to a DLQ. You can then inspect the message in the DLQ and can redeliver it to the consumer after the reason for the delivery failure is addressed.

![Queue - Reliable Message Processing](https://blogs.oracle.com/content/published/api/v1.1/assets/CONT5435728DE90244AA9743F5574F453C9B/Medium?cb=_cache_943b&format=jpg&channelToken=f7814d202b7d468686f50574164024ec)

### Scale and performance to meet occasional high-volume events

With a fully managed service, you don’t need to worry about service availability or scaling the service up or down to meet demands. OCI monitors traffic for spikes and automatically adds resources based on demand, scaling the service and storage needs transparently and dynamically to accommodate the use case.

OCI Queue can also ingest significant volume of messages over a short period even if you have limited consumers and allows the messages to be processed as per the consumer availability and bandwidth.

![Queue - High Volume](https://blogs.oracle.com/content/published/api/v1.1/assets/CONT0D893F958E344E72888D89A55DF940EF/Medium?cb=_cache_943b&format=jpg&channelToken=f7814d202b7d468686f50574164024ec)

## How OCI Queue Works

The following diagram provides an example where a producer sends a message to a queue and two consumers attempt to process it.

![Queue - Message Flow](https://blogs.oracle.com/content/published/api/v1.1/assets/CONT0B76FB8C4E4144ADAD33348E3193EB73/Medium?cb=_cache_943b&format=jpg&channelToken=f7814d202b7d468686f50574164024ec)

1.  A producer sends a message to the queue with the default message retention time. The producer receives confirmation that the Queue service received and stored the message.
    
2.  Consumer A receives the message, which it is supposed to process within Visibility Timeout A.
    
3.  Consumer B receives nothing becuase the only available message was already consumed by Consumer A.
    
4.  Consumer A fails to process message within Visibility Timeout A, so it updates the message to extend the visibility timeout.
    
5.  Consumer B tries to receive a message again but can’t because the only available message was consumed and extended by Consumer A.
    
6.  The extended visibility timeout elapses and the message becomes visible again.
    
7.  Consumer B tries to receive a message a third time. Consumer B receives the message, which it’s supposed to process within Visibility Timeout B.
    
8.  Consumer A tries to receive the message but receives nothing because since Consumer B consumed the message. Consumer A can no longer extend the message’s visibility timeout or delete the message.
    
9.  Consumer B processes the message successfully and tries to delete the message from the queue. Consumer B receives confirmation that the message was permanently deleted, so it can’t be delivered to any other consumer.
    

## How to get started with OCI Queue

You can get started with Oracle Cloud Infrastructure today by [creating your free instance](http://www.oracle.com/cloud/free/), and don’t forget to [sign up to receive a notification](http://go.oracle.com/LP=131383?elqCampaignId=364417) when Queue is generally available soon!

For more information, see the following resources:

-   [OCI Queue product page](http://oracle.com/cloud/cloud-native/queue/)
    
-   [OCI APIs](https://docs.oracle.com/en-us/iaas/api/)
    
-   [OCI Cloud Native services](https://www.oracle.com/uk/cloud/cloud-native/)
    
