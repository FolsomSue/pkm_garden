#Technology #definition #Event-Driven #HA_DR #High-Availability 

# Disaster Recovery with Kafka (Event Broker) Across the Edge and Hybrid Cloud
I spoke at [QCon London](https://qconlondon.com/) in April 2022 about building **disaster recovery and resilient real-time enterprise architectures with Apache Kafka**. This blog post summarizes the use cases, architectures, and real-world examples. The slide deck and video recording of the presentation is included as well.

![](https://www.kai-waehner.de/wp-content/uploads/2022/04/Disaster-Recovery-and-Resiliency-with-Apache-Kafka-Data-Streaming.png)

## What is QCon?

QCon is a **leading software development conference** held across the globe for 16 years. It provides a realistic look at what is trending in tech. The QCon events are organized by [InfoQ](https://www.infoq.com/), a well-known website for professional software development with over two million unique visitors per month.

QCon in 2022 uncovers **emerging software trends and practices**. Developers and architects learn how to solve complex engineering challenges **without the product pitches**.

**There is no Call for Papers (CfP) for QCon. The organizers invite trusted speakers** to talk about trends, best practices, and real-world stories. This makes QCon so strong and respected in the software development community.

![QCon London 2022](https://www.kai-waehner.de/wp-content/uploads/2022/04/IMG_0182-1024x768.jpg)

## Disaster Recovery and Resiliency with Apache Kafka

[Apache Kafka is the de facto data streaming](https://www.kai-waehner.de/blog/2021/05/09/kafka-api-de-facto-standard-event-streaming-like-amazon-s3-object-storage/) platform for [analytical AND transactional workloads](https://www.kai-waehner.de/blog/2022/03/09/analytics-vs-transactions-api-data-streaming-with-apache-kafka/). Multiple options exist to design Kafka for resilient applications. For instance, **MirrorMaker 2 and Confluent Replicator enable uni- or bi-directional real-time replication between independent Kafka clusters** in different data centers or clouds.

**Cluster Linking is a more advanced and straightforward option** from Confluent leveraging the native Kafka protocol instead of additional infrastructure and complexity using Kafka Connect (like MirrorMaker 2 and Replicator).

**Stretching a single Kafka cluster across multiple regions is the best option to guarantee no downtime and seamless failover in the case of a disaster**. However, it is hard to operate and only recommended (i.e., consistent, stable, and mission-critical) across distances with enhanced add-ons to open-source Kafka:

![Disaster Recovery and Resiliency across Multi Region with Apache Kafka](https://www.kai-waehner.de/wp-content/uploads/2022/04/Disaster-Recovery-and-Resiliency-across-Multi-Region-with-Apache-Kafka.png)

## QCon Presentation: Disaster Recovery with Apache Kafka

In my QCon talk, I intentionally showed the broad spectrum of **real-world success stories across industries** for **data streaming with Apache Kafka** from companies such as BMW, JPMorgan Chase, Robinhood, Royal Caribbean, and Devon Energy.

Best practices explored **how to build resilient enterprises architecture with disaster recovery** with RPO (Recovery Point Object) and RTO (Recovery Time Objective) in mind. The audience learns how to **get your SLAs and requirements for downtime and data loss right**.

The examples looked at **serverless cloud** offerings integrating to the IoT edge, **hybrid** retail architectures, and the **disconnected edge** in military scenarios.

The agenda looks like this:

1.  Resilient enterprise architectures
2.  Real-time data streaming with the Apache Kafka ecosystem
3.  Cloud-first and serverless Industrial IoT in automotive
4.  Multi-region infrastructure for core banking
5.  Hybrid cloud for customer experiences in retail
6.  Disconnected edge for safety and security in the public sector

#### Slide Deck from QCon Talk:

Here is the slide deck of my presentation from QCon London 2022:

We also had a great panel that discussed lessons learned from building resilient applications on the code and infrastructure level, plus the organizational challenges and best practices:

![QCon Panel about Resilient Architectures](https://www.kai-waehner.de/wp-content/uploads/2022/04/Screenshot-2022-04-06-at-10.17.22.png)

#### Video Recording from QCon Talk:

With the risk of Covid in mind, InfoQ decided not to record QCon sessions live.

![Kai Waehner speaking at QCon London April 2022 about Resiliency with Apache Kafka](https://www.kai-waehner.de/wp-content/uploads/2022/04/QCon-London-April-2022-1-1024x768.jpeg)

Instead, a pre-recorded video had to be submitted by the speakers. The video recording is already available for QCon attendees (no matter if on-site in London or at the QCon Plus virtual event):

[![Disaster Recovery at the Edge and in Hybrid Data Streaming Architectures with Apache Kafka (QCon Talk)](https://www.kai-waehner.de/wp-content/uploads/2022/04/Screenshot-2022-04-06-at-07.36.50-1024x544.png)](https://qconlondon.com/london2022/presentation/resilient-real-time-data-streaming-across-the-edge-and-hybrid-cloud)

**Qcon makes conference talks available for free** sometime after the event. I will update this post with the free link as soon as it is available.

## Disaster Recovery with Apache Kafka across all Industries

I hope you enjoyed the slides and video on this exciting topic. [Hybrid and global Kafka infrastructures for disaster recovery](https://www.kai-waehner.de/blog/2020/01/29/deployment-patterns-distributed-hybrid-edge-global-multi-data-center-kafka-architecture/) and other use cases are the norm, not exceptions.

Real-time data beats slow data. That is true in almost every use case. Hence, [data streaming with the de facto standard Apache Kafka](https://www.kai-waehner.de/blog/2021/05/09/kafka-api-de-facto-standard-event-streaming-like-amazon-s3-object-storage/) gets [adopted more and more across all industries](https://www.kai-waehner.de/blog/2020/10/20/apache-kafka-event-streaming-use-cases-architectures-examples-real-world-across-industries/).

**How do you leverage data streaming with Apache Kafka for building resilient applications and enterprise architectures?** What architecture does your platform use? Which products do you combine with data streaming? Let’s [connect on LinkedIn](https://www.linkedin.com/in/kaiwaehner/) and discuss it! Stay informed about new blog posts by [subscribing to my newsletter](https://www.kai-waehner.de/newsletter/).

##### Related Tags

-   [Cluster Linking](https://www.kai-waehner.de/blog/tag/cluster-linking/)
-   [Compliance](https://www.kai-waehner.de/blog/tag/compliance/)
-   [Data Integration](https://www.kai-waehner.de/blog/tag/data-integration/)
-   [data loss](https://www.kai-waehner.de/blog/tag/data-loss/)
-   [Disaster Recovery](https://www.kai-waehner.de/blog/tag/disaster-recovery/)
-   [downtime](https://www.kai-waehner.de/blog/tag/downtime/)
-   [kafka](https://www.kai-waehner.de/blog/tag/kafka/)
-   [Kafka Connect](https://www.kai-waehner.de/blog/tag/kafka-connect/)
-   [kafka streams](https://www.kai-waehner.de/blog/tag/kafka-streams/)
-   [KSQL](https://www.kai-waehner.de/blog/tag/ksql/)
-   [ksqldb](https://www.kai-waehner.de/blog/tag/ksqldb/)
-   [middleware](https://www.kai-waehner.de/blog/tag/middleware/)
-   [MirrorMaker](https://www.kai-waehner.de/blog/tag/mirrormaker/)
-   [Replicator](https://www.kai-waehner.de/blog/tag/replicator/)
-   [Resiliency](https://www.kai-waehner.de/blog/tag/resiliency/)
-   [RPO](https://www.kai-waehner.de/blog/tag/rpo/)
-   [RTO](https://www.kai-waehner.de/blog/tag/rto/)
-   [SLA](https://www.kai-waehner.de/blog/tag/sla/)
-   [SLO](https://www.kai-waehner.de/blog/tag/slo/)
-   [Transactions](https://www.kai-waehner.de/blog/tag/transactions/)

[![](https://www.kai-waehner.de/wp-content/uploads/2019/11/kaiwaehnerPNG-150x150.png)](https://www.kai-waehner.de/blog/author/kai-waehner/)

builds cloud-native event streaming infrastructures for real-time data processing and analytics

By continuing to use the site, you agree to the use of cookies. [more information](https://www.kai-waehner.de/data-privacy/)