---
aliases: [EAI, Enterprise Application Integration]
---
#Technology #Integration #definition 

# Enterprise Application Integration (EAI)
**Enterprise application integration** (**EAI**) is the use of [software](https://en.wikipedia.org/wiki/Software "Software") and computer systems' architectural principles to integrate a set of [enterprise computer applications](https://en.wikipedia.org/wiki/Enterprise_computer_application "Enterprise computer application").\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

## Overview\[[edit](https://en.wikipedia.org/w/index.php?title=Enterprise_application_integration&action=edit&section=1 "Edit section: Overview")\]

Enterprise application integration is an integration framework composed of a collection of technologies and services which form a [middleware](https://en.wikipedia.org/wiki/Middleware_(distributed_applications) "Middleware (distributed applications)") or "middleware framework" to enable integration of systems and applications across an enterprise.[\[1\]](https://en.wikipedia.org/wiki/Enterprise_application_integration#cite_note-1)

Many types of business software such as [supply chain management](https://en.wikipedia.org/wiki/Supply_chain_management "Supply chain management") applications, [ERP](https://en.wikipedia.org/wiki/Enterprise_resource_planning "Enterprise resource planning") systems, [CRM](https://en.wikipedia.org/wiki/Customer_relationship_management "Customer relationship management") applications for managing customers, [business intelligence](https://en.wikipedia.org/wiki/Business_intelligence "Business intelligence") applications, [payroll](https://en.wikipedia.org/wiki/Payroll "Payroll"), and [human resources](https://en.wikipedia.org/wiki/Human_resources "Human resources") systems typically cannot communicate with one another in order to share data or business rules. For this reason, such applications are sometimes referred to as [islands of automation](https://en.wikipedia.org/wiki/Islands_of_automation "Islands of automation") or [information silos](https://en.wikipedia.org/wiki/Information_silo "Information silo"). This lack of communication leads to inefficiencies, wherein identical data are stored in multiple locations, or straightforward processes are unable to be automated.\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

Enterprise application integration is the process of linking such applications within a single organization together in order to simplify and automate business processes to the greatest extent possible, while at the same time avoiding having to make sweeping changes to the existing applications or data structures. Applications can be linked either at the back-end via [APIs](https://en.wikipedia.org/wiki/API "API") or (seldom) the front-end ([GUI](https://en.wikipedia.org/wiki/GUI "GUI")).\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

In the words of research firm [Gartner](https://en.wikipedia.org/wiki/Gartner "Gartner"): "\[EAI is\] the unrestricted sharing of data and business processes among any connected application or data sources in the enterprise."[\[2\]](https://en.wikipedia.org/wiki/Enterprise_application_integration#cite_note-2)

The various systems that need to be linked together may reside on different [operating systems](https://en.wikipedia.org/wiki/Operating_system "Operating system"), use different [database](https://en.wikipedia.org/wiki/Database "Database") solutions or [computer languages](https://en.wikipedia.org/wiki/Computer_language "Computer language"), or different date and time formats, or could be [legacy systems](https://en.wikipedia.org/wiki/Legacy_system "Legacy system") that are no longer supported by the vendor who originally created them. In some cases, such systems are dubbed "[stovepipe systems](https://en.wikipedia.org/wiki/Stovepipe_system "Stovepipe system")" because they consist of components that have been jammed together in a way that makes it very hard to modify them in any way.\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

### Improving connectivity\[[edit](https://en.wikipedia.org/w/index.php?title=Enterprise_application_integration&action=edit&section=2 "Edit section: Improving connectivity")\]

If integration is applied without following a structured EAI approach, [point-to-point connections](https://en.wikipedia.org/wiki/Point-to-point_connection "Point-to-point connection") grow across an organization. Dependencies are added on an impromptu basis, resulting in a complex structure that is difficult to maintain. This is commonly referred to as spaghetti, an allusion to the programming equivalent of [spaghetti code](https://en.wikipedia.org/wiki/Spaghetti_code "Spaghetti code"). For example:\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

> The number of connections needed to have fully meshed point-to-point connections, with n points, is given by ![{\displaystyle {\tbinom {n}{2}}={\tfrac {n(n-1)}{2}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/bd968aa9578b40963d342ae78ceebc08659ab9ec) (see [binomial coefficient](https://en.wikipedia.org/wiki/Binomial_coefficient "Binomial coefficient")). Thus, for ten applications to be fully integrated point-to-point, ![{\displaystyle {\tfrac {10\times 9}{2}}=45}](https://wikimedia.org/api/rest_v1/media/math/render/svg/db9b4dfaca7b0fb9dc27eb4c1fe1fb2e2c901387) point-to-point connections are needed.

However, the number of connections within organizations does not grow according to the square of the number of points. In general, the number of connections to any point is independent of the number of other points in an organization ([Thought experiment](https://en.wikipedia.org/wiki/Thought_experiment "Thought experiment"): if an additional point is added to your organization, are you aware of it? Does it increase the number of connections other unrelated points have?). There are a small number of "collection" points for which this does not apply, but these do not require EAI patterns to manage.

EAI can also increase coupling between systems and therefore increase management overhead and costs.\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

EAI is not just about sharing data between applications but also focuses on sharing both business data and business processes. A [middleware analyst](https://en.wikipedia.org/wiki/Middleware_analyst "Middleware analyst") attending to EAI will often look at the [system of systems](https://en.wikipedia.org/wiki/System_of_systems "System of systems").\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

### Purposes\[[edit](https://en.wikipedia.org/w/index.php?title=Enterprise_application_integration&action=edit&section=3 "Edit section: Purposes")\]

EAI can be used for different purposes:\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

-   [Data integration](https://en.wikipedia.org/wiki/Data_integration "Data integration"): Ensures that information in multiple systems is kept consistent. This is also known as [enterprise information integration](https://en.wikipedia.org/wiki/Enterprise_information_integration "Enterprise information integration") (EII).
-   Vendor independence: Extracts business policies or rules from applications and implements them in the EAI system, so that even if one of the business applications is replaced with a different vendor's application, the business rules do not have to be re-implemented.
-   Common facade: An EAI system can front-end a cluster of applications, providing a single consistent access interface to these applications and shielding users from having to learn to use different software packages.

### Patterns\[[edit](https://en.wikipedia.org/w/index.php?title=Enterprise_application_integration&action=edit&section=4 "Edit section: Patterns")\]

This section describes common design patterns for implementing EAI, including integration, access and lifetime patterns. These are abstract patterns and can be implemented in many different ways. There are many other patterns commonly used in the industry, ranging from high-level abstract design patterns to highly specific implementation patterns.[\[3\]](https://en.wikipedia.org/wiki/Enterprise_application_integration#cite_note-Enterprise_Integration_Patterns-3)

#### Integration patterns\[[edit](https://en.wikipedia.org/w/index.php?title=Enterprise_application_integration&action=edit&section=5 "Edit section: Integration patterns")\]

EAI systems implement two patterns:[\[4\]](https://en.wikipedia.org/wiki/Enterprise_application_integration#cite_note-4)

[Mediation](https://en.wikipedia.org/wiki/Data_mediation "Data mediation") (intra-communication)

Here, the EAI system acts as the go-between or broker between multiple applications. Whenever an interesting event occurs in an application (for instance, new information is created or a new transaction completed) an integration module in the EAI system is notified. The module then propagates the changes to other relevant applications.

[Federation](https://en.wikipedia.org/wiki/Federation_(information_technology) "Federation (information technology)") (inter-communication)

In this case, the EAI system acts as the overarching facade across multiple applications. All event calls from the 'outside world' to any of the applications are front-ended by the EAI system. The EAI system is configured to expose only the relevant information and interfaces of the underlying applications to the outside world, and performs all interactions with the underlying applications on behalf of the requester.

Both patterns are often used concurrently. The same EAI system could be keeping multiple applications in sync (mediation), while servicing requests from external users against these applications (federation).\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

#### Access patterns\[[edit](https://en.wikipedia.org/w/index.php?title=Enterprise_application_integration&action=edit&section=6 "Edit section: Access patterns")\]

EAI supports both asynchronous (fire and forget) and synchronous access patterns, the former being typical in the mediation case and the latter in the federation case.\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

#### Lifetime patterns\[[edit](https://en.wikipedia.org/w/index.php?title=Enterprise_application_integration&action=edit&section=7 "Edit section: Lifetime patterns")\]

An integration operation could be short-lived (e.g., keeping data in sync across two applications could be completed within a second) or long-lived (e.g., one of the steps could involve the EAI system interacting with a human [work flow](https://en.wikipedia.org/wiki/Work_flow "Work flow") application for approval of a loan that takes hours or days to complete).\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

### Topologies\[[edit](https://en.wikipedia.org/w/index.php?title=Enterprise_application_integration&action=edit&section=8 "Edit section: Topologies")\]

There are two major topologies: [hub-and-spoke](https://en.wikipedia.org/wiki/Hub_and_spoke "Hub and spoke"), and [bus](https://en.wikipedia.org/wiki/Enterprise_service_bus "Enterprise service bus"). Each has its own advantages and disadvantages. In the hub-and-spoke model, the EAI system is at the center (the hub), and interacts with the applications via the spokes. In the bus model, the EAI system is the bus (or is implemented as a resident module in an already existing message bus or [message-oriented middleware](https://en.wikipedia.org/wiki/Message-oriented_middleware "Message-oriented middleware")).\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

Most large enterprises use zoned networks to create a layered defense against network oriented threats. For example, an enterprise typically has a credit card processing (PCI-compliant) zone, a non-PCI zone, a data zone, a DMZ zone to proxy external user access, and an IWZ zone to proxy internal user access. Applications need to integrate across multiple zones. The **Hub and spoke** model would work better in this case.\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

### Technologies\[[edit](https://en.wikipedia.org/w/index.php?title=Enterprise_application_integration&action=edit&section=9 "Edit section: Technologies")\]

Multiple technologies are used in implementing each of the components of the EAI system:\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

Bus/hub

This is usually implemented by enhancing standard middleware products ([application server](https://en.wikipedia.org/wiki/Application_server "Application server"), message bus) or implemented as a stand-alone program (i. e., does not use any middleware), acting as its own middleware.

Application connectivity

The bus/hub connects to applications through a set of **adapters** (also referred to as **connectors**). These are programs that know how to interact with an underlying business application. The adapter performs one-way communication(unidirectional), performing requests from the hub against the application, and notifying the hub when an event of interest occurs in the application (a new record inserted, a transaction completed, etc.). Adapters can be specific to an application (e. g., built against the application vendor's client libraries) or specific to a class of applications (e. g., can interact with any application through a standard communication protocol, such as [SOAP](https://en.wikipedia.org/wiki/SOAP "SOAP"), [SMTP](https://en.wikipedia.org/wiki/SMTP "SMTP") or [Action Message Format](https://en.wikipedia.org/wiki/Action_Message_Format "Action Message Format") (AMF)). The adapter could reside in the same process space as the bus/hub or execute in a remote location and interact with the hub/bus through industry-standard protocols such as message queues, web services, or even use a proprietary protocol. In the Java world, standards such as [JCA](https://en.wikipedia.org/wiki/J2EE_Connector_Architecture "J2EE Connector Architecture") allow adapters to be created in a vendor-neutral manner.

[Data format](https://en.wikipedia.org/wiki/File_format "File format") and [transformation](https://en.wikipedia.org/wiki/Data_transformation "Data transformation")

To avoid every adapter having to convert data to/from every other application's formats, EAI systems usually stipulate an application-independent (or common) data format. The EAI system usually provides a data transformation service as well to help convert between application-specific and common formats. This is done in two steps: the adapter converts information from the application's format to the bus's common format. Then, semantic transformations are applied to this (converting zip codes to city names, splitting/merging objects from one application into objects in the other applications, and so on).

Integration modules

An EAI system could be participating in multiple concurrent integration operations at any given time, each type of integration being processed by a different integration module. Integration modules subscribe to events of specific types and process notifications that they receive when these events occur. These modules could be implemented in different ways: on [Java](https://en.wikipedia.org/wiki/Java_(programming_language) "Java (programming language)")\-based EAI systems, these could be [web applications](https://en.wikipedia.org/wiki/Web_application "Web application") or [EJBs](https://en.wikipedia.org/wiki/Enterprise_JavaBean "Enterprise JavaBean") or even [POJOs](https://en.wikipedia.org/wiki/POJO "POJO") that conform to the EAI system's specifications.

Support for [transactions](https://en.wikipedia.org/wiki/Database_transaction "Database transaction")

When used for process integration, the EAI system also provides transactional consistency across applications by executing all integration operations across all applications in a single overarching distributed transaction (using [two-phase commit protocols](https://en.wikipedia.org/wiki/Two-phase_commit_protocol "Two-phase commit protocol") or [compensating transactions](https://en.wikipedia.org/wiki/Compensating_transaction "Compensating transaction")).

### Communication architectures\[[edit](https://en.wikipedia.org/w/index.php?title=Enterprise_application_integration&action=edit&section=10 "Edit section: Communication architectures")\]

Currently, there are many variations of thought on what constitutes the best infrastructure, component model, and standards structure for Enterprise Application Integration. There seems to be a consensus that four components are essential for a modern enterprise application integration architecture:\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

1.  A centralized broker that handles security, access, and communication. This can be accomplished through integration servers (like the [School Interoperability Framework (SIF)](https://en.wikipedia.org/wiki/Schools_Interoperability_Framework "Schools Interoperability Framework") Zone Integration Servers) or through similar software like the [enterprise service bus](https://en.wikipedia.org/wiki/Enterprise_service_bus "Enterprise service bus") (ESB) model that acts as a services manager.
2.  An independent data model based on a standard data structure, also known as a [canonical data model](https://en.wikipedia.org/wiki/Canonical_Model "Canonical Model"). It appears that XML and the use of XML style sheets have become the _[de facto](https://en.wikipedia.org/wiki/De_facto "De facto")_ and in some cases _[de jure](https://en.wikipedia.org/wiki/De_jure "De jure")_ standard for this uniform business language.
3.  A connector, or agent model where each vendor, application, or interface can build a single component that can speak natively to that application and communicate with the centralized broker.
4.  A system model that defines the APIs, data flow and rules of engagement to the system such that components can be built to interface with it in a standardized way.

Although other approaches like connecting at the database or user-interface level have been explored, they have not been found to scale or be able to adjust. Individual applications can publish messages to the centralized broker and subscribe to receive certain messages from that broker. Each application only requires one connection to the broker. This central control approach can be extremely [scalable](https://en.wikipedia.org/wiki/Scalable "Scalable") and [highly evolvable](https://en.wikipedia.org/wiki/Event-driven_SOA "Event-driven SOA").\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

Enterprise Application Integration is related to middleware technologies such as message-oriented middleware ([MOM](https://en.wikipedia.org/wiki/Message-oriented_middleware "Message-oriented middleware")), and data representation technologies such as [XML](https://en.wikipedia.org/wiki/XML "XML") or [JSON](https://en.wikipedia.org/wiki/JSON "JSON"). Other EAI technologies involve using [web services](https://en.wikipedia.org/wiki/Web_service "Web service") as part of [service-oriented architecture](https://en.wikipedia.org/wiki/Service-oriented_architecture "Service-oriented architecture") as a means of integration. Enterprise Application Integration tends to be data centric. In the near future, it will come to include [content integration](https://en.wikipedia.org/wiki/Enterprise_Content_Integration "Enterprise Content Integration") and [business processes](https://en.wikipedia.org/wiki/Business_process "Business process").\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

### Implementation pitfalls\[[edit](https://en.wikipedia.org/w/index.php?title=Enterprise_application_integration&action=edit&section=11 "Edit section: Implementation pitfalls")\]

In 2003 it was reported that 70% of all EAI projects fail. Most of these failures are not due to the software itself or technical difficulties, but due to management issues. Integration Consortium European Chairman Steve Craggs has outlined the seven main pitfalls undertaken by companies using EAI systems and explains solutions to these problems.[\[5\]](https://en.wikipedia.org/wiki/Enterprise_application_integration#cite_note-5)

1.  Constant change: The very nature of EAI is dynamic and requires dynamic project managers to manage their implementation.
2.  Shortage of [EAI experts](https://en.wikipedia.org/wiki/Middleware_analyst "Middleware analyst"): EAI requires knowledge of many issues and technical aspects.
3.  Competing standards: Within the EAI field, the paradox is that EAI standards themselves are not universal.
4.  EAI is a tool paradigm: EAI is not a tool, but rather a system and should be implemented as such.
5.  Building interfaces is an art: Engineering the solution is not sufficient. Solutions need to be negotiated with user departments to reach a common consensus on the final outcome. A lack of consensus on interface designs leads to excessive effort to map between various systems' data requirements.
6.  Loss of detail: Information that seemed unimportant at an earlier stage may become crucial later.
7.  Accountability: Since so many departments have many conflicting requirements, there should be clear accountability for the system's final structure.

Other potential problems may arise in these areas:\[_[citation needed](https://en.wikipedia.org/wiki/Wikipedia:Citation_needed "Wikipedia:Citation needed")_\]

-   Lack of centralized co-ordination of EAI work.[\[6\]](https://en.wikipedia.org/wiki/Enterprise_application_integration#cite_note-6)
-   Emerging Requirements: EAI implementations should be extensible and modular to allow for future changes.
-   Protectionism: The applications whose data is being integrated often belong to different departments that have technical, cultural, and political reasons for not wanting to share their data with other departments

### See also\[[edit](https://en.wikipedia.org/w/index.php?title=Enterprise_application_integration&action=edit&section=12 "Edit section: See also")\]

-   [Enterprise architecture framework](https://en.wikipedia.org/wiki/Enterprise_architecture_framework "Enterprise architecture framework")
-   [Strategies for Enterprise Application Integration](https://www.chakray.com/en/strategies-for-enterprise-application-integration/)
-   [Business semantics management](https://en.wikipedia.org/wiki/Business_semantics_management "Business semantics management")
-   [Data integration](https://en.wikipedia.org/wiki/Data_integration "Data integration")
-   [Enterprise information integration](https://en.wikipedia.org/wiki/Enterprise_information_integration "Enterprise information integration")
-   [Enterprise integration](https://en.wikipedia.org/wiki/Enterprise_integration "Enterprise integration")
-   [Enterprise Integration Patterns](https://en.wikipedia.org/wiki/Enterprise_Integration_Patterns "Enterprise Integration Patterns")
-   [Enterprise service bus](https://en.wikipedia.org/wiki/Enterprise_service_bus "Enterprise service bus")
-   [Generalised Enterprise Reference Architecture and Methodology](https://en.wikipedia.org/wiki/Generalised_Enterprise_Reference_Architecture_and_Methodology "Generalised Enterprise Reference Architecture and Methodology")
-   [Integration appliance](https://en.wikipedia.org/wiki/Integration_appliance "Integration appliance")
-   [Integration competency center](https://en.wikipedia.org/wiki/Integration_competency_center "Integration competency center")
-   [Integration platform](https://en.wikipedia.org/wiki/Integration_platform "Integration platform")
-   [Straight through processing](https://en.wikipedia.org/wiki/Straight_through_processing "Straight through processing")
-   [System integration](https://en.wikipedia.org/wiki/System_integration "System integration")

#### Initiatives and organizations\[[edit](https://en.wikipedia.org/w/index.php?title=Enterprise_application_integration&action=edit&section=13 "Edit section: Initiatives and organizations")\]

-   [Health Level 7](https://en.wikipedia.org/wiki/Health_Level_7 "Health Level 7")
-   [Open Knowledge Initiative](https://en.wikipedia.org/wiki/Open_Knowledge_Initiative "Open Knowledge Initiative")
-   [OSS through Java](https://en.wikipedia.org/wiki/OSS_through_Java "OSS through Java")
-   [Schools Interoperability Framework](https://en.wikipedia.org/wiki/Schools_Interoperability_Framework "Schools Interoperability Framework") (SIF)

## References\[[edit](https://en.wikipedia.org/w/index.php?title=Enterprise_application_integration&action=edit&section=14 "Edit section: References")\]

1.  **[^](https://en.wikipedia.org/wiki/Enterprise_application_integration#cite_ref-1 "Jump up")** Linthicum, David S. (2000). [_Enterprise Application Integration_](https://books.google.com/books?id=LIYadz3qEyEC&q=Enterprise+application+integration+what+is). Addison-Wesley Professional. [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [978-0-201-61583-8](https://en.wikipedia.org/wiki/Special:BookSources/978-0-201-61583-8 "Special:BookSources/978-0-201-61583-8").
2.  **[^](https://en.wikipedia.org/wiki/Enterprise_application_integration#cite_ref-2 "Jump up")** In its April 2001 report for AIIM International, "Enterprise Applications: Adoption of E-Business and Document Technologies, 2000–2001: Worldwide Industry Study," Gartner defines EAI as "the unrestricted sharing of data and business processes among any connected applications and data sources in the enterprise."  
    Gable, Julie (March–April 2002). ["Enterprise application integration"](http://www.techstreet.com/direct/ExSum_EU.pdf) (PDF). _Information Management Journal_. Retrieved 2008-01-22.
3.  **[^](https://en.wikipedia.org/wiki/Enterprise_application_integration#cite_ref-Enterprise_Integration_Patterns_3-0 "Jump up")** Hohpe, Gregor; Woolf, Bobby (2015). ["Messaging Patterns Overview"](http://www.enterpriseintegrationpatterns.com/patterns/messaging/). Enterpriseintergationpatterns.com and Addison-Wesley. Retrieved 2016-05-19.
4.  **[^](https://en.wikipedia.org/wiki/Enterprise_application_integration#cite_ref-4 "Jump up")** MSquare Systems (2014-05-21). "Types of EAI". Archived on 2014-05-21 at [https://web.archive.org/web/20140521124430/http://www.msquaresystems.com/enterprise-application-2/eai](https://web.archive.org/web/20140521124430/http://www.msquaresystems.com/enterprise-application-2/eai). _[MSquare Systems](https://en.wikipedia.org/w/index.php?title=MSquare_Systems&action=edit&redlink=1 "MSquare Systems (page does not exist)")_ Retrieved on 2014-05-28 from [http://www.msquaresystems.com/enterprise-application-2/eai](http://www.msquaresystems.com/enterprise-application-2/eai).
5.  **[^](https://en.wikipedia.org/wiki/Enterprise_application_integration#cite_ref-5 "Jump up")** Trotta, Gian (2003-12-15). ["Dancing Around EAI 'Bear Traps'"](http://www.ebizq.net/topics/int_sbp/features/3463.html). Retrieved 2006-06-27.
6.  **[^](https://en.wikipedia.org/wiki/Enterprise_application_integration#cite_ref-6 "Jump up")** Toivanen, Antti (2013-10-25). ["Avoiding Pitfalls of Integration Competency Centers"](https://web.archive.org/web/20170730052826/https://integrationwarstories.com/2013/10/25/avoiding-pitfalls-of-integration-competency-centers/). Archived from [the original](http://integrationwarstories.com/2013/10/25/avoiding-pitfalls-of-integration-competency-centers/) on 2017-07-30. Retrieved 2013-10-26.