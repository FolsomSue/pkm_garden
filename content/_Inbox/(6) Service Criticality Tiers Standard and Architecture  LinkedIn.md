## Purpose and Introduction

The purpose is to provide a Service Tiering Standard based on the Service’s description, characteristics and outage impact as well as a standard for determining the corresponding treatment parameters of Performance, Availability & Recoverability; the corresponding Service Assurance Level or Service Level Agreement (SLA); and the corresponding Risk Tolerance & Acceptance parameters.

The Standard’s Model is based on abstracted definitions of “service” and "service tier" (with their associated "systems") then the model addresses the more concrete corresponding attribute/treatment "parameters" of the "Service (and associated systems) Tier" at each level (view) of the organization based on the viewpoint of the stakeholder at each of these levels.

The Terms RTO, RPO, HA, DR, and OR are defined and seeded - along with the "SLA" - within the attribute and treatment" parameters" at the appropriate Levels. Industry Best Practice values are given to these parameters.

The goal is to eliminate ambiguity and confusion around "what" and "why" a "service tier" is (the definition, description, outage impact & classification), as opposed to "how" it is treated by "who\[m\]" (the treatment & parameters of each stakeholder).

This Standard and Architecture will detail:

-   Service Tiers detailing Criticality, Description, Characteristics and Outage Impacts
-   Service Tiers corresponding Service Assurance SLAs parameters & Availability Requirements
-   A Guideline for assigning Risk Tolerance & Acceptance parameters for each Service Tier
-   Local High Availability (Operational Recovery/Component Resilience) and Remote High Availability (Disaster Recovery/Site Resilience) requirements & Guideline for Technical RTO & RPO for each Tier
-   Service Tiers System Layers Patterns for Resilience & Performance

## Service (and Associated Systems) Tiers Definitions

Four Service Tiers are identified for services and their related systems based on their criticality:

Tiers 1 & 2 represent Critical services/systems:

·        **Tier 1**: Mission Critical Services and their associated Systems

·        **Tier 2**: Business Critical Services and their associated Systems

Tiers 3 & 4 represent non-critical services/systems:

·        **Tier 3**: Business Operational Non-Critical Services and their associated Systems

·        **Tier 4**: Administrative Non-Critical Services and their associated Systems

### Definition of “Service”

In this standard a “Service” is defined as an abstracted functionality (or set of related functionalities \[functions and capabilities\]) _with associated roles, processes and tools (including IT Systems \[data, applications & infrastructure\])_ which has well-defined parameters of description, features, pricing, availability/recoverability, support; & management/ ownership as well as well-defined Operational &/or Service Assurance Levels (OLA &/or SLA) and which can be consumed by users &/or other services.

### Definition of “Service Tier”

In this Standard, a “Service Tier” is defined as a classification of the criticality of a group of services (and their associated IT systems) based on their characteristics & unavailability Impact to which the appropriate operational & service level agreements can be applied based on said characteristics & unavailability impact.

### Definition of “Mission Critical”

The term Mission Critical denotes primarily any services and/or systems that have a direct impact on the Organisation’s Core Mission and/or its Revenue (depending on organisation’s type of industry) and/or where the organisation’s customers are direct users of said services/systems.

### Definition of “Business Critical”

The term Business Critical denotes primarily any services and/or systems that, while not directly impacting the organisation’s mission/revenue, are direct enablers for other Mission Critical systems and hence may indirectly impact the organisation’s mission/revenue.

### Other Services defined as “Critical”

Other Services not strictly fitting the above definitions may be classified as Mission or Business Critical if their unavailability will cause a disruption to business operations that is deemed to be too severe for these services to be classified as non-critical. (e.g. internal email/unified communications services)

## Service Tiers Criticality, Availability & Service Level (SLA)

The following Diagram shows the Service (and systems) Tiers’ corresponding Service Criticality description, impacts; and Availability Uptime/Service Assurance Requirements:

![No alt text provided for this image](https://media.licdn.com/dms/image/C5612AQEGNWhiQHRN3g/article-inline_image-shrink_1500_2232/0/1585976304382?e=1725494400&v=beta&t=9pQwFxhXPowvlPXyXLNiT6QXO1EDlq7pAVruThk9kVI)

## Service Tiers Architecture

Service Tiers are consistent across all levels of the Enterprise based on their characteristics & Impact while only the “View” differs according to the viewpoint of the stakeholders at each level which is represented by different parameters for each Level & Tier:

·        Executive viewpoint parameters are Risk Tolerance, Acceptance and Controls

·        Business Owner viewpoint parameters are critical hours and planned outages

·        Architect/Designer viewpoint parameters are HA, OR, DR, and Technical RTO & RPO

·        Engineer/Operator of Service Delivery viewpoint parameters are SLA response time, resolution time, availability uptime, support hours and service RTO and RPO

·        The Enterprise User viewpoint parameters are the maximum work delay and productivity loss

The following diagram illustrates the Levels (Views) of the Service Criticality Tiers and their relevant parameters. Explanation & guidelines of the Risk, Availability & Recoverability Parameters are detailed in following sections:

![No alt text provided for this image](https://media.licdn.com/dms/image/C5612AQEUDGL2lTUy_A/article-inline_image-shrink_1500_2232/0/1585976570101?e=1725494400&v=beta&t=9Y7qB8wc-ghwcg3RjLEl1CeMp1nUXUXvE5GkK_krreM)

## Service Tiers and Risk Parameters

The Standard provides a guideline for assigning Risk Treatment parameters for the various “Risk Levels” for each Service Tier. Risk Levels (or Risk Zones) are the resultant combination of the Risk Impact and the Risk Likelihood.

### Risk Ratings

The following tables show the Four Risk Rating Levels (Zones), their derivation from the Impact and Likelihood values of Risk and the escalation parameters for each Risk Level:

![No alt text provided for this image](https://media.licdn.com/dms/image/C5612AQEsowINDuBu6w/article-inline_image-shrink_1500_2232/0/1585976682106?e=1725494400&v=beta&t=xNWKX0sw-a4fWYrIwEgX4lDgvIQsAiTz6PTvByxRpx8)

### Risk Tolerance, Acceptance and Controls

Risk Tolerance, Acceptance and Controls for Risks threatening the unavailability of Services (according to the Service Tiering model) are Enterprise Level Risk Parameters whose definition and Guidelines are as follows:

**<u>Risk Tolerance:</u>** Willingness of the organisation to accept a specified level (zone) of Risk without any further controls (i.e. without mitigation or treatment) – represented as a policy statement.

**<u>Risk Acceptance:</u>** How a risk is addressed within the tolerance policy and will include whether the risk should be:

·        **Accepted** (the risk does not require any further controls or direct activity at the current stage)

·        **Reduced** (the risk is beyond tolerance and should be reduced through additional controls)

·        **Shared** (the risk should be shared, either wholly or partly, such as through insurance)

·        **Avoided** (the risk is beyond tolerance and cannot be reduced enough by controls or sharing)

**<u>Risk Controls: </u>**  types of risk mitigation/treatment methods

·        **Directive:** A measure (such as a policy, guideline, standard, etc.) which outlines expectations (directing people how to act); e.g. a document directing staff how to properly perform a task, thus limiting risks.

·        **Preventative:** A measure designed to prevent a risk from occurring. Within systems, preventative controls are abundant (access controls, data types, user restrictions, encryption, etc.). Preventative controls are often abundant in IT environments. For instance, a login prevents unauthorised access to a system.

·        **Detective:** A measure designed to detect where a risk is occurring. Monitoring tools, reports, reviews, etc. are designed to detect where something is occurring which is not intended. These can be regular, ad hoc, and range in depth from extremely detailed reporting to high level dashboards. An example of a detective control is system log monitoring (to identify which users are actually accessing systems).

·        **Corrective** A measure designed to correct a risk, once an event has occurred. This could include clean-up processes, disciplinary processes, and other measures which deal with an identified event. An example of a corrective control is Malware quarantine after an intrusion and infection.

### Service Tiers Risk Levels’ Tolerance, Acceptance & Controls Guideline

The following diagram shows the Service Tiers guideline for the Risk Levels’ Tolerance, Acceptance & Controls:

![No alt text provided for this image](https://www.linkedin.com//:0)

## Service Tiers Systems Availability & Recoverability Parameters

The Availability & Recoverability Parameters below describe the “Technical” RTO & RPO for recovery of systems which will differ from and will usually be less than the Service Delivery Level SLA RTO & RPO values.

**RTO (\[Technical\] Recovery Time Objective)** is the time required to restore the system technically to an operational state after a system failure or disaster.

**RPO (\[Technical\] Recovery Point Objective)** is measured backwards from the time of failure (not from the time of recovery of service) and is the acceptable amount of data (in time units) to be lost before the time of system failure or disaster.

**High Availability \[HA\]:** The _concept_ of utilising resiliency measures in order to ensure that the service (& associated systems) can be recovered from a failure within the allowed time delay (RTO) & data loss (RPO) for its criticality tier. HA entails both Operational Recovery \[OR\] (component resilience) & Disaster Recovery \[DR\] (site resilience) Redundancy Mechanisms.

**Operational Recovery \[OR\] (Component Resilience / Local Recoverability):** The use of redundant system components & fault tolerance methods within the same site to achieve Recovery (Local Recoverability) from a component failure - usually with an RTO and RPO of <=30 minutes for critical services systems.

**Disaster Recovery \[DR\] (Site Resilience / Remote Recoverability):** The use of redundant system components in a separate secondary site to achieve recovery (Remote Recoverability) from a complete system failure or site, regional, or national disaster - usually with an RTO & RPO of <= 8 hours for critical services systems.

### Availability and Recoverability Parameters Guideline

This guideline refers to recovery from generalised modes of failure (i.e. failure of a system component, a complete system or a complete site failure in a disaster situation):

![No alt text provided for this image](https://www.linkedin.com//:0)

### Service Tiers System Resilience & Performance Measures Guiding Principles

The following principles ensure that a critical system is truly resilient by mandating resilience at each layer of the system (Network, Storage, Compute, OS, Data & Application) and not just in one or some of the layers. It emphasizes the requirement for at least one test environment that, in the case of Tier 1 systems, must match the production environment and that Tier 1 DR (remote site) system components must also be redundant.

1.      All systems must have at a minimum an Acceptance (Test) Non-Production Environment

2.      For Tier 1 systems, the Acceptance environment must exactly match the Production Environment

3.      For a system to be highly available, it must be resilient at every layer (redundancy at every system layer)

4.      For Critical Systems (Tier 1 & 2), all system layers must have OR and DR components

5.      For Tier 1 Systems, DR components in the Remote Site must also be redundant (OR Local Recoverability)

6.      For Critical Systems Data Layer, it is sufficient for HA purposes to have redundant clustered Database Mgmt. Systems (DBMS or DB servers) even when sharing a single Database Copy provided that:

a. The Data / Database is stored on a fault tolerant “Primary” Storage System (e.g. SAN, NAS)

b. and a separate DR data copy is available in a remote site and connected to a separate DR DBMS

7.      if supported by the application, Active/Active Resilience (Cluster/LB) is preferred over Active/Passive

8.      The Order of Preference for the Application Layer Resilience Method is as follows:

a. First preference: Native Application Level Clustering/Load Balancing

b. Second Preference: Network Level Load Balancing/Load Sharing

c. Third Preference: Operating System (OS) Level Clustering

9.      For Tier 2 & 3, Local Redundancy may be combined with Remote Redundancy (combined OR & DR) provided that:

a. Two separate copies of Data exist – one at each site

b. The resilience mechanism supports automatic failover across the two sites

c. The cross-site failover technical RTO & RPO are within the Service Tier’s Local OR RTO & RPO

The following Diagrams show the required measures of resilience and for each Service Tier at each System Layer:

![No alt text provided for this image](https://www.linkedin.com//:0)

![No alt text provided for this image](https://www.linkedin.com//:0)

## Conclusion

Proper criticality classification of the organisation's services (Service Tiering) is paramount and essential for the correct treatment and implementation of required resiliency (Availability/Recoverability), Service Assurance (SLAs) and risk mitigation (Controls) measures. The Service Tiering Standard is the foundation which most of the Enterprise Standards and Processes would reference for the purpose of prioritisation of resources and effort according to the Criticality Tier of each Service.