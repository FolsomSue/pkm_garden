---
aliases: [Service Level Objective, Service-Level Objective, SLO]
---
#EA #Performance  #Metrics #ITSM #ITIL
A **Service-Level Objective** (**SLO**) is a key element of a service-level agreement (SLA) between a [service provider](https://en.wikipedia.org/wiki/Service_provider "Service provider") and a [customer](https://en.wikipedia.org/wiki/Customer "Customer"). SLOs are agreed upon as a means of measuring the performance of the Service Provider and are outlined as a way of avoiding disputes between the two parties based on misunderstanding.

## Overview\[[edit](https://en.wikipedia.org/w/index.php?title=Service-level_objective&action=edit&section=1 "Edit section: Overview")\]

There is often confusion in the use of SLAs and SLOs. The SLA is the entire agreement that specifies what service is to be provided, how it is supported, times, locations, costs, performance, and responsibilities of the parties involved. SLOs are specific measurable characteristics of the SLA such as availability, throughput, frequency, response time, or quality. These SLOs together are meant to define the expected service between the provider and the customer and vary depending on the service's urgency, resources, and budget. SLOs provide a quantitative means to define the level of service a customer can expect from a provider.[\[1\]](https://en.wikipedia.org/wiki/Service-level_objective#cite_note-:1-1)

The SLO may be composed of one or more [quality of service](https://en.wikipedia.org/wiki/Quality_of_service "Quality of service") (QoS) measurements ([service level indicators](https://en.wikipedia.org/wiki/Service_level_indicator "Service level indicator"), SLIs) that are combined to produce the SLO achievement value. As an example, an availability SLO may depend on multiple components, each of which may have a QoS availability measurement. The combination of QoS measures into an SLO achievement value will depend on the nature and architecture of the service.

## Examples\[[edit](https://en.wikipedia.org/w/index.php?title=Service-level_objective&action=edit&section=2 "Edit section: Examples")\]

Sturm and Morris argue [\[2\]](https://en.wikipedia.org/wiki/Service-level_objective#cite_note-2) that SLOs must be:

-   Attainable
-   Repeatable
-   Measurable
-   Understandable
-   Meaningful
-   Controllable
-   Affordable
-   Mutually acceptable

While Andrieux et al. define the SLO as "the quality of service aspect of the agreement. Syntactically, it is an assertion over the terms of the agreement as well as such qualities as date and time".[\[3\]](https://en.wikipedia.org/wiki/Service-level_objective#cite_note-:0-3) Keller and Ludwig more concisely define an SLO as "commitment to maintain a particular state of the service in a given period" with respect to the state of the SLA parameters.[\[4\]](https://en.wikipedia.org/wiki/Service-level_objective#cite_note-4) Keller and Ludwig go on to state that while service providers will most often be the lead entity in taking on SLOs there is no firm definition as such and any entity can be responsible for an SLO. Along with this an SLO can be broken down into a number of different components.

-   Obliged - The entity that is required to deliver the SLO.
-   Validity Period - The time in which the SLO will be delivered.
-   Expression - This is the actual language that defines what the SLO will be.

Optionally an EvaluationEvent maybe assigned to the SLO, an EvaluationEvent is defined as the measure by which the SLO will be checked to see if it's meeting the Expression.

SLOs should generally be specified in terms of an achievement value or service level, a target measurement, a measurement period, and where and how they are measured.[\[1\]](https://en.wikipedia.org/wiki/Service-level_objective#cite_note-:1-1) As an example, "90% of calls to the helpdesk should be answered in less than 20 seconds measured over a one-month period as reported by the [ACD system](https://en.wikipedia.org/wiki/Automatic_call_distributor "Automatic call distributor")". Results can be reported as a percent of time that the target answer time was achieved and then compared to the desired service level (90%).

| Type of Measure | Example SLO Requirement | Measurement Period |
| --- | --- | --- |
| Availability | The application will be available 99.95% of the time | Over a year |
| Service Desk Response | 75% of help desk calls will be answered in less than a minute
85% of help desk calls will be answered within two minutes

100% of help desk calls will be answered within three minutes

 | Over a month |
| Incident Response Time | 99% of severity 1 tickets will be resolved within three hours

98% of severity 2 tickets will be resolved within eight hours

98% of severity 3 tickets will be resolved within three business days

98% of severity 4 tickets will be resolved within five business days

 | Over a quarter |
| Response Time | 85% of TCP replies within 1.5 seconds of receiving a request

99.5% of TCP replies within 4 seconds of receiving a request

 | Over a month |

## Term usage\[[edit](https://en.wikipedia.org/w/index.php?title=Service-level_objective&action=edit&section=3 "Edit section: Term usage")\]

The SLO term is found in various scientific papers, for instance in the reference architecture of the SLA@SOI project,[\[5\]](https://en.wikipedia.org/wiki/Service-level_objective#cite_note-5) and it is used in the Open Grid Forum document on WS-Agreement.[\[3\]](https://en.wikipedia.org/wiki/Service-level_objective#cite_note-:0-3)

## References\[[edit](https://en.wikipedia.org/w/index.php?title=Service-level_objective&action=edit&section=4 "Edit section: References")\]

1.  ^ [Jump up to: _**a**_](https://en.wikipedia.org/wiki/Service-level_objective#cite_ref-:1_1-0) [_**b**_](https://en.wikipedia.org/wiki/Service-level_objective#cite_ref-:1_1-1) Rastegari, Yousef; Shams, Fereidoon (2015-12-29). ["Optimal Decomposition of Service Level Objectives into Policy Assertions"](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4709918). _The Scientific World Journal_. **2015**: 465074. [doi](https://en.wikipedia.org/wiki/Doi_(identifier) "Doi (identifier)"):[10.1155/2015/465074](https://doi.org/10.1155%2F2015%2F465074). [ISSN](https://en.wikipedia.org/wiki/ISSN_(identifier) "ISSN (identifier)") [2356-6140](https://www.worldcat.org/issn/2356-6140). [PMC](https://en.wikipedia.org/wiki/PMC_(identifier) "PMC (identifier)") [4709918](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4709918). [PMID](https://en.wikipedia.org/wiki/PMID_(identifier) "PMID (identifier)") [26962544](https://pubmed.ncbi.nlm.nih.gov/26962544).
2.  **[^](https://en.wikipedia.org/wiki/Service-level_objective#cite_ref-2 "Jump up")** Rick Sturm, Wayne Morris "Foundations of Service Level Management", April 2000, Pearson.
3.  ^ [Jump up to: _**a**_](https://en.wikipedia.org/wiki/Service-level_objective#cite_ref-:0_3-0) [_**b**_](https://en.wikipedia.org/wiki/Service-level_objective#cite_ref-:0_3-1) Alain Andrieux, Karl Czajkowski, Asit Dan, [Kate Keahey](https://en.wikipedia.org/wiki/Kate_Keahey "Kate Keahey"), Heiko Ludwig, Toshiyuki Nakata, Jim Pruyne, John Rofrano, Steve Tuecke, Ming Xu "Web Services Agreement Specification (WS-Agreement)", GFD-R-P.107, March 2007, Open Grid Forum.
4.  **[^](https://en.wikipedia.org/wiki/Service-level_objective#cite_ref-4 "Jump up")** Alexander Keller, Heiko Ludwig "The WSLA Framework: Specifying and Monitoring Service Level Agreements for Web Services", Journal of Network and Systems Management, Vol 11, n. 1, March 2003.
5.  **[^](https://en.wikipedia.org/wiki/Service-level_objective#cite_ref-5 "Jump up")** Jens Happe, Wolfgang Theilmann, Andrew Edmonds, and Keven T. Kearney "A Reference Architecture for Multi-Level SLA Management" in "Service Level Agreements for Cloud Computing", eds. Wieder, Philipp and Butler, Joe M. and Theilmann, Wolfgang and Yahyapour, Ramin, Springer New York, 2011, DOI:10.1007/978-1-4614-1614-2\_2