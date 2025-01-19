We’ve talked previously about a wide range of topics concerning API events and messages — from [current integration guidelines](https://nordicapis.com/apis-and-events-what-does-a-modern-integration-look-like/) to [protocols for event-driven API architectures](https://nordicapis.com/5-protocols-for-event-driven-api-architectures/), the idea of leveraging these systems to automate and streamline communication has been of great interest. Below, we’ll look at two styles within this broad domain — **Event Brokers** and **Message Queues.** We’ll compare the two types, look at use cases, and consider some benefits and drawbacks of each approach.

## What is an Event Broker?

To understand what an Event Broker is, it helps to understand what an **event** is and how it functions within **Event-Driven Architecture**. In its simplest form, an event is any action that produces a change of state. This state change can be simple or complex, but as soon as the state is changed, it counts as an event. In the Event-Driven Architecture approach, consumers “subscribe” to these events and receive notifications when they occur. This stands in contrast to the traditional server-client model, in which a client actively requests updates about a set of information. In other words, it is a “push,” not a “pull” system.

In this architecture, there are three actors. The Event Producer is the entity that is responsible for the generation of the Event; this is typically the API itself. Next, there is the Mediator or Broker; when this Event is sent to the Consumer, it is either distributed in an orderly fashion to specific consumers (Mediator) or broadcast equally to all interested parties (Broker). Finally, the last actor, the Consumer, receives these events and processes them for whatever purpose they desire.

![](https://nordicapis.com/wp-content/uploads/What-is-an-event-broker-nordic-apis-event-mediator.png)

This is the basic order of things, yet even then, there are different kinds of brokers. Some brokers may provide simple subscription pushes, while others might push events into a log based upon previously defined attributes. Ultimately, the paradigm remains the same: an event happens, it is sent to the broker, and then on to the interested parties.

### Pros

An Event Broker’s major pro is that it creates a direct information pipeline between the event generator and the interested parties. This means that as a state change occurs, those parties can almost immediately know that it happened. This is especially useful for logical functions. For instance, if we want to detect when a package has entered a production facility, we can use an API on a weighted pad to simply issue an event state change to all interested parties, updating the office manager, the production assistant, the receiving engine, etc. that a package has arrived (or, at the very least, that the state of the pad has changed).

More complex functions can also be achieved with chained Event Brokers. For instance, if we use a log-based Event Broker, we can “replay” these events as part of a historical log. This can be helpful on the other side of our package delivery example, where the shipping company can detect that a package was scanned from the back of the truck, triggering a “delivered” event to go out to the shipping system. From here, the log can be audited at the end of the day to “replay” those deliveries in comparison to consumer-verified package reception.

### Cons

While chained Event Brokers can carry out more complicated functions, there is definitely a problem at scale. Suppose an event change is the determinant of pushing information to the user. In that case, we are somewhat limited in what can be accomplished. For instance, what if we don’t want to let the user know that some state has changed until we verify that the change in a data store was requested, that it was done correctly, that it was done within policy, and that is has been committed to the production server? To do this, we’d need a series of event mediators mixed in with our Event Brokers, and we’d have to time these events through a relatively complex data flow.

## What is a Message Queue?

Event Brokers solve a simple problem: how do we update a consumer about a state change? Message Queues solve the same sort of problem but in a different way. The simple idea of a Message Queue is that, instead of having a consumer subscribing to an event update, individual elements or services can have a Message Queue containing a variety of calls sequentially sorted and sent to all interested parties.

In essence, instead of having an Event result in a service yelling to a group of interested parties “something happened!”, a Message Queue takes an event or output that requires additional processing and adds it to a long queue. Down the line, consumers or additional processors can look at the queue, and take the message off the line to reprocess, keep, or add to its own processes.

![](https://nordicapis.com/wp-content/uploads/What-is-a-message-queue-nordic-apis.png)

Message Queues can use intricate patterns to address their messages in an effort to direct the state changes in the system properly. Topic-based routing can help address state changes to relevant parties without those parties actually requesting the data. Alternatively, [pub-sub relationships](https://nordicapis.com/websub-common-cases-and-implementations/) can help parties subscribe to general areas of interest, which can then be used as categories for those messages.

### Pros

Decoupling the paradigm of “sender and receiver” inherent in something like an Event Broker can enable significantly more customized interactions. Not every receiver knows _who_ to ask for their events or messages, and not every sender will want to keep an ongoing list of all interested parties. This is especially important in messages, as messages are typically pieces of data that require additional processing or contextualization.

Perhaps the biggest pro of adopting a Message Queue model is that it enables greater levels of [asynchronous communication](https://nordicapis.com/asynchronous-apis-in-choreographed-microservices/). When you have multiple chained brokers, you end up having a waiting line for data handling — consumers have to wait for someone to do something before processing their own data. Under this model, that is not an issue anymore –— processors can take data from the queue and do what they need to do with it when they notice it’s available.

## Cons

With greater complexity comes greater difficulty in doing simple things. It also may be too complicated for the task at hand. For example, if you’re handling a single message generator and a single interested party, you don’t really need a queue. If the interested party is just going to carry out a function and return it to the message creator, then you’re really dealing with a simple event system. Using a Message Queue for a simple function could introduce significant complexity with little gain, which could hurt usability and efficiency.

Unfortunately, extremely complex systems can also suffer issues with the Message Queue approach. While a Message Queue — up to a certain point — tends to help things along, when more messages are introduced, and the interactions are more complex, the buffered and asynchronous nature of the Message Queue can result in too many messages being seen by too many entities. Ultimately, in such a case, a microservice-centric system with a blended approach of Event Brokers and Message Queues makes more sense.

## Which is the Best Choice?

As with anything in the API space, your particular implementation will dictate if an Event Broker or Message Queue is right for your scenario. Each of these paradigms has some specific use cases where they make the most sense.

Event Brokers are best used when the relationship between the event generator and the interested parties is relatively simple, or when the Event does not result in additional asynchronous processing. If your API simply needs to know when a state has changed to either update another API or launch another process, there’s no need to over-complicate the system and add additional overhead.

On the other hand, if you’re looking at a data flow that requires transformation as the result of an event — that is, an event requires transformation encapsulated as a message — it makes more sense to have these messages go through a queue. In this way, the interested parties can act when it makes sense, pulling asynchronously where appropriate.

## Using Event Brokers _and_ Message Queues

Another layer to this problem probably gives us the easiest answer to the question of “which is the best choice” — they both are. These are not mutually exclusive concepts, and in many cases, they can make sense within the same architecture as mutually cooperative elements.

To take our shipping example further, imagine we scan a package as received based upon the weighted doormat. From here, we might want to send an Event to let the office manager know a package has arrived, but we also might send a Message notifying the API that the manager was notified and that the package is waiting for pickup. The chain of custody API might want to wait until the mat issues a new event that the package has been picked up to create a record of custody to notify several other systems that control inventory. Simple Events occur at each of these stages, but so do Events and data packets that need additional processing, often in a delayed manner and often across multiple systems.

Simply put, Event Brokers and Message Queues are two sides of the same coin, and should be viewed as supporting elements in a cohesive solution, rather than as competing options.

## Conclusion

What do you think about this summary? Did we miss any major points? Let us know in the comments below!