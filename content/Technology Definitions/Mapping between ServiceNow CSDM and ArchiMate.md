---
title: Mapping between ServiceNow CSDM and ArchiMate
source: https://bizzdesign.com/blog/mapping-between-servicenow-csdm-and-archimate-discover-a-new-digitized-world-of-management-support/
author:
  - "[[https://bizzdesign.com/blog/mapping-between-servicenow-csdm-and-archimate-discover-a-new-digitized-world-of-management-support/, https://www.facebook.com/Bizzdesign, https://x.com/bizzdesign, https://www.linkedin.com/company/bizzdesign, https://twitter.com/bizzdesign, https://www.facebook.com/Bizzdesign, https://www.linkedin.com/company/bizzdesign, https://www.youtube.com/channel/UCw9zVU57XY5KMRk1RybCDhg]]"
published: 2022-05-09T12:41:18+00:00, https://www.facebook.com/Bizzdesign, https://x.com/bizzdesign, https://www.linkedin.com/company/bizzdesign, https://twitter.com/bizzdesign, https://www.facebook.com/Bizzdesign, https://www.linkedin.com/company/bizzdesign, https://www.youtube.com/channel/UCw9zVU57XY5KMRk1RybCDhg
created: 2024-09-24
description: Mapping between ServiceNow CSDM and ArchiMate gives you a full line of sight of your organization's strategic goals and infrastructure.
tags:
  - CSDM
  - ServiceNow
  - definition
  - CMDB
  - Configuration_Management
  - Modelling
  - Methods
  - ITSM
---
## Mapping between ServiceNow CSDM and ArchiMate. Bringing The Information of Both Platforms Together.

Bizzdesign recently launched an application for ServiceNow, titled [Bizzdesign Integration for ServiceNow](https://bizzdesign.com/solution/bizzdesign-integration-for-servicenow/), available in the [ServiceNow Store](https://store.servicenow.com/sn_appstore_store.do#!/store/home). In this blog post, we want to give you some more background.

As you can imagine, there are many use cases for the integration between a platform for IT service and asset management and operations (ServiceNow) and a platform for architecting and designing business change (Bizzdesign Horizzon). Bringing together the information from both platforms provides you with a full line of sight between the strategic goals of your enterprise, via its business capabilities, value streams, processes, and organizational makeup, to its application and technology landscapes, data created and used, and other dependencies.

You need to manage the full lifecycle of all these elements from when they’re first conceived (via their architecture and design and their delivery and operation) to their eventual retirement or replacement. You need to do all of this in a constantly changing environment and using agile working methods. This requires live insights of relevant information on design and operation and not some documentation after the fact.

Change leaders in any larger organization need such an integrated perspective. Without this, it’s impossible to manage complex transformations, prioritize future investments, or address risk effectively. For example, your enterprise’s digital transformation goes far beyond integrating application portfolio management with IT service management. Digital transformation touches everything from changing your business model, reinventing customer journeys, improving business processes, and implementing new cloud-native and mobile-first applications. At the same time, phasing out obsolete technology, managing cyber risk, and ensuring regulatory compliance. How can you decide on priorities in the design, realization, and operation of such a complex endeavor without having an integrated view?

To connect ServiceNow® Platforms with Bizzdesign Horizzon, users can create custom mappings between the data in both. To facilitate this, the Bizzdesign Integration for ServiceNow application provides out-of-the-box mapping between the ServiceNow [Common Service Data Model (CSDM)](https://www.servicenow.com/products/it-operations-management/what-is-csdm.html) and the [ArchiMate modeling language](https://www.opengroup.org/archimate-forum), which is an Open Group standard and lies at the heart of Bizzdesign’s platform. The CSDM is ServiceNow’s best practice for CMDB modeling, while ArchiMate is the international standard for enterprise architecture modeling.

Although the two metamodels have different backgrounds, they share a surprising number of concepts that facilitate ‘mapping’. Most importantly, both center on the notion of ‘service’. For ServiceNow’s CSDM this is perhaps not very surprising, but you may not know that ArchiMate is also firmly rooted in service thinking. Both even share a similar classification in business, application and technology (or technical) services.

We don’t want to take you through all the mappings between CSDM and ArchiMate, but just show you some highlights. For more detail, please read the forthcoming whitepaper from ServiceNow when it becomes available.  
The out-of-the-box mapping from CSDM to ArchiMate is as follows:

| CSDM Concept | ArchiMate Concept |
| --- | --- |
| Business Service | Business Service |
| Business Service Offering | Business Service |
| Service Portfolio | Business Service |
| Request Catalogue Item | Application Service |
| Application Service | Application Service |
| Technical Service | Application Service |
| Technical Service Offering | Application Service |
| SDLC Component | Artifact |
| Business Application | Application Component |
| Business Capability | Capability |
| Business Process | Business Process |
| Dynamic CI Group | Technology Collaboration |
| Application, Server, IoT, Network Gear | Node |
| Information Object | Data Object |
| Contract | Contract |
| Company | Business Actor |
| Business Unit | Business Actor |
| Department | Business Actor |
| Groups | Business Actor |
| Users | Business Actor |
| CMDB Group | Representation |
| Location | Location |
| CSDM Concept | ArchiMate Concept |

The ArchiMate mapping (above) uses the Business Service concept at three levels of aggregation (individual service, offering and portfolio). The same holds true for the concepts for the organization structure such as Company, Business Unit and Department: these all map to Business Actor. This is because ArchiMate, as a rule, uses the same concept at all aggregation levels; any fixed hierarchy would limit its usability for cases needing more or different levels.  
By using the Language Customization Mechanism described in the ArchiMate standard and supported by Bizzdesign Horizzon, you can define specializations of ArchiMate concepts. You could distinguish these aggregation levels using such specializations. These can have their own notation or use the default «stereotype» notation with guillemets.

The figure below shows a high-level overlay of the CSDM’s main concepts and corresponding ArchiMate elements (play to see the animation).

As we have seen, there are many similarities. However, we need to call out one difference between these two: the way they deal with relationships and, in particular, their direction. Most ArchiMate relationships point in the direction of delivery of some result, whereas CSDM’s are often defined as dependencies, pointing in the opposite direction. However, this is only relevant when you want to draw a diagram of your model since this direction is mainly a notational issue. To connect the two platforms, it’s enough that we can map the various relationships to an equivalent on the other side.

Of course, for your particular use case you may not need all these concepts. If, say, you are managing your current-state application portfolio in ServiceNow and want to use these applications in your baseline and target architecture models in Horizzon, you may only be interested in the elements that correspond with ArchiMate application layer concepts (in blue) in the figure above. If you are managing a service catalog in ServiceNow, the business service elements in the “Sell/Consume” box would be most relevant. And if you are interested in capability-based planning and want to investigate and plan how your applications and data support your business capabilities, the elements in the “Design” box top-right might be of interest.

Combining the strengths of these two market-leading platforms is more than 1 + 1 = 3. It opens new avenues into a fully digitized world of management support for digital enterprises. And who would want to keep managing this in an analog way?