#EA #Methods #IT4IT #OpenGroup 
## Introduction
The Open Group's [IT4IT Reference Architecture](https://www2.opengroup.org/ogsys/catalog/c155), released last October, isn't well known yet, but it could be a game changer for the future of IT operations. Here's what you need to know, and why the [Information Technology Infrastructure Library (](http://techbeacon.com/devops-itil-two-paths-common-goal)[ITIL) isn't enough](http://techbeacon.com/devops-itil-two-paths-common-goal).

This new specification, which The Open Group describes as a "standard reference architecture and value chain-based operating model for managing the business of IT," focuses on the entire range of functions, data, and tools you need to manage the business of IT, including IT asset management (ITAM) and IT operations management (ITOM) tools. The standard is vendor independent and supports both agile and lean methodologies.

Tool vendors are already moving to support the specification, and it's well positioned to become a prescriptive standard for a key set of IT operations functions, APIs, and information flows. IT4IT offers a data model, API specification, and functional map for automating a layer of disconnected activities and software within and beyond ITAM and ITOM. Eventually, it could replace today's proprietary data models, gnarly integrations, and manual processes.

Some mainstream tool vendors have said IT4IT compliance will become a formal part of their strategy as early as this summer. Long term, expect all vendor tools to comply with at least part of the IT4IT scope, particularly in the area of ITAM and ITOM tools.

## **Why you need IT4IT**

Like every other standard in the ITOM and IT service management (ITSM) space, IT4IT arose in response to the increasing complexity of runtime environments.

Karel van Zeeland, lead IT4IT architect at Shell Information Technology in the Netherlands, was one of the “founding fathers” of IT4IT. He is enthusiastic about the value standards will bring to IT operations and support professionals.

> “Every supplier of IT services has developed their own tool set for managing IT. These are all driven from different underpinning data models. It is immensely complex to exchange information, even for something as simple as IT incidents with two or three providers—let alone if the number of suppliers grows to dozens or more.
> 
> We think we can leverage the standard when we need to make sourcing decisions. Having external providers use the same standard would make contract negotiation easier, and would help speed up integration of their service offering into our overall portfolio.”

To understand how IT4IT can help, consider how the Simple Network Management Protocol (SNMP) addressed complexity. SNMP replaced a snarl of manual tasks, one-off integrations, and proprietary messaging that did not scale. SNMP solved such problems, and today it is so universal that no one gives much thought to how things were done before. Likewise, the present-day diversity of tools and process used to serve up and manage IT services doesn't scale well in response to modern requirements. Increasing complexity, driven by developments such as cloud, DevOps, IoT, and the vision of an agile, automated digital enterprise, make a move to standards a certainty, and IT4IT is the only nonproprietary architecture on offer. 

While the official IT4IT standard is newly released, the idea has been under development for a long time and is already at Version 2.0. IT4IT is the result of four years of collaboration among industry organizations, academia, and tool vendors. Companies actively participating in the [IT4IT Forum](http://www.opengroup.org/IT4IT) include HPE, IBM, Microsoft, ServiceNow, and some of the biggest IT organizations in the world.

IT4IT was designed to solve the problems many enterprises have with the error-prone, slow, manual activities associated with linking functions such as code management, packaging, release management, deployment, and configuration management. It helps with all of these challenges by prescribing a single architectural framework across the value chain. 

A common operational data model and standardized interfaces are essential to overcoming functional gaps and friction that have grown up at the touchpoints between traditional silos: 

-   Without an approach to tools and processes that break down silos, the agile dream of continuous automated releases will remain a dream. Even where the will to change exists, often the technology needed to do so has not been there. Without a more holistic blueprint, nothing can change.
-   There are no standard ways to integrate monitoring and service management processes and data with external organizations like cloud suppliers and external service desks. Complex integrations are possible but expensive, as well as slow to build and, worse, maintain. The immaturity and inconsistency of cloud provider management interfaces is alarming.
-   Heroic after-the-fact attempts to populate the configuration management database (CMDB) with knowledge about applications, development teams, users, support teams, and other data needed to provide expected levels of support have been disappointing. The data may have been created some time in the past, but it was lost, stored in a useless or unreachable format, and so on.
-   Many IT shops have accumulated a large number of point solutions, either homegrown or from tool vendors, that don’t play well together. Most tool vendors offer a mixed bag of solutions that are not based on a holistic vision of service delivery and don’t play well together within a single vendor’s portfolio, let alone in the typical heterogeneous environment.

 To provide effective end-to-end value, a new way of thinking about the business of IT is needed. 

## **Managing services in the IT value chain**

Enter IT4IT. In the mature enterprise envisioned by The Open Group, everything provided by an IT organization can be thought of as a service, whether it’s an iPhone or access to SAP. This isn’t always a comfortable place for infrastructure traditionalists, but it can relieve your pain.

Every service is based in turn on a pattern called a service model, which evolves through the IT value chain, from vague concept to a well-defined set of operational configuration items.

By focusing on the service model as a persistent object, evolving through all its phases as IT’s fundamental offering, IT4IT provides a structured approach to specifying the functional components and information model needed to standardize the end-to-end IT value chain.

The IT4IT model divides the value chain into four parts, called value streams, that each have a role in defining, creating, delivering, and supporting the IT services that customers consume.

[](http://bit.ly/1TAQlNL)[![](http://techbeacon.com/sites/default/files/phases_and_activities-blue.png)](http://techbeacon.com/sites/default/files/phases_and_activities-blue.png)

_Image credit: The Open Group_

Within each of the value streams shown above, a set of functional components and key data objects form the backbone of the model.

The purple circles along the bottom of the IT4IT Reference Architecture diagram below show the core states for the service model object that make up the service backbone.

 [](http://bit.ly/1mTlaPF)[![](http://techbeacon.com/sites/default/files/it4it_reference_architecture_l1_v_2_0.png)](http://techbeacon.com/sites/default/files/it4it_reference_architecture_l1_v_2_0.png)

_Image credit: The Open Group._

IT4IT lets IT practitioners understand gaps and overlaps, and provides a framework that you can use to understand root causes more clearly.

In one real-world example, an ITSM team repeatedly attacked a persistent data problem in ITSM, with minimal success. But when team members analyzed the problem through the value-chain and systems-thinking lens of IT4IT, they quickly identified upstream data issues in the corporate ERP system as the root cause. Once they stopped fixing the CMDB and started fixing the real problem, things got better quickly.

## **Why ITIL isn't enough** 

IT4IT specifies a framework for procuring and implementing the functions needed to run IT. But ITIL and other frameworks are already out there. Why do IT operations and service management teams need yet another model? Isn’t ITIL enough? Not really.

ITIL does a great job of describing service management processes and the relationships that link them, but IT4IT builds on this and brings some new things to the table:

-   The value chain-based operating model speaks to business value, not just operational practices.
-   IT4IT is an open standard developed by The Open Group, an organization that's open to participation by anyone. That's not the case with ITIL and most other standards in this space.
-   The standard was designed from the start to look at the big picture. It balances all the value streams of the IT value chain, rather than focusing largely on a single one.
-   IT4IT offers prescriptive guidance on how to design, procure, and implement the functions needed to run IT. Its end-to-end, _how to_ emphasis and specific data models make it possible to hold tool vendors not just to generic process compliance but to compliance with specific operational APIs. This differs significantly from ITIL, which is a descriptive set of best practices focused on process.

This is a good thing for everyone. Neither tool vendors nor their customers benefit from huge investments in commodity platforms. Everyone can move to higher value work.

IT4IT has given vendors a standard architecture for the next generation of tools, and most will move to it quickly for functions like service desk, which have become commodities. How they will differentiate themselves on less mature functionality, such as cloud brokering, remains to be seen.

## **Action items: What should ITOM and ITSM practitioners do?** 

If proprietary architectures were already meeting the needs of customers, the impetus for IT4IT would not be there. In fact, the traditional point-solution model for tool design, selection, and implementation is less useful when the real need is end-to-end automation across the whole IT value chain.

Practitioners should understand the opportunities presented by standardized tool and process architectures, and adapt that understanding to making better choices in their own context.

-   **Learn about the standard.** Take an hour or two to download [the IT4IT specification](http://www.opengroup.org/bookstore/catalog/c155.htm) or the [pocket guide](https://www2.opengroup.org/ogsys/catalog/g154) and review what's going on in this space. Check out videos such as the [All Things ITSM Podcast](http://bit.ly/1TxAGxx). Consider how relevant it is to your particular situation. 
-   **Keep IT4IT in mind as you look at tool changes and upgrades.** Today, there are no IT4IT-compliant tool vendors, but over the next 12 to 18 months, the standard will evolve into v3.0, which will include the detailed prescriptive model that tool vendors need to create compliant functions and APIs. It's possible that choosing compliant tools will be the norm in three to five years. Vendors with proprietary answers to end-to-end automation may fall behind those that are willing to play to their strengths within a standards-based architecture.
-   **Consider IT4IT as a template for deploying more effective hybrid service management.** Today, collaboration with external services partners, from call centers to cloud vendors, can create a lot of friction and tie you to expensive one-off integrations. Can using IT4IT as a standard ease the pain? 
-   **Consider getting involved.** IT professionals who are passionate about taking ITOM and ITSM to the next level should think about joining the discussion as the standard evolves. You and your organization can have a say in the future of the standard. Amplify your voice by collaboration with other experts across the globe. 

The IT4IT Reference Architecture is the perfect complement to ITIL and should be part of your IT infrastructure strategy. If your goal is end-to-end automation, getting acquainted with this new standard is a great place to start.

Source: [Why the IT4IT Reference Architecture is a game changer for IT ops (techbeacon.com)](https://techbeacon.com/enterprise-it/why-new-it4it-reference-architecture-game-changer)
#### Keep learning

-   **Choose the right ESM tool** for your needs. Get up to speed with the our  [Buyer's Guide to Enterprise Service Management Tools](https://content.microfocus.com/l/buyers-guide-esm-tools-special-report-tb?utm_source=techbeacon&utm_medium=referral&utm_campaign=7014J000000dVOTQA2)
    
-   **What will the next generation of enterprise service management tools look like?** TechBeacon's [Guide to Optimizing Enterprise Service Management](https://content.microfocus.com/l/enterprise-service-management-tb?utm_source=techbeacon&utm_medium=referral&utm_campaign=7014J000000dVOTQA2) offers the insights.
    
-   **Discover more** about [IT Operations Monitoring with TechBeacon's Guide](https://content.microfocus.com/l/it-operations-monitoring-tb?utm_source=techbeacon&utm_medium=referral&utm_campaign=7014J000000dVOTQA2).
    
-   What's **the best way to get your robotic process automation project off the ground?** Find out how to [choose the right tools—and the right project.](https://content.microfocus.com/l/robotic-process-automation-tb?utm_source=techbeacon&utm_medium=referral&utm_campaign=7014J000000dVOTQA2) 
    
-   **Ready to advance up the IT career ladder?** [TechBeacon's Careers Topic Center](https://content.microfocus.com/careers-tb-tc?utm_campaign=7014J000000dVOTQA2) provides expert advice you need to prepare for your next move.