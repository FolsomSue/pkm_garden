---
tags:
  - EA
  - Integration
  - Data_Integration
  - definition
  - Technology
  - Pub-Sub
aliases:
  - PubSub
  - Pub-Sub
  - Publish-Subscribe
---
# Pub-Sub Model Fundamentals
-   [What is the publish-subscribe model?](https://cedalo.com/blog/pub-sub-model-fundamentals/#What_is_the_publish-subscribe_model "What is the publish-subscribe model?")
    -   [Publish-subscribe architecture](https://cedalo.com/blog/pub-sub-model-fundamentals/#Publish-subscribe_architecture "Publish-subscribe architecture")
-   [How does the publish-subscribe model work?](https://cedalo.com/blog/pub-sub-model-fundamentals/#How_does_the_publish-subscribe_model_work "How does the publish-subscribe model work?")
-   [Core features of the publish-subscribe model](https://cedalo.com/blog/pub-sub-model-fundamentals/#Core_features_of_the_publish-subscribe_model "Core features of the publish-subscribe model")
    -   [Publish-subscribe decoupling](https://cedalo.com/blog/pub-sub-model-fundamentals/#Publish-subscribe_decoupling "Publish-subscribe decoupling")
    -   [Publish-subscribe filtering](https://cedalo.com/blog/pub-sub-model-fundamentals/#Publish-subscribe_filtering "Publish-subscribe filtering")
-   [Semantics Delivery](https://cedalo.com/blog/pub-sub-model-fundamentals/#Semantics_Delivery "Semantics Delivery")
-   [Advantages of the publish-subscribe model](https://cedalo.com/blog/pub-sub-model-fundamentals/#Advantages_of_the_publish-subscribe_model "Advantages of the publish-subscribe model")
-   [Disadvantages of the publish-subscribe model](https://cedalo.com/blog/pub-sub-model-fundamentals/#Disadvantages_of_the_publish-subscribe_model "Disadvantages of the publish-subscribe model")
-   [When to avoid using the publish-subscribe model?](https://cedalo.com/blog/pub-sub-model-fundamentals/#When_to_avoid_using_the_publish-subscribe_model "When to avoid using the publish-subscribe model?")
-   [When to use the publish-subscribe model](https://cedalo.com/blog/pub-sub-model-fundamentals/#When_to_use_the_publish-subscribe_model "When to use the publish-subscribe model")
    -   [Examples of publish-subscribe model usage in IoT](https://cedalo.com/blog/pub-sub-model-fundamentals/#Examples_of_publish-subscribe_model_usage_in_IoT "Examples of publish-subscribe model usage in IoT")
-   [How can MQTT support your publish-subscribe architecture requirements?](https://cedalo.com/blog/pub-sub-model-fundamentals/#How_can_MQTT_support_your_publish-subscribe_architecture_requirements "How can MQTT support your publish-subscribe architecture requirements?")
-   [How do message queues and the publish-subscribe model differ?](https://cedalo.com/blog/pub-sub-model-fundamentals/#How_do_message_queues_and_the_publish-subscribe_model_differ "How do message queues and the publish-subscribe model differ?")
    -   [Communication pattern](https://cedalo.com/blog/pub-sub-model-fundamentals/#Communication_pattern "Communication pattern")
    -   [Message persistence](https://cedalo.com/blog/pub-sub-model-fundamentals/#Message_persistence "Message persistence")
    -   [Message ordering](https://cedalo.com/blog/pub-sub-model-fundamentals/#Message_ordering "Message ordering")
    -   [Consumer acknowledgment](https://cedalo.com/blog/pub-sub-model-fundamentals/#Consumer_acknowledgment "Consumer acknowledgment")
    -   [Use cases](https://cedalo.com/blog/pub-sub-model-fundamentals/#Use_cases "Use cases")
-   [Wrap-up](https://cedalo.com/blog/pub-sub-model-fundamentals/#Wrap-up "Wrap-up")

Imagine receiving an urgent alert while away from home – your fire alarm detects smoke. 

With a few taps, you can remotely secure the situation by shutting off the gas, cutting power, and calling the fire department, or even going further and automating all these steps to start all these processes with one click of a button on your smartphone.

The publish-subscribe model achieves this control and real-time communication among your home IoT devices. 

This article explores the Pub/Sub model from its architecture to its advantages and practical use cases. So let’s start by gaining a better understanding of what the **Pub/Sub model** is.

## What is the publish-subscribe model?

The **publish-subscribe (Pub/Sub) design pattern** is used in distribution systems for _asynchronous communication between components and services_.

There are quite a few implementations of this pattern. For example, **MQTT**, which is widely used when working with systems that implement **event-driven architecture** and **IoT devices**.

### Publish-subscribe architecture

Regardless of the different implementations of Pub/Sub systems, they all consist of the following basic elements:

-   **Message:** A message is a unit of data that is sent between a publisher and subscriber.
-   **Topic****:** Topics serve as unique categories or channels within the Pub/Sub system. They provide a structured way to classify, organize and filter messages based on their content or purpose.
-   **Publisher:** This component is responsible for creating and sending messages to a specific topic.
-   **Subscriber**: A component that subscribes to the relevant topic and receives messages from it.
-   **Message Broker:** Acts as an intermediary between the publishers and the subscribers, it stores all topics and messages from publishers and routes messages to subscribers based on their specific topic subscriptions. This ensures that all relevant messages are efficiently reach all subscribers who are show interest in the corresponding topics.

Now that you have a clear understanding of the primary components of the Pub/Sub model, let’s delve into how these systems operate in practice.

## How does the publish-subscribe model work?

The main idea behind the operation of the Pub/Sub system is that the publisher does not send messages directly to the subscriber, but works through an intermediary – _a broker_.

The following steps show how the model works:

1.  Subscribers subscribe to a specific topic to receive messages.
2.  The publisher sends a message to the relevant topic.
3.  The broker accepts and stores this message in a specific topic and sends it to all subscribers.

Let’s consider the operation of the Pub/Sub system using the specific example at the beginning of the article.

At home, you have IoT devices that are responsible for detecting smoke and controlling electricity and gas. For communication between all these devices, you use the MQTT broker, which ensures reliable operation between different devices.

The system that notices smoke is a publisher that will send a message with an alert to the broker, your smartphone is a subscriber that will receive a message that there is smoke in the house.

Also, the subscriber (in our example, your smartphone) can act as a publisher, which will send messages to a separate topic to which the subscribed devices responsible for the supply of electricity and gas will turn off the supply.

In this case, one message will be sent, but two separate IoT devices will be able to receive the message and react to it accordingly.

## Core features of the publish-subscribe model

The previous sections looked at the main components and the operations between them. This section will delve deeper into the main features of Pub/Sub systems.

### Publish-subscribe decoupling

One of the main features of Pub/Sub systems is their flexibility and scalability – due to **loose coupling** between system components.

There are two coupling systems:

-   **Tight coupling** describes system components that are highly dependent on each other. If one component malfunctions, it will affect the operation of other components, which can cause the entire system to crash. Also, updating one component may require updating dependent components, which creates system inflexibility and makes maintenance and scalability very difficult.
-   **Loose coupling**, on the other hand, will not have such problems. The components of such systems are independent. In the case of a Pub/Sub system, the publisher, subscriber, and broker are independent entities with well-defined interfaces that interact with each other using a standardized protocol such as MQTT. This allows the development of each separate component without needing to change other components of the system.

Take the home system example of IoT devices. You can change and update each device separately and it will not affect the system as a whole, as long as you know the address of the broker and the name of the topic to send messages to.

Also, the example system is easily scalable due to loose coupling. In theory, you can add as many IoT devices and smartphones through which the broker will exchange messages.

### Publish-subscribe filtering

Filtering becomes essential in a dynamic system where numerous publishers and subscribers interact to ensure that messages reach the right clients. The Pub/Sub systems offer robust filtering mechanisms that enhance message targeting and relevance.

-   **Topic-based Filtering:** At the core of Pub/Sub systems is topic-based categorization. Subscribers express their interests by subscribing to specific topics. Publishers send messages to designated topics. This alignment ensures that messages are delivered only to subscribers interested in that particular category. For example, a Fire Safety System will send messages to the “**fire-alert**” topic, allowing subscribers to subscribe and receive relevant messages.
-   **Wildcards for Advanced Filtering:** Pub/Sub systems often support wildcard subscriptions based on naming patterns. Subscribers can use wildcards to match and subscribe to topics that adhere to specific criteria. For instance, a subscriber interested **in all system alert topics** can use a wildcard to simplify their subscription. This feature simplifies subscription management, especially in multi-topic scenarios. Refer to [this guide on MQTT topics and wildcards](https://cedalo.com/blog/mqtt-topics-and-mqtt-wildcards-explained/#What_are_MQTT_Wildcards) for more information.
-   **Content-Based Filtering:** Messages are delivered to a subscriber only if the attributes or content of those messages meet the constraints defined by the subscriber. For example, you want to receive messages from devices in which the word “**Error**” is present. Filtering is what enables you to know that something has happened to your IoT devices at home.

## Semantics Delivery

In Pub/Sub systems, messages travel a long way from the publisher to the broker and from the broker to the subscriber.

_At least two points exist where a message can get lost (e.g., from the publisher to broker, or from the broker to the subscriber). In such cases, there is a concept of semantic delivery, also called **Quality of Service (QoS) levels in MQTT** that guarantees the delivery of messages:_

-   **At most once:** In this semantic, message delivery occurs at most once. While this ensures minimal message duplication, it doesn’t guarantee that all messages are received. Network issues or system failures might cause the loss of some messages.
-   **At least once:** This semantic ensures message delivery at least once, even if it means occasional duplicates. It offers stronger reliability by minimizing message loss.
-   **Exactly once:** This is the most robust semantic, guaranteeing that message delivery exactly once and in the correct order. Achieving this requires careful coordination and in scenarios where message accuracy is critical.

By providing these semantics, Pub/Sub systems allow developers to choose the appropriate level of message delivery reliability based on their application’s requirements.

These features make Pub/Sub systems versatile and adaptable to various communication needs. They provide the tools to build efficient, reliable, and responsive communication networks. To read more about QoS and MQTT check out [this article](https://cedalo.com/blog/understanding-mqtt-qos/).

## Advantages of the publish-subscribe model

The decoupled architecture and versatile nature of Pub/Sub systems offers the following key benefits:

-   **Efficient resource utilization:** Pub/Sub systems ensures message delivery only to interested subscribers. This efficiency reduces network congestion and minimizes unnecessary data transfer, making the best use of available resources.
-   **Real-time updates:** Publishers can instantly notify subscribers about important events or changes, making them well-suited for applications requiring immediate information dissemination (e.g., event-driven architecture).
-   **Smooth scalability:** Pub/Sub is able to scale the architecture of message brokers, filters, and users without affecting the underlying components. Implementing a new messaging system is as simple as changing a topic, as long as message formats are compatible–even with complex architectural changes.
-   **Modular and flexible:** Pub/Sub systems have a modular architecture that separates communication and logic, making it easier to troubleshoot issues. This also allows developers to focus on specific components without worrying about affecting the rest of the application.

Additionally, the loose coupling between components eliminates the need to predetermine a fixed number of publishers or subscribers, making Pub/Sub systems flexible. If necessary, you can add additional components to the desired topic.

## Disadvantages of the publish-subscribe model

While the publish-subscribe model offers numerous advantages, it also comes with challenges. Here are some disadvantages to consider:

-   **Increased latency:** While the Pub/Sub model is excellent for real-time communication, it may introduce some latency compared to direct communication methods. Messages must traverse the broker, which can add a slight delay, although it’s typically negligible for many applications.
-   **Limited to asynchronous communication:** Pub/Sub is primarily designed for asynchronous communication. While this benefits many scenarios, it might not be suitable for applications requiring strict synchronous interactions, where one entity depends on immediate responses from another.

For example, Pub/Sub systems are not suitable for working with media such as audio and video, as they require synchronous data streaming between source and receiver.

## When to avoid using the publish-subscribe model?

Pub/Sub models are a powerful tool, but they are not a one-size-fits-all solution. They come with their own set of limitations, and their suitability depends on the specific needs and constraints of a given system or application. The following are scenarios depict situations in which the Pub/Sub is unsuitable for application:

-   **Simple, point-to-point communication:** If your system primarily involves direct, one-to-one communication without the need for message distribution to multiple recipients, the publisher-subscriber model might introduce unnecessary complexity. In such cases, simpler communication methods like direct messaging or request-response patterns may be more suitable.
-   **Unsuitable for periodic or background tasks:** Pub/Sub operates asynchronously, making it incompatible with systems designed for tasks that run periodically, such as [cron](https://en.wikipedia.org/wiki/Cron) jobs triggered at specific time intervals
-   **Small-scale applications:** For small-scale applications with a limited number of components and straightforward communication needs, the introduction of a Pub/Sub infrastructure might be overcomplicated. Simpler communication models could lead to a more lightweight and easily manageable system.
-   **Non event-driven systems:** For the most part, systems using the Pub/Sub model are those that implement event-driven architecture, in which individual components react to changes in the system state. If your application uses a more traditional approach, such as a batch processing model, the Pub/Sub system may not be suitable for you.

## When to use the publish-subscribe model

After exploring the advantages and disadvantages of Pub/Sub systems, you should now have a clear understanding of where to apply this versatile system. Let’s delve into some of the most popular use cases where the Pub/Sub model truly shines.

-   **Social media platforms:** Pub/Sub systems are ideal for sending real-time notifications to users or applications. Social media platforms, messaging apps, and news websites often use Pub/Sub to instantly notify users about new messages, updates, or relevant content – like in our first example. A good example of this use case is Meta, which uses MQTT for its [Facebook Messenger](https://engineering.fb.com/2011/08/12/android/building-facebook-messenger/).
-   **Content streaming:** Platforms like Netflix and Spotify use Pub/Sub to distribute multimedia content to users. A great example is Netflix, which utilizes it as part of its recommendation system. They divide the system into three levels: offline, nearline, and online modules, which ensure the processing of each user’s information. Each module has its own data storage and processing mechanism that transfers information from one module to another. Netflix also uses the Pub/Sub system to send the results of data processing to the user: handle errors, monitor system performance and send notifications. For further details about how Netflix utilizes the Pub/Sub system, please refer to the [link](https://netflixtechblog.com/system-architectures-for-personalization-and-recommendation-e081aa94b5d8).
-   **Distributed logging:** Application logs are critical for distribution systems. They help to reproduce events in the system, facilitate troubleshooting, and help respond quickly to critical changes in the system. With the Pub/Sub system, you can set up a separate topic for sending logs. This allows you to process and store the logs easily later on. Additionally, you can use **content-based filtering** (as mentioned earlier) to quickly identify logs with errors and set up triggers for quick response to any issues.
-   **Internet of Things (IoT):** IoT devices generate vast amounts of data that require efficient distribution. Pub/Sub enables seamless communication between IoT devices, central servers, and other components, ensuring timely data updates and event handling.

You can infinitely expand this list, and further subdivisions are possible for some examples. Take IoT, for instance: the versatility of this technology allows for countless applications and use cases across various industries.

### Examples of publish-subscribe model usage in IoT

In the realm of IoT, imagination knows no bounds. Interestingly, many of the gadgets you incorporate into your daily routine fall under the category of IoT. The publish-subscribe model finds numerous applications with IoT devices, and some of the most prevalent use cases include:

-   **Environmental monitoring:** IoT sensors deployed in agriculture or environmental monitoring networks frequently use the publish-subscribe model. For example, soil moisture sensors can publish data on a topic. Subscribers, such as a farming application, receive this data to make informed irrigation decisions.
-   **Healthcare telemetry:** IoT devices like wearable health monitors can employ publish-subscribe for transmitting patient data. When a health device collects vital signs, it publishes the data to a topic. Healthcare providers can subscribe to this topic to monitor patients’ health remotely.
-   **Smart home automation:** In smart homes, various IoT devices like thermostats, lights, and security cameras can communicate through the publish-subscribe model. For instance, when a motion sensor detects movement, it publishes an event on a specific topic. Subscribers, such as smart lights, can subscribe to this topic to respond by turning on lights in the detected area.

**MQTT** is a widely used protocol in IoT that enables communication between devices through the publish-subscribe design pattern. [This guide](https://cedalo.com/blog/complete-mqtt-protocol-guide/#What_is_MQTT) explains the connection between MQTT and the publish and subscribe design pattern in detail.

## How can MQTT support your publish-subscribe architecture requirements?

MQTT inherently follows the publish-subscribe communication pattern, which is essential for scenarios where publishers need to distribute messages to multiple subscribers without direct coupling. It’s purposely-built for the Pub/Sub model. Several other compelling reasons make Pub/Sub an excellent choice for MQTT:

-   **Lightweight and efficient:** MQTT is designed to be incredibly lightweight, making it suitable for resource-constrained devices and low-bandwidth networks. This efficiency is crucial in applications like IoT, where conserving resources is paramount.
-   **Quality of Service (QoS) Levels:** MQTT offers different QoS levels, allowing users to choose the desired trade-off between reliability and efficiency. This flexibility is critical in applications with varying message delivery requirements.
-   **[Last Will and Testament (LWT)](https://cedalo.com/blog/mqtt-last-will-explained-and-example/):** MQTT allows clients to define a “Last Will” message, which the broker will publish if the client unexpectedly disconnects. This feature is essential for managing device failures in IoT applications.
-   **Broad industry adoption:** MQTT has gained widespread adoption across various industries, including industrial automation, home automation, and telemetry. Its proven reliability and efficiency make it a trusted choice for many applications.
-   **Rich ecosystem:** MQTT has a well-developed ecosystem of libraries, tools, and frameworks available for different programming languages and platforms. This makes it easier to integrate MQTT into diverse applications.
-   **Security features:** MQTT can be configured with various security mechanisms, such as TLS/SSL encryption and username/password authentication, ensuring that data remains protected during transmission.
-   **Open standard:** MQTT is an open standard maintained by OASIS, ensuring its long-term availability and support from a wide range of vendors and communities.

If you are eager to delve deeper into MQTT, explore its features, and gain mastery over this system, enroll in the MQTT Academy by following the link provided [here](https://cedalo.com/mqtt-academy/).

## How do message queues and the publish-subscribe model differ?

It’s inevitable to encounter the age-old question: What sets a message queue apart from the Pub/Sub model? Let’s dissect the crucial distinctions between these two communication paradigms.

First of all, you need to understand what a message queue is: A **message queue** also serves to asynchronously send messages from one component to another, _all messages are stored in a queue and processed once and then deleted, unlike a Pub/Sub system where messages are sent to many subscribers at once and may be processed many times_.

### Communication pattern

**Message Queue:** Message queues adopt a service-to-service communication. In this setup, the sender (producer) sends a message to a specific receiver (consumer). This message is stored in a queue until the recipient can receive it. Messages are typically consumed once by a single recipient.

**Pub/Sub Model:** The Pub/Sub model inherently follows a one-to-many communication pattern. Publishers broadcast messages to multiple subscribers without necessarily knowing the identity or quantity of subscribers. Messages reach all interested parties, of course, in accordance with the [Quality of Services](https://cedalo.com/blog/understanding-mqtt-qos/) (QoS).

### Message persistence

**Message Queue:** Message queues often offer message persistence, meaning messages are stored until successfully consumed by a consumer. This guarantees message durability and fault tolerance.

**Pub/Sub Model:** In many Pub/Sub systems, messages are transient and do not automatically persist. Subscribers receive messages as they are published, and if a subscriber is inactive, it may miss messages.

### Message ordering

**Message Queue:** Message queues typically maintain strict message ordering. Messages are consumed in the order they were added to the queue, crucial for scenarios where message sequence matters.

**Pub/Sub Model:** The Pub/Sub model does not guarantee strict message order. Subscribers may receive messages out of order, depending on factors like message routing and subscriber activity.

### Consumer acknowledgment

**Message Queue:** Message queues often rely on explicit acknowledgment from consumers to mark messages as processed. This ensures that a message is not lost if a consumer fails during processing.

**Pub/Sub Model:** Pub/Sub systems may not require an explicit confirmation from subscribers. In the case of QoS0, after the message is sent to all subscribers, the system assumes successful delivery. This can make messaging easier to use, but may not offer the same level of reliability, requiring additional configuration of more robust message delivery semantics.

### Use cases

**Message Queue:** Message queues are commonly employed in scenarios where strict message order, guaranteed delivery, and message durability are paramount. Examples include task queues, job processing, and asynchronous communication between components.

**Pub/Sub Model:** Pub/Sub systems are ideal for scenarios necessitating real-time updates or notifications to multiple consumers. Common use cases encompass event-driven architectures, broadcasting updates to subscribers, and Internet of Things (IoT) applications.

Therefore, the choice between a message queue and the Pub/Sub model depends on the specific needs of your application. Message queues are suitable for service-to-service communication with guaranteed order and durability, which can be achieved out of the box. On the other hand, Pub/Sub systems achieve this by setting up QoS2 in MQTT. The Pub/Sub model is great when distributing messages to many subscribers without knowing the identity of the recipients.

## Wrap-up

The Pub/Sub model is a crucial framework for modern technology that enables efficient and real-time communication between components and services. It comprises several essential elements, such as publishers, subscribers, and a broker.

When looking at different scenarios involving real-time notifications and IoT applications, you can see that the publish-subscribe model has a wide range of applications. In particular, the MQTT protocol is a great example of its implementation. The protocol follows the publish-subscribe message pattern, allowing publishers to distribute messages to multiple subscribers without direct coupling.

Although the Pub/Sub model has certain drawbacks, it provides several advantages that make it suitable for widespread industry adoption.

##### About the author

For over three years, Bohdan has been dedicated to projects centered around event-driven architecture. Throughout this period, he has actively participated in various projects, varying from startups to large-scale applications involving teams exceeding a hundred members.

Bohdan's main area of expertise lies within IoT devices, encompassing monitoring and home security systems, ship analysis systems, and cloud cluster analytics.

Bohdan has a deep passion for acquiring and imparting new knowledge to others. In pursuit of this passion, he creates training courses for students, writes articles, and collaborates with interns, aiming to share his expertise and contribute to the growth of others in the field.