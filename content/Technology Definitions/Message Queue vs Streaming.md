#Integration #Technology #definition 
![Message Queue vs Streaming](https://blog.iron.io/wp-content/uploads/2021/06/jelleke-vanooteghem-t4PkYWVjD40-unsplash.jpg "jelleke-vanooteghem-t4PkYWVjD40-unsplash")

Message queues and streams have some subtle differences that can easily leave a developer scratching their head. While the differences may seem small at first, they're enough to give streams and queues very different use cases, when implemented in the most optimal manner.

## What Is a Message Queue?

A [message queue](https://blog.iron.io/right-on-queue-message-queues-made-simple/), sometimes called a [[point-to-point]] communication, is fairly straightforward. A message queue can have one or more consumers and/or producers. In a message queue with multiple consumers, the queue will attempt to distribute the messages evenly across them, with the guarantee being that every message will only be delivered once.

When all consumers are busy, the queue (or "broker") will store messages, making it a durable queue. To ensure the broker doesn't drop messages that haven't been delivered yet, the queue needs to persist. Durability and persistency are two important qualities to look for in a message queue.

## What Is Streaming?

A streaming broker is different from a message queue for many reasons. For starters, messages are organized into log files or topics. One or more consumers can subscribe to a log file or topic to receive all messages that come through that stream. With proper setup, a streaming broker will deliver the same message to every subscriber, in a specific order. This is often described as a [[publish-subscribe]] pattern.

Active subscribers will always get the message, but with this type of message broker, new subscribers can access the logs file and read messages from any point in time. This has its own set of benefits for many use cases.

## Message Queue vs Streaming: The Differences

While many consumers may be active, queues only deliver messages to a single consumer (typically whichever consumer is available to receive it first) before removing that message from the queue. Meanwhile, streaming brokers send the same message to every subscriber of that log file.

In a [queue](https://blog.iron.io/use-message-queue/), once a message is delivered, it's gone forever. To reprocess a message, you have to have a backup, like a batch layer, so that you can put it back into the queue. In comparison, a streaming broker uses a distributed log file, so consumers can move backward and forward within that file to re-process messages they've already received on command.

Examples of event streaming platforms include Apache Kafka, where streaming data is organized by Kafka topics. Kafka streams offer the same high throughput and high performance of message queues, but with different functionality.

As you can see, the primary difference between queues and streams is the means of message delivery. This seemingly subtle difference completely changes the landscape of use cases for each of these services.

## Pros and Cons of Message Queues

Message queues have an only-once delivery goal, which can be thought of as a back pressure mechanism if you're dealing with microservices. As such, message queues are [common for managing tasks](https://blog.iron.io/top-10-uses-for-message-queue/,%20https://blog.iron.io/use-message-queue/) and workloads where you only want each task processed once.

-   Message queues only deliver each message once, to a single consumer.
-   Message queues process on a first-come, first-serve basis.
-   Message queues may not deliver in the same order messages are queued.

Examples of message queues include RabbitMQ, ActiveMQ, and IronMQ.

## Pros and Cons of Stream Processing

A streaming broker acts as a distributed data store, which means you can use it as a single source of truth when working with data-centric environments that require real-time interactions. Let's say you need to expose a given message in many formats (such as graph, search, and so on). A message queue would make that impossible because a message can only be received once.

A streaming broker makes taking one message and producing multiple actions easy with the help of polyglot persistence. In other words, a streaming broker can deliver the same message to multiple consumers, with each consumer set up to do a different thing with that message. This is known as reactive programming, whereas a message queue is designed for imperative programming.

-   Streaming brokers can deliver the same message to many consumers without the need for replication.
-   Consumers can be set up to do different things with the same message.
-   Streaming brokers always deliver in the same order messages are queued.

![Message Queue vs Streaming](https://blog.iron.io/wp-content/uploads/2021/06/austin-distel-goFBjlQiZFU-unsplash.jpg "austin-distel-goFBjlQiZFU-unsplash")
