## Market Definition/Description

_Gartner defines data integration as the discipline comprising the architectural patterns, methodologies and tools that allow organizations to achieve consistent access and delivery of data across a wide spectrum of data sources and data types to meet the data consumption requirements of business applications and end users. Data integration tools enable organizations to access, integrate, transform, process and move data spanning various endpoints and across any infrastructure to support their data integration use cases._

The market for data integration tools includes vendors that offer a stand-alone software product (or products) to enable the construction and implementation of data access and data delivery infrastructure for a variety of data integration **use cases.**

These include (but are not limited to):

-   **Data engineering:** The usage of data integration tool capabilities to engineer data pipelines in support of various analytical use cases such as data warehouse, data lakes, data science and machine learning. We are not referring to data engineering as a practice here.
    
-   **Cloud data integration****:** Migrating and modernizing data workloads in the public cloud with an architecture that spans on-premises and one or more cloud ecosystems (hybrid/multicloud) to enable an optimal use of cloud resources.
    
-   **Operational data integration:** Supporting operational/transactional data integration use cases such as master data management (MDM), interenterprise data acquisition and sharing, B2B data sharing, synchronizing data related to critical business processes, and supporting data governance initiatives.
    
-   **Data fabric:** Data integration capabilities delivered in support of use cases related to the emerging data fabric design. This includes the ability to enable faster access to trusted data across distributed landscapes by utilizing active metadata, semantics and ML capabilities.
    

The core capabilities are functional requirements that each evaluated data integration tool vendor must support to be included in this research.

These include:

-   **Data movement topology:** Uni-/bi-/multi-directional movement of data across endpoints (e.g., synchronize, compare, broadcast, consolidate) via physical and virtual modes, meeting batch/microbatch/real-time latency requirements for data integration.
    
-   **Data virtualization:** Executing distributed queries against disparate data sources that are virtually integrated. This requires adapters to data sources, a metadata repository and a distributed query engine that can provide results in various ways (e.g., API, JDBC) for downstream consumption.
    
-   **Stream data integration:** Processing data in motion (e.g., streams, events) and provisioning the in-stream data for downstream consumption, analysis or storage.
    
-   **API services:** Data-as-a-service enabled through API design capabilities to create and manage outbound API endpoints over existing data assets and handle inbound API consumption to ingest internal and external data.
    
-   **Complex data transformation:** Capabilities that ease complex data processing operations such as fixing outliers, sophisticated parsing (e.g., free-form text mining, telemetry logs, media mining), complex data modeling (e.g., automated data pipeline creation and data warehouse automation support) and creating reusable transformations.
    
-   **Augmented data integration:** Capabilities that improve and optimize data integration operations (e.g., self-healing schema drifts, autorecovery) using extensive use of metadata (e.g., usage data, transaction logs, system workloads) and prepackaged ML algorithms that can inform or automate the tasks to ingest, transform, combine and provision data.
    
-   **Data preparation:** The suitability of data integration tools to support a range of business roles (e.g., citizen integrators, business analysts) for self-service data integration. The emphasis is on empowering nontechnical staff using various techniques such as low-/no-code data blending, visual exploration and probabilistic matching.
    
-   **Integration portability:** Data flow design portability across infrastructure (on-premises, SaaS, cloud service provider, VPC, etc.), providing workload management capabilities in a clean, safe and portable runtime environment (e.g., through containerization).
    

The support capabilities consist of those features that support forward-looking use cases through differentiated functionality.

These include:

-   **Metadata support:** Capabilities that support the extensive use of metadata (e.g., usage metadata, transaction logs, system workloads) to automate/improve data integration tasks.
    
-   **Data governance support:** Capabilities that assist data governance mandates (e.g., data quality, data lineage) while handling data for meeting specific data integration use cases (e.g., MDM, data sharing)
    
-   **DataOps support:** Change management capabilities to support data and related artifacts (e.g., Git integration of data pipelines, data model management), automation (e.g., automated testing), orchestration of data delivery (e.g., CI/CD pipelines) with appropriate levels of security to improve the use and value of data.
    
-   **FinOps support:** Capabilities that enable data and analytics leaders to iteratively control spending, understand product performance and make choices regarding price-to-performance trade-offs, resulting in optimal allocation of resources in the cloud.
    

For a vendor to be included in this market, its data integration tools must be able support these use cases and capabilities **independent** of other vendor’s product offerings. Vendors that sell data integration technology as part of other solutions (such as analytics platforms, DBMSs, and packaged or SaaS applications) are not considered data integration tool vendors by Gartner.

**Our evaluation of data integration tools does not include open-source frameworks, general-purpose development platforms or programming interfaces. Such data integration frameworks or platforms that require heavy customization by developers to engineer them for specific data integration scenarios are excluded from this Magic Quadrant.**

Vendors evaluated in this Magic Quadrant offer at least one commercial off-the-shelf tool that is purpose-built for supporting all the listed data integration use cases in this report.

## Magic Quadrant

Figure 1: Magic Quadrant for Data Integration Tools

Source: Gartner (August 2022)

![The Magic Quadrant for Data Integration Tools shows 21 providers placed in either the Leaders, Challengers, Visionaries or Niche Players quadrant, as of August 2022. Providers are positioned based on ability to execute and completeness of vision.](https://www.gartner.com/resources/758100/758102/Figure_1_Magic_Quadrant_for_Data_Integration_Tools.png?reprintKey=1-2AV770DR)

### Vendors Added and Dropped

We review and adjust our inclusion criteria for Magic Quadrants as markets change. As a result of these adjustments, the mix of vendors in any Magic Quadrant may change over time. A vendor's appearance in a Magic Quadrant one year and not the next does not necessarily indicate that we have changed our opinion of that vendor. It may be a reflection of a change in the market and, therefore, changed evaluation criteria, or of a change of focus by that vendor.

#### Added

The following vendors are included in this Magic Quadrant as they met the inclusion criteria:

-   AWS
    
-   Hitachi Vantara
    
-   K2View
    
-   Palantir
    
-   Software AG (StreamSets)
    

#### Dropped

-   **Adeptia:** Adeptia is dropped from this year’s Magic Quadrant because the vendor positions itself as a citizen integration solution focused on self-service data access, integration and sharing. Adeptia did not share the required information to substantiate its ability to meet the latest inclusion criteria for this research (which includes and requires use cases beyond self-service data preparation and integration for citizen integrators).
    
-   **HVR:** Fivetran (already on this Magic Quadrant) acquired HVR in October 2021.
    

## Inclusion and Exclusion Criteria

The inclusion criteria represent the specific attributes that analysts believe are necessary. To qualify for inclusion, the vendor’s data integration tool (or tools) must offer at least one “stand-alone” product directly usable by the buyer. The vendors must offer a generally available software product that meets Gartner’s definition of a data integration tool. To use the product, customers should be able to procure the data integration tool as an independent offering and not as a part of some other offerings — such as another form of tool suite, an application or other technology solution — of which the data integration capabilities are an “embedded” subset.

The data integration tool (or tools) must demonstrate various data delivery styles (from the list below) and be flexible enough to combine these styles for delivering various customer use cases:

-   **Bulk/batch data movement:** Bulk and/or batch data extraction and delivery approaches (such as support for ETL/ELT) are used to consolidate data from distributed databases and formats. This capability draws on data from across systems and organizational boundaries and can play a role in all use cases in this research.
    
-   **Data virtualization:** Data virtualization executes queries against distributed data sources to create virtual, integrated views of data “in memory.” Virtual views require adapters to data sources, a metadata repository and a distributed query engine that can provide results in various ways for downstream consumption.
    
-   **Data replication:** Data replication implies a simple copy of data and schema from one location to another, always in a physical repository. Replication does not change the form, structure or content of the data it moves.
    
-   **Data synchronization:** Data synchronization focuses on establishing and maintaining consistency between two separate and independently managed create, read, update, delete (CRUD) instances of a shared, logically consistent data model for an operational data consistency use case. Synchronization also maintains and resolves instances of data collision, with the capability to establish embedded decision rules for resolving such collisions (using schema-drift-handling mechanisms and other means).
    
-   **Stream data integration:** This is the ability to address data integration requirements through interoperability with streams/events, including provisioning of data in-stream for enabling downstream consumption, analysis or storage.
    
-   **Data services orchestration:** This covers both message-oriented middleware and API services:
    
    -   This capability allows data integration tools to encapsulate data in messages that various applications can read. Data is exchanged in real time, often via message queues like Apache Kafka or by using message-oriented middleware such as Java Message Service (JMS), IBM MQ and RabbitMQ.
        
    -   This capability allows data as a service, enabled through API design and delivery capabilities, to create and manage outbound API endpoints over existing data assets, and to handle inbound API consumption to ingest internal and external data.
        

Beyond the data delivery styles called out in the list above, the data integration tools must exhibit the following capabilities to be included in this Magic Quadrant research:

-   **Range of connectors/adapters (sources and targets):** This includes native connectors to seamlessly access relational and nonrelational DBMS products, plus access to nonrelational legacy data structures, flat files, XML and message queues, cloud-based data asset types (including data of SaaS applications and cloud data stores), and streaming data. Preference is given to connectors that work out-of-the-box, as opposed to connectors that must be customized by end users.
    
-   **Data movement topology:** Uni-/bi-/multi-directional movement of data across endpoints (e.g., synchronize, compare, broadcast, consolidate) via physical and virtual modes, meeting batch/microbatch/real-time latency requirements.
    
-   **Complex data transformation support:** Capabilities that support complex data processing operations such as fixing outliers, sophisticated parsing (e.g., free-form text mining, telemetry logs, media mining), complex data modeling (e.g., automated data pipeline creation for Data Vault modeling) and creating reusable transformations.
    
-   **Augmented data integration support:** These capabilities improve and optimize data integration operations (such as self-healing schema drifts and autorecovery) using extensive use of metadata (for example, usage data, transaction logs and system workloads) and prepackaged ML algorithms that can inform or automate the tasks to ingest, transform, combine and provision data.
    
-   **Support for data preparation capabilities:** This is the usability of data integration tools both for data engineers and citizen integrators and their suitability to support a range of business roles (e.g., citizen integrators and business analysts) for self-service. The emphasis is on empowering nontechnical staff using various techniques such as low-/no-code data blending and visual exploration.
    
-   **Integration portability:** This is data flow design portability across the infrastructure (at on-premises, SaaS, CSP and virtual private cloud \[VPC\]), providing workload management capabilities in a clean, safe and portable runtime environment (like containerization).
    
-   **Metadata and data modeling support:** This includes automated metadata discovery (such as profiling new data sources for consistency with existing sources), lineage and impact analysis reporting, and the ability to synchronize metadata across multiple instances of the tool. It also involves an open metadata repository, including mechanisms for bidirectional sharing of metadata with other tools. Capabilities must be provided for extensive use of metadata (e.g., usage data, transaction logs, system workloads) to automate/improve data integration and operations tasks.
    
-   **Data governance and information stewardship support:** Capabilities that assist data governance mandates (e.g., data quality, data lineage) while handling data for meeting specific use cases (e.g., master data management, data sharing). This is the ability to import, export and directly access metadata with/and from data profiling, data quality tools and/or other data-governance-enabling technologies (such as MDM, information stewardship, metadata management and data catalog tooling). Accepting business and data management rule updates from data stewardship workflows and sharing data profiling information with such tools is highly desired. Capabilities that assist data governance mandates (such as data quality and data lineage) while handling data for meeting specific use cases (master data management, data sharing and so on) are also needed.
    
-   **DataOps support:** Change management capabilities to data and related artifacts (e.g., Git integration of data pipelines, data model management), automation (e.g., automated testing), orchestration of data delivery (e.g., CI/CD pipelines) with appropriate levels of security to improve the use and value of data.
    
-   **FinOps support:** Capabilities that enable D&A leaders to iteratively control spending, understand product performance and make choices regarding price-to-performance trade-offs, resulting in optimal allocation of resources in the cloud.
    
-   **Runtime platform support:** This is the ability to deploy and run data integration tools on multiple platforms including Windows, UNIX and/or Linux operating systems.
    
-   **Service enablement support:** This is the ability to deploy functionality as services, including manners in which functionality can be called via a web service interface.
    
-   **Support for the delivery of data integration functionality as cloud services:** This could be done through a hosted, containerized, PaaS, IaaS, or SaaS delivery mechanism. The ability to perform integration across a hybrid and possibly a multicloud and intercloud ecosystem is highly desired. The ability to deliver integration services via a PaaS delivery model is highly desired by customers.
    

In addition, vendors must satisfy the following quantitative requirements regarding their market penetration and customer base:

-   **Revenue or customer count:**
    
    -   **Either,** generate at least **$30 million in software revenue** from data integration tools in the calendar year 2021 — that is, from perpetual license with maintenance, or subscription with support (which would include payment only for data integration software), or through a consumption-based licensing model where the consumption metrics are being used only for the data integration software (on an annual basis).
        
    -   **Or,** maintain at least **450 subscription or maintenance paying customers** (where “customers” does not mean individual “user” license seats), for its data integration tools in **production.** (The number of downloads without license or maintenance revenue is informative, but not a qualifying piece of information.)
        
-   **Geography:** Have market presence in **at least three of the following regions** (regional market presence is defined as a minimum of 5% of the revenue of the verified production customer base, as well as the existence of dedicated sales offices or distribution partnerships in a specific region):
    
    -   North America (Canada, Mexico and the U.S.)
        
    -   Central and South America
        
    -   Europe (including Western Europe and Eastern Europe)
        
    -   Middle East and Africa (including North Africa)
        
    -   Asia/Pacific region (Including Japan)
        
-   **Market presence:** Demonstrated market presence will be assessed through internal Gartner search, external search engines, Gartner inquiry interest, technical press presence and activity in user groups. A relative lack of market presence could be determined as a reason to exclude a product/service offering.
    
-   Have a data integration tool service **generally available** as of midnight, U.S. Eastern Daylight Time on 2 April 2022. This includes any new functionality added to the service by the specified date. We do not consider beta, “early access,” “technology preview” or other not generally available functionality or services. Additionally:
    
    -   Any acquired product or service must have been acquired and offered by the acquiring vendor as of 2 April 2022. Acquisitions after this date were considered under their preacquisition identities, if appropriate, and are represented separately until the publication of the following year’s Magic Quadrant.
        

Vendors that focus on narrow use cases that are too specific for the broader data integration market were excluded. Certain vendor tools were excluded because:

-   They focused on only one horizontal data subject area — for example, the integration of customer-identifying data.
    
-   They focused on only a single vertical industry.
    
-   They served only their own internally managed data models and/or architectures (such as providing data integration tools that only ingest data to a single proprietary data repository). Or, they were used by a single data discovery/visualization, analytics/BI tool, data science/ML platform, or DBMS/data management solution for analytics, data lake management, data warehouse automation or cloud ecosystem vendor. These vendors use their data integration tools only to ingest/integrate data into their own repository or within the confinement of their own broader tool/platform or ecosystem.
    
-   They provided data integration as a capability embedded within their broader data management/analytics/data science platform but did not provide a stand-alone/independent or commercially off-the shelf generally available data integration tool product.
    
-   Vendors that only provide support for open-source platforms/frameworks or development platforms, which need to be heavily engineered/customized for specific data integration tasks/use cases and/or are specific to a single data integration/data delivery style (such as stream data integration only).
    
-   Vendors that provide adapters or drivers to various data and analytics sources and targets, thereby indirectly supporting data integration, but these vendors do not market a stand-alone data integration tool.
    
-   Vendors that only provide self-service data preparation tools for citizen integrators, power users, analysts and line-of-business (LOB) users, but these tools do not have the ability to physically move data or operationalize these self-service data flows and models into production through data movement, governance and sharing, if and when needed.
    

### Honorable Mentions

-   **Cambridge** **Semantics** is headquartered in Boston, Massachusetts, and offers Anzo Knowledge Graph Platform. Anzo simplifies the integration, modeling and blending of multirelationship data across silos into insight-rich knowledge graphs at enterprise scale. Users can manage their metadata in the Anzo platform by connecting to data sources and then mapping their relationships. Its ontology management enables users to describe their business concepts, map their data assets, deploy a knowledge graph and drive business decisions. It also provides deep data integration and unification for AI and ML models. There is a good adoption among enterprises toward data fabric use cases. At this time, we do not see sufficient demonstrable market presence from Cambridge Semantics as a stand-alone data integration product vendor, which is why it was not included on this year’s Magic Quadrant.
    
-   **CData** **Software** is headquartered in Chapel Hill, North Carolina, and offers products under three segments. Under the first segment of data connectivity, it provides CData Drivers and CData Connect Cloud, which have more than 3,000 product SKUs. A product SKU is a unique combination of a specific connector and the technology on which it is supported, such as a CData Salesforce Connector available for JDBC, ODBC, Python, Tableau or PowerBI. CData Connect Cloud provides a library of connectivity via a “Data Connectivity as a Service” cloud offering built for business users. Under the second segment of data integration, it provides CData Sync and CData DBAmp. The former is a log-based change data capture product supporting more than 100 data sources, while the latter is a specialist product supporting Salesforce to SQL Server integration. Under the third segment of application integration, it provides CData Arc, which supports multiple communication protocols for B2B integration for secure Electronic Data Interexchange (EDI), Managed File Transfer (MFT) and APIs. At this time, we do not see sufficient demonstrable market presence from CData Software as a stand-alone data integration product vendor, which is why it was not included on this year’s Magic Quadrant.
    
-   **Confluent** is headquartered in Mountain View, California, and offers Confluent Cloud and Confluent Platform as its data integration tools. Confluent Cloud is a fully managed, serverless, and cloud-native service for Apache Kafka. Confluent Platform is a self-managed Kafka distribution. Both products are used for enabling stream data integration and stream analytics, both through Kafka and through a portfolio of tools designed to work with Kafka. Many organizations are using Kafka for streaming, messaging and event-based data integration scenarios. Despite its popularity, organizations struggle to maintain Apache Kafka deployments on their own, which can be operationally burdensome. Kafka does not provide full support for all data integration capabilities (such as orchestration, security and governance) and does not have a schema registry for metadata. Confluent helps address these gaps. Confluent is currently a very popular choice for customers looking to support stream data integration, but was excluded from this year’s Magic Quadrant evaluation because it does not provide some essential functions including data virtualization, augmented data integration or data preparation.
    
-   **Data Virtuality** is headquartered in Leipzig, Germany, and offers the Data Virtuality Platform and Pipes as its data integration tools. Data Virtuality uses data virtualization to create a unified semantic layer that helps users access data, even when the data is stored in different locations. The Data Virtuality Platform combines both data virtualization and ETL/ELT, providing flexibility depending on the requirements. Customers connect their data sources to the Data Virtuality Platform, create a data logic to map the connections, and then deliver data to the data targets. Common use cases include real-time data access, creating a logical data warehouse, data federation, data governance, GDPR compliance and creating a self-service semantic layer. Data Virtuality also provides a simplified version of its platform, which is called “Pipes,” that is a “data loader” tool that is used for data ingestion and replication. Organizations can use Pipes to load data into a cloud data warehouse. Data Virtuality was excluded from this year’s Magic Quadrant because it did not exhibit enough market presence (see our Inclusion Criteria section). Also, Gartner did not see Data Virtuality in a significant number of competitive situations for use-case scenarios not involving data virtualization.
    
-   **DataStreams** is headquartered in South Korea and provides the TeraONE Data Fabric platform, which provides capabilities for data integration, data governance and database management. It also provides stand-alone products for specific data integration patterns, such as TeraStream for batch data processing, TeraStream BASS for streaming ETL, DeltaStream for CDC, TeraONE for Data Lake and TeraONE Super Query for data virtualization. Although data governance is the biggest use case with its IRUDA platform, it supports analytical use cases as well through its own visualization tools, SuperVisual and TeraONE Idea, and through partnerships with Tableau, Qlik and others. At this time, DataStreams does not meet our inclusion criteria for market presence, and therefore was not included in the Magic Quadrant this year.
    
-   **dbt****Labs** is headquartered in Philadelphia, Pennsylvania, and offers dbt (data build tool) to transform data within data warehouses. Started as an internal productivity tool at Fishtown Analytics (a service company then), it has become dbtLabs (a product company now). It focuses on simplifying the transformation tasks within ELT use cases. It uses DataOps principles to drive velocity including CI/CD deployment practices and test-driven-development (TDD) frameworks to cut down on unmanaged code. Developers use dbt to express a piece of business logic and manage the end-to-end data pipeline process from development to production. There is a wide adoption of the tool among enterprises and a rapidly growing community of users. However, it did not meet the inclusion criteria on support for core capabilities including data movement topology (does not provide data ingestion) and streaming data integration capabilities.
    
-   **eQ Technologic** is headquartered in Costa Mesa, California, and provides the eQube Data as a Service (eQube-DaaS) platform. eQube-DaaS is closely aligned to the data fabric design and offers a low-code/no-code integration platform that supports multiple data integration techniques (through embedded support for batch, streaming, messaging, API-based delivery, data virtualization and application integration). The eQube-DaaS platform is made up of three loosely coupled offerings: eQube-MI (for data integration and data migration use cases), eQube-AG (for application integration and API gateway) and eQube-TM (for data model management and data transformation maps). eQube’s data virtualization service is integrated as part of the eQube-DaaS platform and plays a critical role in offering data as a service. Asset-heavy industries (including aerospace and defense, auto and machinery, energy, shipbuilding and high tech) looking to establish a data fabric design for use cases including enterprise search, common data model, API creation, synchronization of multiproduct life cycle management (multi-PLM) systems and their data with popular ERP systems (like SAP) will benefit from eQube’s native integration support for industrial applications and IoT systems. Although eQube-DaaS did offer all the data integration capabilities for this market, it did not make the inclusion criteria related to market execution for this year’s Magic Quadrant.
    
-   **Google** is headquartered in Mountain View, California, and provides a comprehensive set of data integration capabilities as part of its data management portfolio. Its Google Cloud Platform (GCP) offers Cloud Data Fusion, which is a fully managed and cloud-native data integration service that delivers ETL/ELT capabilities. Additionally, Cloud Data Fusion also supports a low-code data preparation environment for self-service data transformation by citizen integrators. GCP also offers a data replication service, Datastream, that delivers a log-based CDC capability to support real-time data movement to BigQuery (GCPs data warehouse), and other GCP databases including CloudSQL, Spanner, Bigtable and Firestore. For message-oriented data movement, Google offers the Pub/Sub integration service, and for customers looking to support IoT data ingestion and streaming analytics use cases, Google offers the Cloud Dataflow service. GCP has also added an orchestration service called Cloud Composer that supports data orchestration and life cycle management. Finally, GCP offers Dataplex, which centrally manages and governs data across all these GCP offerings. Although GCP offers comprehensive data integration services to support all use cases, it did not meet our inclusion criteria on market presence (specifically due to the low number of Gartner client inquiries mentioning GCP in support of stand-alone data integration use cases).
    
-   **Nexla** is headquartered in San Mateo, California, and offers the Unified Data Operations platform. This platform provides a low-code/-no-code, automation-based approach for diverse roles (such as data analysts, data engineers, business ops teams and data scientists) to achieve self-service data integration, preparation, monitoring and delivery. At the heart of the platform are Data Connectors and Data Products (Nexsets), which can be autogenerated or manually created for user collaboration. Nexsets are logical entities that contain metadata related to datasets, data transformations, data access controls, data errors and alert configurations, to help accelerate and standardize data sharing and collaboration within an organization. Connecting Nexsets with different data systems generates ETL/ELT integration, streaming data integration, API integration, data APIs and more. At this time, Nexla does not meet our inclusion criteria for market presence, despite having a technically sound offering, and was therefore not included in the Magic Quadrant this year.
    
-   **Striim** is headquartered in Palo Alto, California, and offers Striim Platform and Striim Cloud as its data integration tools. Striim Cloud is a unified stream data integration and stream analytics solution that operates as a fully managed service. Striim Platform offers a self-hosted version of the same core software that can be deployed either in the cloud or on-premises. While other stream data integration tools mainly focus on data ingestion, with limited support for transformation, Striim is able to provide full support for stream data ingestion and integration, so it can be used for in-flight transformation, real-time enrichment and stream analytics. Customers praise Striim’s log-based change data capture (CDC) capabilities, which are commonly used to stream data from on-premises and disparate cloud environments to cloud targets. In addition, Striim provides data delivery validation, metadata management, pipeline monitoring, event preview, and alerts, for continuous monitoring to ensure business SLAs and SLOs for real-time data delivery. Striim was excluded from this year’s Magic Quadrant because it did not meet the inclusion criteria for revenue/customer count threshold or market presence.
    

## Evaluation Criteria

### Ability to Execute

Gartner analysts evaluate providers on the quality and efficacy of the processes, methods or procedures that enable IT provider performance to be competitive, efficient and effective, and to positively impact revenue, retention and reputation within Gartner’s view of the market.

In this research, we evaluate the vendors’ ability to execute in the data integration tool market by using the following criteria.

### Product/Service

These are core goods and services that compete in and/or serve the defined market. This includes current product and service capabilities, quality, feature sets and skills. This can be offered natively or through OEM agreements/partnerships as defined in the market definition and detailed in the subcriteria.

We rated the vendors on:

-   The vendors’ capabilities that address current market requirements. These include but are not limited to bulk/batch data movement, CDC-based data replication and synchronization, data services orchestration, stream data integration for real-time use cases, data migration support, support for data engineering for analytics and data science, and other integration efforts for operational use cases (like MDM).
    
-   The degree of openness of the vendor technology and product strategy — that is, the ability to exchange metadata with third-party offerings.
    
-   The ability of offerings to allow interoperability to open-source solutions and third-party offerings. Some consumers are prepared to accept products from many different suppliers and assemble them together on their own. Interoperability is therefore appreciated by end users.
    
-   Connectivity options to not only nonrelational databases, cloud applications and cloud data stores (such as cloud object stores and cloud data warehouses), but also traditional stores (including relational databases and enterprise applications).
    
-   Connecting data integration activities to data quality and governance becomes integral in supporting those operational data integration use cases that require sharing high-quality data along with its lineage, such as master data management and B2B data sharing.
    
-   The ability to offer both serverless metered pricing options (for net new use cases) and traditional pricing models such as node-/core-based models (when the use cases do not require flexibility of compute).
    
-   The ability to support DataOps and orchestration capabilities to enable agile pipeline delivery, management, operationalization and maintenance. CI/CD integration, support for Git and Jenkins, support for regression test/validation, support for data observability, support for schema drift handling and so forth are all expected.
    

### Overall Viability

Viability includes an assessment of the organization’s overall financial health, as well as the financial and practical success of the business unit. This criterion views the likelihood of the organization to continue to offer and invest in the product as well as the product position in the current portfolio.

We rated the vendors on:

-   The appropriateness of the vendor’s financial resources, the continuity of its people and its technological consistency and how that affects the practical success of the business unit or organization in generating business results.
    
-   The growth of the vendor’s product lines, ARRs, profitability and growth in new geographies/use cases.
    
-   Product/services growth in revenue to determine the vendor growth in the data integration software market.
    
-   Growth in high-momentum use cases such as cloud data integration. Revenue growth through cloud integration tools (iPaaS, SaaS, etc.).
    
-   Other metrics to determine financial viability and spend on R&D efforts to continue differentiation and growth in product lines.
    
-   Investment in skills, people and persona for product development, delivery and support. Retention and growth metrics — both are necessary.
    

### Sales Execution/Pricing

This measures the vendor’s capabilities in all presales activities and the structure that supports them. This includes deal management, pricing and negotiation, presales support, and the overall effectiveness of the sales channel.

We rated the vendors on:

-   The ability of vendors to offer modular solutions. Organizations increasingly seek “modularity” or the capability to isolate specific required functions in data integration that are then reflected in their implementation approach and cost allocation.
    
-   Ability to provide tools and capabilities through different pricing models appropriate by use cases, persona and environment is rated highly.
    
-   The ability of vendors to support buyers that are looking for new pricing metrics that abstracts them from the underlying metrics of cloud pricing. Buyers are looking for vendor options that support serverless metered pricing metrics that are a true reflection of the actual work done and that can separate compute from storage/infrastructure.
    
    -   Having said that, organizations are also wary that serverless metered pricing options that don’t consider good financial governance can soon get out of control. Gartner will be closely evaluating vendors on their ability to enforce financial governance metrics into their pricing models and licensing metrics.
        
-   On the ease with which customers can hold vendors accountable for agreed-upon SLAs. Buyers are evaluating ways through which they can hold vendors accountable for the promised SLAs (in terms of uptime, turnaround times to issues, bug fixes, migrations and so on). Providers must demonstrate ways through which customers can escalate and attain credits/discounts when SLAs are not met.
    
-   Finally, data management as a discipline needs to track, predict and preempt overall cost associated with cloud integration workloads. This is especially important as data and analytics teams are becoming distributed across various domains and are increasingly being placed in various lines of businesses. This makes it important for data management leaders to have the ability to associate the cost of running data integration workloads to the business value they provide. This can be done by analyzing performance and system metadata to best allocate processing capacity. Vendors will need to provide tools that can automate aspects of this through FinOps approaches.
    

### Market Responsiveness/Track Record

This measures vendors’ ability to respond, change direction, be flexible and achieve competitive success as opportunities develop, competitors act, customer needs evolve and market dynamics change. This criterion also considers the provider’s history of responsiveness to changing market demands.

We rated the vendors on:

-   We are looking for evidence on how the vendors “course-corrected” to changing buyer requirements in terms of use cases, upcoming capabilities, pricing models and support requirements.
    
    -   As an example, managed services options for maintaining data pipelines and handling schema drifts are in demand, particularly by business teams and citizen integrators. Providers that can enable these requests are therefore selected over others that are still focused on IT teams alone.
        
-   The requirements to enable data fabric designs are also increasing. We are looking for vendors that are adding features to enable more comprehensive data fabrics.
    
-   Even though solutions that provide low-code/no-code UIs are preferred, we are also getting requests from data engineering teams for tools that support custom coding and importing scripts created in languages such as R and Python for highly advanced transformations.
    
-   The market is also looking for vendors that can assist with moving away from environments that seem to have lost traction — for example, Hadoop — and toward modern sources and targets, such as cloud database platforms as a service and cloud applications.
    
-   Vendors that support using AI/ML to automate complex and repetitive data integration tasks such as data transformation, orchestration, parts of data modeling and data delivery are preferred.
    
-   Vendors that provide open ecosystems to support independent data integration (which does not depend on any cloud infrastructure specifically or a DBMS or a proprietary data exchange format or data storage format) are preferred.
    

### Marketing Execution

This is the clarity, quality, creativity and efficacy of delivering the organization’s message in order to influence the market, promote the brand, increase awareness of products and establish a positive identification in the minds of customers. This “mind share” can be driven by a combination of publicity, promotional activity, thought leadership, social media, referrals and sales activities.

We rated the vendors on:

-   Brand recall value has a high premium in a mature market like data integration.
    
-   Providers must develop a means of converting community “chatter” and excitement to support delivery and go-to-market campaigns.
    
-   The overall effectiveness of the vendor’s marketing efforts — which impact its mind share, market share and account penetration — is important.
    
-   The ability of the vendor to adapt to changing demands in the market by aligning its product message with new trends and end-user interests was part of the evaluation.
    
-   Suppliers need to be aware of emerging best practices for data management infrastructure and whether they and their customers can specifically benefit from specialized horizontal or vertical capabilities, geographically targeted approaches, or partner-supported implementation practices.
    
-   Ability of the vendor to support and become a part of open community channels for best practices sharing, sharing connectors/code/mappings/other assets or support open metadata sharing standards.
    
-   Finally, how the vendor is rated and perceived on community review and evaluation channels like the Gartner Peer Insights.
    

### Customer Experience

These services should enable customers to achieve anticipated results. Specifically, this includes quality supplier/buyer interactions, technical support and account support. This may also include ancillary tools, customer support programs, availability of user groups and service-level agreements.

We rated the vendors on:

-   We will evaluate the level of satisfaction expressed by customers with the vendor’s product support and professional services support.
    
-   We will also look at customers’ overall relationship with the vendor, the experience while upgrading software versions, the learning curve for new users given the training resources available, and customer perceptions of the value of the vendor’s data integration tools relative to cost and expectations.
    
-   We will evaluate the ability of the vendor to maintain parity between cloud and on-premises software and measure after-sales support, migration ease, ease of deployment and overall maintenance and support.
    
-   Customer feedback on the ability of their vendors to meet roadmap deliverables, technical knowledge sharing, skills enablement and augmentation, and training will all be evaluated.
    
-   We will look at various platforms for such data points including but not limited to our interactions with end users in inquiries, Peer Insights data, surveys, customer reference calls, touchpoints across various Gartner and external events, community chatter, and vendor briefing data.
    
-   The distinction between advanced use cases and “pedestrian” applications is becoming more pronounced. The evaluation this year is focused on separating success in “traditional” market delivery from success in “innovative” market delivery in reviewing the customer experience.
    

### Operations

This is the ability of the organization to meet goals and commitments. Factors include quality of the organizational structure, skills, experiences, programs, systems and other vehicles that enable the organization to operate effectively and efficiently.

We rated the vendors on:

-   Operations are not specifically differentiating to end-user markets, but product management consistency and support/maintenance practices add to the overall customer experience and to the stability of senior staff.
    
-   Suppliers need to demonstrate a new balance in their R&D allocation to ensure they are positioned for deployment with greater focus on active metadata, metadata management overall and semantic tiers.
    
-   Also, they must demonstrate that they can provide ongoing support for the massive bulk/batch data movement market and for other data delivery styles including replication, streaming, API, virtualization and messaging.
    
-   Partner programs, skills augmentation, improvements in support and services, training materials and programs, and delivery with external service providers are all important in this evaluation criteria.
    

### Table 1: Ability to Execute Evaluation Criteria

| Evaluation Criteria | Weighting |
| --- | --- |
| 
Product or Service

 | 

High

 |
| 

Overall Viability

 | 

High

 |
| 

Sales Execution/Pricing

 | 

High

 |
| 

Market Responsiveness/Record

 | 

Medium

 |
| 

Marketing Execution

 | 

Medium

 |
| 

Customer Experience

 | 

High

 |
| 

Operations

 | 

Low

 |
|  |

Source: Gartner (August 2022)

### Completeness of Vision

### Market Understanding

This is the ability to understand customer needs and translate them into products and services. Vendors that show a clear vision listen, understand customer demands, and shape or enhance market changes with their added vision.

We rated the vendors on:

-   The ability to formulate product vision around multicloud/intercloud and hybrid data integration capabilities. Also, how the vendors are participating in a cloud ecosystem
    
-   The ability to provide core data integration services including all kinds of data movement topologies, support for bulk/batch, streaming, replication, API, messaging and support for the interoperating and combining of these data delivery styles if needed.
    
-   The ability to provide “advisors” and other insights in design, development, deployment and management of integration services to support decision insights and decision automation.
    
-   The ability to automate and augment data integration design and delivery through active metadata analysis and recommendation engines.
    
-   The ability to provide business-user-friendly UIs through self-service data preparation modules and to allow skilled users to operationalize self-service findings and flows.
    
-   The ability to work with data services through API management and integration and to deliver application and data integration flows together if the use case demands it. Existing support for delivery capabilities through microservices is a plus.
    
-   The ability to contribute to data fabrics/mesh designs. We are looking for support for knowledge graphs, graph modeling, semantic modeling and enrichment, taxonomy to ontology mappings support, graph analysis, and graph query to support data fabrics. It would be interesting to view support for data product delivery through governance to distributed data product teams in domains.
    
-   Ability to showcase capabilities (and upcoming ones on the roadmap) to support DataOps for agile and automated delivery of data integration pipelines. We will look for capabilities that support agile data engineering practices.
    
-   Finally, the vision to support financial governance through plans for FinOps support and current capabilities to validate this.
    

### Marketing Strategy

This is the clear, differentiated messaging consistently communicated through social media, advertising, customer programs and positioning statements.

We rated the vendors on:

-   Ability to differentiate their offerings from various other categories in the market — for example, basic ingestion tools as well as integration tools supporting only open-source frameworks.
    
-   Clear messaging on trial/freemium to full enterprise offerings (with differentiators across each support/SLA level)
    
-   Good visibility into the product portfolio along with features across each separate tool — including possible overlaps, ways to buy, means to procure, support tiers and licensing — is now a must.
    
-   Ability to showcase a complex portfolio through clear differentiated messaging justifying purchase and clarifying use of each product/SKU.
    
-   Efforts and investments, with demonstrations, into partner programs, training programs, OEM/value-added reseller (VAR), other partnerships, cloud provider partnerships, SI partnerships and so on.
    
-   Demonstrated proof of expansion in training, certifications and availability of talent in the market (through partner programs, training and so on).
    

### Sales Strategy

This involves the strategy for selling and using the appropriate networks, including direct and indirect sales, marketing, service, and communication. This includes partners that extend the scope and depth of market reach, expertise, technologies, services and customer base.

We rated the vendors on:

-   Expansion in sales partner networks
    
-   Vendors’ ability to become a part of different cloud ecosystems as an independent data integration partner for the customer
    
-   Strategy to grow beyond existing markets, use cases, geographies, and core capabilities
    
-   Demonstrated evidence of improvement in communication of existing and upcoming tools/services
    
-   Affiliate partnerships
    
-   Growth through varying channels (OEMs, VAR, Sis, consulting companies, join go-to-market, partnerships with vendors in the data and analytics space, etc.)
    

### Offering (Product) Strategy

This is an approach to product development and delivery that emphasizes market differentiation, functionality, methodology and features as they map to current and future requirements.

We rated the vendors on:

-   Aligning existing tools and roadmaps with future market direction.
    
-   We are looking for tools that can deliver distributed data integration across on-premises, cloud, intercloud and edge ecosystems.
    
-   Tools must exhibit improvement in automation-oriented capabilities.
    
-   While advanced capabilities are needed, the tools must not drop existing and “traditional” requirements of data integration, including bulk/batch capabilities, supporting hybrid/on-premises sources and targets, supporting developers and so on.
    
-   There is now significant increased expectation on “active” metadata understanding, conversion, utilization and analysis:
    
-   This active metadata is used in profiling, machine learning, evaluation of assets and comparison with existing integration upon connection.
    
-   Self-correcting optimization in processes is now important and expected.
    
-   Utilizing metadata to assist in user “push” recommendations for new data assets — and to create semantic knowledge graphs to assist with data fabric design that enables a more consistent (and application-neutral) semantic model for integration — is considered a differentiator.
    
-   Given the requirement to support diverse environments for data, delivery models and platform-mix perspective, we assess vendors on the degree of openness of their technology and interoperability with other data and analytics tools.
    
-   We will assess vendors’ roadmap and existing capabilities to support interoperability (through open metadata exchange) with other tools (their own or third party)
    
-   We will also assess roadmaps to support DataOps and FinOps to support agile data engineering and cost optimization measures.
    
-   Finally, we will be looking out for a roadmap (through demonstrable evidence) that supports seamless on-premises to cloud migration of tools or version/system migration in general. This will include changes to tool pricing as well.
    

### Business Model

This is the design, logic and execution of the organization’s business proposition to achieve continued success.

We rated the vendors on:

-   The overall approach the vendor takes to execute on its strategy for the data integration tool market — including diversity of delivery models, packaging and pricing options, and partnerships — is important.
    
-   It is both expected and reasonable to assume that tightly targeted models for traditional delivery needs can cut delivery cost, increase adoption and deliver specific integration needs to end-user organizations.
    
-   The ability of the vendors to provide both “current” requirements through best-fit engineering tools versus future requirements through end-to-end platforms or best-of-breed options is a good measure of this category.
    
-   The business proposition must include the ability for end-user organizations to try before they buy, and the tools must be able to interoperate with existing tools within the customer base rather than having to replace all current software.
    
-   We will be looking out for vendors to create a niche for themselves in this complex market. How vendors carve out differentiation, land-expand, grow and target specific differentiated use cases, persona, delivery models and even operating models is evaluated.
    

### Vertical/Industry Strategy

The strategy to direct resources (sales, product and development), skills and products to meet the specific needs of individual market segments, including verticals.

We rated the vendors on:

-   We look at the degree of emphasis the vendor places on vertical solutions and the vendor’s depth of vertical market expertise.
    
-   Although most prospects are not looking for data integration tools focused on a specific vertical/domain because they rightly treat data integration as industry-agnostic, some organizations might favor tools that are able to create a specific industry model, ontology or knowledge graph based on an industry-specific taxonomy.
    
-   Vertical/domain specific solution accelerators, KPIs, best practices and other industry starter templates might be favored by some buyers as well, in addition to industry/domain experts being a part of the professional services provided.
    
-   The vendors’ ability to provide vertical knowledge and expertise in presales, sales, implementation and support for targeted verticals is evaluated in this section.
    

### Innovation

This is direct, related, complementary and synergistic layouts of resources, expertise or capital for investment, consolidation, defensive or preemptive purposes.

We rated the vendors on:

-   The current innovation demands in the market are centered on managing location-agnostic capability in data integration — that is, the ability to not have to move or replicate data necessarily but to connect to data in-place when feasible and take the processing to the data (rather than vice versa) to execute integration.
    
-   Integration should run on-premises and in the cloud, and switch between them.
    
-   As data becomes highly distributed, data integration activities are also required to become easily distributable to any data location, and vendors should be able to recommend/determine when data needs to be moved for optimal processing and deliver workloads to the most optimal execution engines through containerized services and microservices architecture.
    
-   Converging data and application integration approaches is now expected.
    
-   ML-based automation using internal analytics on all kinds of collected metadata to support integration activities is another area of improvement that the market currently demands.
    
-   The growing diversity of users indicates a much higher demand for administrative, auditing, monitoring and even governance controls that utilize job audit statistics.
    
-   Graph analysis to determine user classification and optimization “hints” are also increasingly demanded.
    
-   Provide support for financial governance to enable business units, CDOs and CFOs to support cost optimization as workloads move to the cloud.
    
-   Finally, because the increase in the number of data pipelines is inevitable, organizations are expecting DataOps-oriented capabilities that can support CI/CD; project management capabilities such as Git and Jenkins; automated testing/validation; the handling of various environments in an agile manner; sandboxes on demand and management of them; and agile pipelines creation, reuse, execution, management and so on.
    

### Geographic Strategy

The provider’s strategy is to direct resources, skills and offerings to meet the specific needs of geographies outside the “home” or native geography — either directly or through partners, channels and subsidiaries — as appropriate for that geography and market.

We rated the vendors on:

-   The ability for vendors to provide their customers with local support with differing levels of confidence in the various approaches possible (that is, VARs, resellers, channel partners, OEM offerings and distributors).
    
-   The ability to provide continuity of support across regions.
    
-   The ability for development platforms to monitor where data originates with jurisdictional cognizance, and where it is eventually delivered.
    
-   Their ability to address the possible violation of national laws due to data movement.
    
-   The vendor’s strategy for expanding into markets beyond its home region/country and its approach to achieving global presence (for example, direct local presence and use of resellers/distributors) are crucial for capitalizing on global demands for data integration capabilities and expertise.
    
-   Level and performance of support in different geographies and skills availability to support after sales maintenance, etc.
    

### Table 2: Completeness of Vision Evaluation Criteria

| Evaluation Criteria | Weighting |
| --- | --- |
| 
Market Understanding

 | 

High

 |
| 

Marketing Strategy

 | 

High

 |
| 

Sales Strategy

 | 

Medium

 |
| 

Offering (Product) Strategy

 | 

High

 |
| 

Business Model

 | 

Medium

 |
| 

Vertical/Industry Strategy

 | 

Low

 |
| 

Innovation

 | 

High

 |
| 

Geographic Strategy

 | 

Medium

 |
|  |

Source: Gartner (August 2022)

### Quadrant Descriptions

#### Leaders

Leaders are front-runners in their capability to support the combination of different data delivery styles (for example, the ability to combine and switch between ETL/ELT, replication, messaging, API integration and data virtualization based on their use-case demands).

Leaders exhibit significant market mind share and recognize the need for new and emerging market demands — often providing new functional capabilities in their products ahead of demand — by identifying new types of business problems to which data integration tools can bring significant value. Leaders have an established market presence, significant size and a multinational presence.

In 2022, Leaders in this market have started delivering on the data fabric promise — that is, their ability to balance collecting data with connecting to data. They automate the process of collecting all types of metadata (not just passive) and then represent the metadata in a graph to preserve context. This is then followed by improving the data modeling process by enriching the models with agreed-upon semantics. Finally, some vendors embed AI/ML toolkits, which utilize active metadata (as input) to start automating various aspects of data integration design and delivery. Most vendors in the Leaders quadrant provide capabilities to deliver the data fabric, although some require customization.

Leaders are adept at providing tools that can support both hybrid integration and multicloud integration options, bridging the data silos that exist across on-premises and multicloud ecosystems. Leaders allow organizations to remain independent in data integration as they look to deploy workloads across multiple CSPs, and they allow organizations to effectively provision cloud ecosystems.

Leaders provide efficient data engineering through self-service data preparation capabilities and integration portability. They also provide the ability to deliver pipelines and code through containerized services. Leaders identify the need for financial governance, especially for integration workloads running in the cloud and support needs to balance flexibility with cost optimization.

Leaders are strong in establishing their data integration tools to support both traditional and new data integration patterns to capitalize on market demand.

#### Challengers

Bulk/batch delivery styles (such as replication, streaming or data virtualization) are no longer differentiating but a “must have” feature. As such, this capability is now considered under execution rather than vision. In line with this market shift, Challengers have been making significant strides in delivering these capabilities within a broader metadata-driven data integration toolset.

In 2022, the Challengers listed in this research exhibit a strong understanding of the current data integration market demand and exhibit both the credibility and viability to deliver. Some Challengers are mature in specific core capabilities, which enables them to deliver targeted use cases faster and with a better overall TCO than other vendors. These vendors have developed best practices for leveraging their strongest product capability in new delivery models. For example, they can productize and market (1) data replication as a key strength for targeted use cases such as cloud data migration, data warehouse automation and data lake enablement or (2) data virtualization for faster turnaround time to analytics or (3) extensive support for moving data and workloads from nonrelational DBMSs such as Hadoop to cloud data warehouses or cloud data lakes.

Challengers generally have substantial customer bases. They exhibit strong market presence, although implementations may be of a single-project nature or reflect multiple projects of a single type — for example, predominantly data replication or application integration, or use cases specific to mainframe data, analytics/BI or data science. Gartner realizes that many customers have specialized demands for their most urgent or upcoming projects. We also recognize vendors in the Challengers quadrant that (if needed) can scale to support broader data integration use cases but can also customize their offerings for specific/traditional use cases, data types, data sources/targets, execution environments or specific CSPs.

Overall, the market is pushing Challengers to embrace the market vision of a data fabric, automated data integration and multicloud/hybrid data integration to deliver solutions that can automate various data integration tasks. These tasks include automated profiling, automation of repetitive transformations, data preparation (and the ability to use ML to automate self-service data preparation), performance optimization, query optimization, and movement of workloads to data stores and engines that are best suited for processing. Overall, this move toward enabling data fabric architectures with support for financial governance automation through FinOps is a key driver that will determine which Challengers can move into the Leaders quadrant next year.

#### Visionaries

Visionaries demonstrate a strong understanding of emerging technology and business trends or focus on a specific market need that is far outside of common practices, while also possessing capabilities that are expected to grow in demand. In 2022, the Visionaries in this Magic Quadrant have focused early on futuristic capabilities and go-to-market strategies to capitalize on their capacity to leverage:

• Augmented data integration through the data fabric design

• Representing data and metadata in business taxonomies and ontologies with support for semantic modeling

• The ability to provision a knowledge graph of data entities that represent multirelationship data in business context

• Serverless integration that supports a multicloud and hybrid cloud integration architecture

• The delivery of various data integration functionalities as loosely coupled API/microservices

• Seamless orchestration through DataOps techniques

• iPaaS delivery models led by the convergence of data integration, application integration and API integration/API management use cases

• Deliver data applications as data products and support federated governance.

In addition, a significant driver of vision is the ability of tools to connect to and analyze all forms of metadata — both passive and, increasingly, active metadata. With this, tools provide key statistics to developers and citizen integrators that aid with integration design and automation. Visionaries should lead the push toward the utilization of graphs, semantics, knowledge graphs and AI/ML for significant automation in data integration design, delivery and maintenance. Visionaries sometimes lack market mind share or credibility beyond their established customer base, their main use cases or very specific application domains/verticals. They may lack partnerships and (or) tight integrations with other incumbent data management vendors including third-party metadata management, data governance and data quality solutions. Visionaries could still be ramping up partnerships with system integrators, consulting companies and other partners that can ensure consistent support, implementation, training or after-sales support to their clients worldwide and beyond their main established markets. They may lack the installed base and global presence of larger vendors. Finally, Visionaries may be established players in related markets that have only recently placed an emphasis on data integration.

#### Niche Players

Because this is a mature market, Niche Players generally do not generally exhibit gaps in primary functionality or features. Instead, they are simply challenged to improve their execution or have not identified a specific market approach that expands use cases for their technology. This means that almost every Niche Player will be able to deliver against standard market expectations, both in functionality and cost/price options.

Niche Players may not appear very frequently in competitive situations for comprehensive and/or enterprise-class data integration deployments. Many have very strong offerings for a specific range of data integration problems — for example, a set of specific data delivery styles (batch, replication, streaming or virtual), application domains or use-case scenarios — and deliver substantial value for their customers in the associated segment. Niche Players often exhibit advantages in pricing in their small footprint and in vertical or horizontal solutions and can’t complement an organization’s other data management technologies. Niche Players are known for solving one part of the data integration problem well through a targeted solution and may be a “good enough” solution for organizations with less complex needs.

Importantly, Niche Players in this market have demonstrated their capability to outperform dozens of tool and solution offerings that were considered and eventually excluded from this Magic Quadrant, but may be lacking maturity on certain features that display market vision.

## Context

The market for data integration tools continues to evolve and is supported by strong levels of consolidation, strong revenue growth of 11.8% in 2021 (to reach $3.8 billion at the end of 2021) and rapid adoption. More data and analytics leaders are realizing that data integration is a critical component of their data management infrastructure. They understand that they need to employ data integration functions to share data across all organizational and systemic boundaries. Therefore, organizations are increasingly seeking a comprehensive range of improved data integration capabilities to modernize their data, analytics and application infrastructures.

Data and analytics leaders must navigate a market brimming with products that claim to solve a range of data integration problem types. However, not all vendor solutions have experience in, or evenly provide, all the relevant capabilities needed across our key data integration use cases (see the companion Critical Capabilities for Data Integration Tools). Some vendors focus heavily on providing solutions focused on just one data integration style such as bulk/batch (through ETL or ELT), data replication (through CDC), messaging (through Kafka), or virtual (through data virtualization). But they may place less emphasis on the important capability of interoperating, orchestrating or even combining these different data delivery styles (ETL with data virtualization or data replication or messaging through API integration, for example) for accomplishing key use cases.

Some organizations have determined that basic functions are adequate and are seeking tools with targeted capabilities. As a result, they are interested in tools that are specialists in one data delivery style (for example, data replication, data ingestion, API integration, self-service data preparation or data virtualization). Some organizations prefer tools that can support one use case (such as cloud data ingestion and migration), one data type (such as IoT data integration) or one scenario (such as location intelligence through geospatial data integration focus). Such organizations can confidently start with the vendors in the Niche Players.

Organizations that seek tools that are generalists and can support multiple use cases through a combination of different data integration styles should evaluate the vendors mentioned in the Challengers and Leaders quadrants.

In addition, vendors in the Leaders quadrant are focused on automating various aspects of data integration. These include design, ingestion, schema mapping, schema drift detection and corrections, dataOps automation, orchestration automation, next-best transforms, automated lineage and impact analysis, and infrastructure management. These capabilities for augmented data integration demand a new data integration design — one that supports a balance of connect and collect data integration strategies.

Active-metadata-enabled data integration augmentation is a significant driver of market vision this year. Metadata as a byproduct of the design and operations management of a data integration platform is a minimum requirement of data integration tools in 2022. Platforms and solutions are now expected to provide continuous feedback regarding the profiles, quality, location, performance optimization, lineage, use cases, access points, context, frequency of access and content analysis of integrated data assets. As far as architects and solution designers are concerned, this feedback was long overdue. It is expected that graph analytics, powered by every conceivable type of metadata, will provide the necessary data fabric designs for introducing ML capabilities into data integration platforms (see How to Activate Metadata to Enable a Composable Data Fabric). This capability for active-metadata-based integration has been weighted very highly to define the vision of the market this year by Gartner analysts.

Gartner sees that the need to acquire and integrate data across multiple CSPs, typically for hybrid cloud and intercloud integration, is becoming crucial to many data integration use cases. Vendors that support just one cloud provider (CSP) or only their own databases or applications will fall behind due to valid lock-in and CSP dependence concerns.

An interesting trend from our inquiries revealed that an increasingly high number of data and analytics leaders are investigating and adopting tools that can support data ingestion and replication. This increase is because organizations are looking to ingest or replicate the data from their operational DBMSs to cloud data warehouses. This has been a significant driver of growth for many data integration providers (such as Fivetran, Matillion, Qlik and Software AG \[StreamSets\]). These providers have formed significant partnerships with CSPs like AWS, GCP and Microsoft Azure, along with popular cloud data warehouse vendors such as Snowflake and Teradata, to deliver integrated data to cloud data warehouses and data lakes for analytics. This task is often termed as data warehouse automation and is seen as a differentiator by organizations evaluating tools.

This year, organizations have also started evaluating vendors for their ability to support integration portability and improve the ability to deliver integration flows, mappings, assets and pipelines in an agile and orchestrated manner. Support for DataOps has been rated as a significant driver for vision by our analyst team. This is in line with market demand to support infrastructure as code and to enable the ability to port integration pipelines for optimal executions to environments that best support the required SLAs. Organizations now expect vendors to deliver an increasing array of such capabilities embedded in solutions ranging from support for CI/CD and integration with Git and Jenkins to providing automated serverless execution capabilities. Support for open-source data transformation tools (like DBT), orchestration solutions (like Apache Airflow), and open-source ingestion capabilities using crowdsourced connectors (from vendors like Airbyte, for example) are a sign of vision for this edition of the Magic Quadrant.

For the first time, we have also started evaluating vendors on their ability to iteratively control spending, understand product performance, and help make choices regarding price-to-performance trade-offs, resulting in optimal allocation of resources in the cloud. This is what we are calling FinOps, and it’s vital to address the growing concerns of overspending, overbudgeting and cost optimization in the cloud.

As more and more subject matter experts become a part of data integration tasks, their needs should be better supported through native integration with self-service data preparation tools and modules. These modules should support less technically skilled personnel with low-code/no-code integration environments. This capability is now a must-have. Moreover, vendors must also support data engineers who are tasked with operationalizing self-service models to production environments after guaranteeing governance and compliance.

Finally, a mix of data integration approaches has remained crucial, spanning from physical delivery to virtualized delivery, and from bulk/batch movements to event-driven granular data propagation. When data is being constantly produced in massive quantities and is always in motion and constantly changing (for example, IoT platforms and data lakes), attempts to collect all this data are neither practical nor viable. This is driving an increase in demand for connection to data, not just the collection of it (see Assessing the Relevance of Data Virtualization in Modern Data Architectures). In 2022, data virtualization has again been a key criterion for evaluating vendors. In addition, we see a surge in demand for tools that can integrate “data in motion” through stream data integration technologies that provide native connectors to event data sources (like clickstreams, logs and IoT) and the ability to capture, enrich and deliver event data to data stores/applications for real-time analytics and other use cases (see Market Guide for Event Stream Processing).

## Market Overview

The data integration tools market continues to push toward distributed and augmented data management. This push is inherent in the modern data fabric architecture (see Data and Analytics Essentials: Data Fabric). _The market has realized that those data integration tools that do not balance “collect”- with “connect”-based data management architectures will always result in data silos and/or poorly integrated infrastructures._ Moving forward, organizations will need to monitor trends that are affecting enterprise requirements and vendor offerings. We highlight some of these below:

-   **Data integration market experiences double-digit growth:** The market grew at 11.8% in 2021 as compared with 6.8% in 2020 (see Market Share: Data Integration Software, Worldwide, 2021). The increased growth in this market is part of the broader trend of postpandemic recovery reflected in higher growth of software markets overall, as software growth increased from 9.0% in 2020 to 16.0% in 2021. This increased growth in 2021 for the data integration market is reflected in our updated forecasts for growth as well. Five-year compound annual growth rate (CAGR) for the 2021 to 2026 time frame forecast is now 8.5% (see Forecast: Enterprise Infrastructure Software, Worldwide, 2020-2026, 2Q22 Update), updated from 7.0% same time last year. Cloud adoption continues to be significant, with the iPaaS market growing by 40.2% in 2021.
    
-   **Market leaders continue to lose ground to smaller vendors:** The top five vendors in this market (based on their market share) had a collective market share of 71% in 2017. This number has been steadily dropping over the years, and in 2021, the collective market share was only 52%. A similar trend can be seen when analyzing the top three or even top 10 vendors. One of the main reasons for this is that market share leaders such as Informatica and Talend are ceding market share as they focus their growth efforts primarily on their iPaaS products. Another reason is that smaller vendors with more focused offerings (such as those targeted toward a specific data integration capability like data ingestion or data virtualization etc) continue to disrupt larger vendors with their land-and-expand strategies.
    
-   **Market growth is being driven by support for modern data delivery styles and cloud data ecosystems:** Vendors gaining market share have a common theme: They focus on leadership in specific data integration styles such as data virtualization or data replication, and/or they focus on data integration delivered as a native and managed cloud service. Some high-growth vendors in the first category are Denodo, Qlik, Software AG (StreamSets), Striim and Confluent. These vendors collectively grew their revenue by 32% in 2021. Some high-growth vendors in the second category are AWS, Fivetran, Google, Matillion and Microsoft. These vendors collectively grew their revenue by 94% in 2021. Although these growth numbers are off a much smaller revenue base, the gradual decline in market share for the larger and established vendors shows that they will need to find the right balance between all-encompassing platform solutions and easily accessible point solutions to keep pace (see Market Share Analysis: Data Integration Software, Worldwide, 2021). Some providers have focused on vendor acquisitions to gain maturity in specific data delivery styles in the last couple of years. The most prominent examples include Fivetran acquiring HVR Software (a log-based data replication vendor), Qlik acquiring Blendr.io (for application integration), Talend acquiring Gamma Soft (a log-based change data capture vendor) and TIBCO Software acquiring Information Builders (a batch ETL/ELT technology provider).
    
-   **Data fabric is critical and driven by the end-user push toward augmented data integration:** Another huge completeness of vision criterion that the market is demanding is augmented data integration design and delivery. The COVID-19 pandemic has only fast-tracked this strategic direction of the market. Data and analytics leaders are realizing that they cannot keep investing in manual data integration; they need automation support. Data integration teams (in terms of individual members) are constantly contracting — the median number of individuals in teams is less than 10 (based on anecdotal evidence from our inquiries). And while team sizes are reducing, the amount of data and, hence, the number of data integration requirements, are growing exponentially. This gap between demand and supply is pointing toward an urgent focus on automation and augmentation. Augmented data integration demands a renewed focus on the data fabric architecture design, which is a key use case for this year. The data fabric is an architecture pattern that informs and automates the design, integration and deployment of data objects. This approach results in faster, informed and, in some cases, completely automated data access and sharing. In 2021, some vendors have been able to combine most (if not all) of these capabilities needed to deliver the data fabric into productized solutions, which signifies leadership. Others are going in this direction through partnerships, merger and acquisition (M&A) activity, product enhancements and, more frequently, a combination of all these (see Quick Answer: What Is Data Fabric Design?).
    
-   **Data mesh starts gaining traction:** One of the key reasons why organizations investigate the data mesh design is that they require decentralized and domain-oriented data delivery of “data products.” This push is gathering pace because business teams believe that they are often left waiting for data engineering resource attention and that the data pipelines delivered by engineering teams do not do justice to their time-to-market SLAs. Business teams also request more data integration and modeling ownership to impart subject matter expertise into their data products through semantic modeling, ontology creation and knowledge graph support. As a result, organizations are actively evaluating data integration tools that can balance centralized data pipeline delivery with technical capabilities to provision decentralized data product delivery through capabilities such as data-as-a-service, DataOps-based CI/CD, infrastructure-as-code, GIT integration, scheduling and testing automation, and other agile capabilities to deliver data as a product to domains and business teams. See Data Fabric or Data Mesh: How to Decide Your Future Data Management Architecture.
    
-   **FinOps and financial governance are to be taken seriously for cost optimization in cloud data integration efforts:** This is the first time that Gartner is introducing FinOps as a key capability for evaluating vendors in this Magic Quadrant research. Data integration tools need to track, predict and preempt overall cost associated with cloud integration workloads as data and analytics teams get distributed across various domains and are being placed increasingly in various lines of businesses. This makes it important for data and analytics leaders to have the ability to associate cost of running data integration workloads to the value associated with them and have control over allocating processing capacity to workloads they deem to be important through optimal analysis of performance and system metadata and the ability to associate value to cost. Vendors will therefore need to provide tools that can enable financial governance and automate aspects of this through FinOps approaches that also reflect in their pricing models and governance models. FinOps for data integration comprises the capabilities that enable data and analytics leaders to iteratively control spending, understand product performance and make choices regarding price-to-performance trade-offs, resulting in optimal allocation of resources in the cloud for efficient cost optimization.
    

-   **Data engineering requirements are fueling the next round of investments:** Data engineering is the discipline of translating data into usable forms by building and operationalizing data pipelines across various data and analytics platforms. It goes beyond the traditional data management practices to include software engineering and infrastructure operations practices (see How to Build a Data Engineering Practice That Delivers Great Consumer Experiences). An example is using coding languages like Python and Scala to automate data pipeline builds, regression tests, deployments and operations monitoring. With more and more data infrastructure running on the cloud, platform operations are becoming a core part of data teams’ responsibilities. The market around data engineering is still emerging, and there are no set industrywide standards, which limits the use-case application. Data integration tools are stepping up to this need and providing various built-in capabilities to assist end-user customers. Therefore, organizations prefer those data integration tools that embed capabilities that assist data engineers to build, manage, operationalize and even retire data pipelines in an agile and trusted manner, as well as run their pipelines in various execution environments. Data integration tools that allow optimizing code and pipeline execution through pushdowns, containerizations and serverless execution are being preferred in competitive RFPs.
    
-   **DataOps needs to be supported:** Even though data integration tools don’t by themselves provide all capabilities necessary to deliver DataOps, they certainly support DataOps enablement. DataOps is not a single tool or process but is instead a focus on building collaborative workflows to make data delivery more predictable. For additional information, see Data and Analytics Essentials: DataOps. Those data integration tools that can support DataOps are naturally being favored over those that do not. Based on our inquiries with clients, key aspects being requested include the ability to deliver data pipelines through CI/CD. Organizations also request capabilities that support automated testing and validation of code. Leading tools also provide the ability to integrate their tools with project management and version-control tooling like GIT, Jenkins and Maven. Data engineering departments in end-user organizations prefer data integration tools that can help them balance the low-code capabilities (offered as part of the data integration tool) with options to invoke code developed in external Python libraries; in dbt (for complex transformation where manual coding is preferred); and in Apache Airflow, Luigi, Prefect, Dagster and so on for task workflow scheduling, for example. Some data integration tools also enable organizations to manage different nonproduction environments (such as sandbox, development and test/quality assurance \[QA\]) in an agile manner.
    
-   **Support for hybrid and intercloud data management is now critical:** Cloud architectures for data management span hybrid, multicloud and intercloud deployments. There are both risks and benefits in managing data across diverse and distributed deployment environments. Data location impacts performance, data sovereignty, application latency SLAs, high-availability and disaster recovery strategies, and financial models. Gartner estimates nearly half of data management implementations use both on-premises and cloud environments. Hybrid data management and integration support has therefore become pivotal in the market. Data integration tools are expected to dynamically construct or reconstruct integration infrastructure across a hybrid data management environment. Those tools that can support integrating data across different cloud infrastructures and synchronize it with on-premises data sources and targets have been given more vision scores in this year’s Magic Quadrant revision.
    
-   **Independent data integration tools are needed to prevent application/cloud service provider (CSP)/database lock-in:** There needs to be a clear focus on independent data integration tools that do not necessitate the movement and persistence of data into a specific vendor repository or cloud ecosystem. This is more important than ever because embedded data integration capabilities delivered by vendors as part of a broader application (such as analytics and BI or CRM tool) or database, or even CSP-specific data integration solutions, might make it easy for organizations to ingest data into one database, application or CSP ecosystem. However, these same embedded integration capabilities do very little to allow organizations to integrate data across different data stores, applications or multicloud/hybrid environments. This could lead to potential vendor lock-in challenges, high egress costs and data silos, resulting in the inability of organizations to reuse integrated data for general-purpose use cases. Although the CSP native data integration tools have started becoming more open in terms of allowing for two-way integration (to and from their own cloud data stores), those organizations that are looking to invest in a general-purpose (and independent) data integration tool for use cases involving more than one cloud service provider must favor independent data integration tools to partner with those provided by CSPs, DbPaaS or even their analytics/BI or data science vendors.
    

## Evidence

The analysis in this Magic Quadrant research is based on information from several sources, including:

-   An RFI process that engaged vendors in this market. It elicited extensive data on functional capabilities, customer base demographics, financial status, pricing and other quantitative attributes.
    
-   Interactive briefings in which vendors provided Gartner with updates on their strategy, market positioning, recent key developments and product roadmap.
    
-   Feedback about tools and vendors captured during conversations with users of Gartner’s client inquiry service.
    
-   Market share and revenue growth estimates developed by Gartner’s technology and service provider team. Peer feedback from Gartner Peer Insights, comprising peer-driven ratings and reviews for enterprise IT solutions and services covering more than 300 technology markets and 3,000 vendors.
    

## Evaluation Criteria Definitions

### Ability to Execute

**Product/Service:** Core goods and services offered by the vendor for the defined market. This includes current product/service capabilities, quality, feature sets, skills and so on, whether offered natively or through OEM agreements/partnerships as defined in the market definition and detailed in the subcriteria.

**Overall Viability:** Viability includes an assessment of the overall organization's financial health, the financial and practical success of the business unit, and the likelihood that the individual business unit will continue investing in the product, will continue offering the product and will advance the state of the art within the organization's portfolio of products.

**Sales Execution/Pricing:** The vendor's capabilities in all presales activities and the structure that supports them. This includes deal management, pricing and negotiation, presales support, and the overall effectiveness of the sales channel.

**Market Responsiveness/Record:** Ability to respond, change direction, be flexible and achieve competitive success as opportunities develop, competitors act, customer needs evolve and market dynamics change. This criterion also considers the vendor's history of responsiveness.

**Marketing Execution:** The clarity, quality, creativity and efficacy of programs designed to deliver the organization's message to influence the market, promote the brand and business, increase awareness of the products, and establish a positive identification with the product/brand and organization in the minds of buyers. This "mind share" can be driven by a combination of publicity, promotional initiatives, thought leadership, word of mouth and sales activities.

**Customer Experience:** Relationships, products and services/programs that enable clients to be successful with the products evaluated. Specifically, this includes the ways customers receive technical support or account support. This can also include ancillary tools, customer support programs (and the quality thereof), availability of user groups, service-level agreements and so on.

**Operations:** The ability of the organization to meet its goals and commitments. Factors include the quality of the organizational structure, including skills, experiences, programs, systems and other vehicles that enable the organization to operate effectively and efficiently on an ongoing basis.

### Completeness of Vision

**Market Understanding:** Ability of the vendor to understand buyers' wants and needs and to translate those into products and services. Vendors that show the highest degree of vision listen to and understand buyers' wants and needs, and can shape or enhance those with their added vision.

**Marketing Strategy:** A clear, differentiated set of messages consistently communicated throughout the organization and externalized through the website, advertising, customer programs and positioning statements.

**Sales Strategy:** The strategy for selling products that uses the appropriate network of direct and indirect sales, marketing, service, and communication affiliates that extend the scope and depth of market reach, skills, expertise, technologies, services and the customer base.

**Offering (Product) Strategy:** The vendor's approach to product development and delivery that emphasizes differentiation, functionality, methodology and feature sets as they map to current and future requirements.

**Business Model:** The soundness and logic of the vendor's underlying business proposition.

**Vertical/Industry Strategy:** The vendor's strategy to direct resources, skills and offerings to meet the specific needs of individual market segments, including vertical markets.

**Innovation:** Direct, related, complementary and synergistic layouts of resources, expertise or capital for investment, consolidation, defensive or pre-emptive purposes.

**Geographic Strategy:** The vendor's strategy to direct resources, skills and offerings to meet the specific needs of geographies outside the "home" or native geography, either directly or through partners, channels and subsidiaries as appropriate for that geography and market.