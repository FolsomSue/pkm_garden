#Technology #definition #Integration #Patterns 
# Integration Frameworks
![Default image background](https://www.credera.com/static/2c51ac833a5973d0cc3963511cbf00c5/8c332/default-banner.png)

Integration frameworks provide a model for interaction and communication between mutually interacting software applications in service-oriented architecture (SOA).  Most integration frameworks are based on, and implement, a set of patterns from the book _Enterprise Integration Patterns_ by Gregor Hohpe and Bobby Woolf. These patterns attempt to provide technology agnostic guidance toward solving many of the known, repeated problems that software developers encounter when integrating applications. Integration frameworks can help whether you’re integrating with an existing application, connecting to a third party web service, or building a complex transaction-processing platform.

_Enterprise Integration Patterns_ details 65 known patterns. Here are a few examples and their respective symbols:

### Responsibilities of an Integration Framework

Aside from the implementation of the major integration patterns, frameworks provide the following core responsibilities:

-   **Orchestration:** Organizing and arranging finely grained components into logical process flows.
    
-   **Manipulation and Transformation:** Converting data between formats or enriching data in its existing format.
    
-   **Transportation:** Providing communication in a multitude of formats including HTTP, FTP, SMTP, JDBC, and JMS. They may also provide implementations of proprietary formats like Tibco, Vitria, CICS, SAP, SalesForce, and PayPal.
    
-   **Mediation:** Decoupling of objects by providing a communication layer through which they interact. See [mediator pattern](http://en.wikipedia.org/wiki/Mediator_pattern) for more info.
    

### When to Use an Integration Framework

Consider an integration framework when:

-   Integrating applications with multiple communication protocols or technologies.
    
-   Building applications or application platforms that require loosely coupled, fine-grained process orchestration.
    
-   The project requires message routing, forking, aggregation, transformation, or enrichment.
    
-   … And you don’t want to write it all yourself.
    

Using a framework will give you a standardized way to model and implement all of the aforementioned integration patterns and will greatly reduce the amount of boilerplate code you write.

For example, if we wanted to expose a single endpoint to receive both SOAP and JSON messaging and route to the appropriate service depending on the content of the message, we could use an integration framework to build a flow that looks like this:

Each component encapsulates a single behavior, and is decoupled from the others using channels (queues). The user is left to configure the properties of each component and implement the business logic that the content-based router will use to determine which channel receives the message. That business logic could be as simple as a single method, expression or a complex load-balancing algorithm.

In this example, the Gateway Channel Adapter receives a message and sends it to Channel In, which sends it to the Content Based Router. The router contains the business logic to figure out if the content is SOAP or JSON and forwards it to the appropriate channel. These channels then deliver the data to the appropriate endpoint.

This flow above was built with Spring Integration. As you can see, it’s based on the exact same integration patterns mentioned above; the only difference is the iconography.

### Java Integration Frameworks

There are several very mature integration frameworks for Java. The most popular Java integration frameworks are Apache Camel, Spring Integration, and Mule ESB (as the name implies, it provides full ESB functionality). All three support the enterprise integration patterns mentioned above and are open source. Each provides slightly different configuration methods, from XML to DSLs, IDE tooling and communication support. In my next post, I’ll dive deeper into Spring Integration.

If you have questions or comments, feel free to post in the comment section below or contact us at info@credera.com. You can also follow us on Twitter at @CrederaOpen or connect with us on [LinkedIn](http://www.linkedin.com/company/credera?goback=%2Enmp_*1_*1_*1_*1_*1_*1_*1_*1_*1_*1&trk=top_nav_home).

###  References:

Enterprise Integration Patterns [http://www.eaipatterns.com](http://www.eaipatterns.com/)

MuleSoft [http://www.mulesoft.com](http://www.mulesoft.com/)

SpringSource [http://www.spring.io](http://www.spring.io/)

Apache Camel [http://camel.apache.org](http://camel.apache.org/)

Kai Waehner’s Blog [http://www.kai-waehner.de](http://www.kai-waehner.de/)

-   [Integration Frameworks](https://www.credera.com/insights/tag/integration-frameworks)
-   [Enterprise Integration Patterns](https://www.credera.com/insights/tag/enterprise-integration-patterns)
-   [Java Integration Frameworks](https://www.credera.com/insights/tag/java-integration-frameworks)