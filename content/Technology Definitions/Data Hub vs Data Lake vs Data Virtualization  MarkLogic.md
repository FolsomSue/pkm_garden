# Data Hub vs Data Lake vs Data Virtualization | MarkLogic

> Learn the differences between data hubs, data lakes, and data virtualization. MarkLogic is here to help your organization reach mission-critical data goals.

All large organizations have massive amounts of data and it is usually spread out across many disparate systems. This wasn’t a conscious choice but rather a bunch of pragmatic tradeoffs. Silos are tech debt and are on the rise with the adoption of Software as a Service (SaaS) applications and other cloud offerings, increasing friction between the business and IT. Integrating those data silos is notoriously difficult, and there are clear challenges when trying to use a [traditional data warehouse approach](https://www.marklogic.com/product/comparisons/data-hub-vs-data-warehouse/). For that reason, IT organizations have sought modern approaches to get the job done (at the urgent request of the business).

This comparison covers three modern approaches to data integration: Data lakes, data virtualization or federation, and data hubs. All three approaches simplify self-service consumption of data across heterogeneous sources without disrupting existing applications. However, there are trade-offs to each of these new approaches and the approaches are not mutually exclusive — many organizations continue to use their data lake alongside a data hub-centered architecture.

|  | MarkLogic Data Hub | Data Lake | Data Virtualization |
| --- | --- | --- | --- |
| Data Ingestion | 
*   Load raw data _as is_
*   Data physically migrated and persisted in a database

 | 

*   Load raw data _as is_
*   Data physically migrated and stored in HDFS or an object store

 | 

*   Virtual views of the data
*   No data is physically moved

 |
| Data Model | 

*   Multi-Model
*   Native JSON, XML, and RDF storage

 | 

*   HDFS is a file system that supports multiple data models

 | 

*   Often the same as the underlying federated systems, but can also create new composite views or semantic layers

 |
| Search & Query | 

*   Built-in, full-text search
*   Complete indexing (words, structure, etc.)
*   Relational views over unstructured data

 | 

*   Depends. There are various tools for data access: Hive, Hbase, Impala, Presto, Drill, etc. These add-on tools attempt to add query capabilities, but are generally limited and complex to manage

 | 

*   Queries optimized and passed to underlying systems. Dependent on indexes defined in those systems

 |
| Operational Capabilities | 

*   ACID transactions at scale
*   Real-time data processing
*   REST, JDBC, ODBC, etc.

 | 

*   No ACID transactions, cannot power transactional apps
*   Other tools used to operationalize the data

 | 

*   No ACID transactions, cannot power transactional apps
*   Can provide an access layer for data consumption via JDBC, ODBC, REST, etc.

 |
| Curation

(Harmonization, Enrichment, Mastering)

 | 

*   High-performance data pipelines at scale
*   Support for third-party tools (MuleSoft, Apache NiFi)
*   Easy to use Data Hub UI
*   Smart Mastering
*   Agile data curation

 | 

*   Depends. There are some tools that support “ELT” on Hadoop. Most use cases involve using an ETL tool before or after moving data to a data lake

 | 

*   Some support for data curation when the data is returned or processed, but usually relies on data pipeline or ETL tools

 |
| Security | 

*   Granular security controls
*   RBAC at document/element level
*   Redaction on export
*   Advanced encryption

 | 

*   Poor data security and governance (or at least hard to operationalize and requires additional tools to fill gaps such as Apache Atlas, Cloudera Navigator)

 | 

*   Security controls are required for both the virtual database and underlying database —  both layers must be secured

 |
| Scalability | 

*   Petabyte scalability
*   Higher cost due to indexing overhead for some implementations. Also, MarkLogic Data Hub Service provides predictable low-cost auto-scaling

 | 

*   Petabyte scalability
*   Ideal for low-cost storage

 | 

*   Only performs as well as the slowest federate, and is impacted by system load or issues in any federate

 |
| Performance | 

*   High-performance transactions and analytics
*   Dedicated, separate hardware from source systems for independent scaling

 | 

*   High-performance analytics
*   Performance depends on the infrastructure the system runs on

 | 

*   High-performance analytics
*   Performance depends on both the infrastructure the virtual database runs on _and_ the performance of the underlying systems’ infrastructure
*   Performance is also dependent on all network connections

 |
| Deployment | 

*   Self-managed deployment in any environment
*   And, fully managed, serverless deployment with MarkLogic Data Hub Service

 | 

*   Self-managed deployment in any environment

 | 

*   Since there is no data migrated, they are very fast to deploy. It may only require a VM to be configured

 |

A Data lake is a central repository that makes data storage at any scale or structure possible. They became popular with the rise of Hadoop, a distributed file system that made it easy to move raw data into one central repository where it could be stored at a low cost. In data lakes, the data may not be curated (enriched, mastered, harmonized) or searchable and they usually require other tools from the Hadoop ecosystem to analyze or operationalize the data in a multi-step process. But, data lakes have the advantage of not requiring much work on the front end when loading data.

Data lake use cases include serving as an analytics sandbox, training machine learning models, feeding data prep pipelines, or just offering low-cost data storage.

A few years ago, the Hadoop landscape was contended by three main players: Cloudera, Hortonworks, and MapR. Today, only Cloudera remains following its [merger with Hortonworks](https://techcrunch.com/2019/01/03/cloudera-and-hortonworks-finalize-their-merger/) and [MapR’s fire sale](https://techcrunch.com/2019/08/07/with-mapr-fire-sale-hadoops-promise-has-fallen-on-hard-times/).

For many organizations, object stores like [Amazon S3](https://aws.amazon.com/s3/) have become de facto data lakes, and support the move to the cloud from an on-premises Hadoop landscape.

Besides the Hadoop core, there are many other related tools in the Apache ecosystem. For example, [Spark](https://spark.apache.org/) and [Kafka](https://kafka.apache.org/) are two popular tools used for processing streaming data and doing analytics in an event-streaming architecture (they are marketing by [Databricks](https://databricks.com/) and [Confluent](https://www.confluent.io/), respectively).

A detailed review of those tools is out of scope for this comparison. But, in general, those tools are complementary to a data hub approach for most use cases. They manage streaming data but still need a database. For example, Kafka does not have a data model, indexes, or way of querying data. As a rule of thumb, an event-based architecture and analytics platform that has a data hub underneath is more trusted and operational than without the data hub.

Data virtualization involves creating virtual views of data stored in existing databases. The physical data doesn’t move but you can still get an integrated view of the data in the new virtual data layer. This is often called data federation (or virtual database), and the underlying databases are the federates.

For example, you may have a few Oracle and SAP databases running and a department needs access to the data from those systems. Rather than physically moving the data via ETL and persisting it in another database, architects can virtually (and quickly) retrieve and integrate the data for that particular team or use case.

With data virtualization, queries hit the underlying database. Newer virtualization technologies are increasingly sophisticated when handling query execution planning and optimization. They may utilize cached data in-memory or use integrated massively parallel processing (MPP), and the results are then joined and mapped to create a composite view of the results. Many newer data virtualization technologies can also write data (not just read). Newer solutions also show advances with data governance, masking data for different roles and use cases and using LDAP for authentication.

One of the major benefits of data virtualization is faster time to value. They require less work and expense before you can start querying the data because the data is not physically moved, making them less disruptive to your existing infrastructure.

Another major benefit is that data virtualization gives users the ability to run ad hoc SQL queries on both unstructured and structured data sources — a primary use case for data virtualization.

### So, with all these benefits, what are the drawbacks of data virtualization?

*   Virtual databases do not index the data, nor do they have separate data storage to store indexes. They rely on the underlying source systems to have indexes, which are often inadequate
*   Virtual databases map any request into a different request for each source system and execute on all source systems. This can create performance problems across the network and the system will always face concerns with network capacity
*   Virtual databases have no place to “curate” the data, increase data quality, or track data lineage or history. They do minimal data harmonization, and only when data is returned or processed. There is no persisted canonical form of the data to create a single source of truth and securely share it with downstream consumers.
*   Virtual databases usually have limited (or at least more complex to implement) security controls. For example, virtual databases may only secure data at the table level, not per record.
*   Virtual database volume will always be limited in scope to the volume of data in the underlying source systems

Examples of companies offering stand-alone data virtualization solutions are [SAS](https://www.sas.com/en_us/software/federation-server.html), [Tibco](https://www.tibco.com/products/data-virtualization), [Denodo](https://www.denodo.com/en), and [Cambridge Semantics](https://www.cambridgesemantics.com/). Other vendors such as Oracle, Microsoft, SAP, and Informatica embed data virtualization as a feature of their flagship products.

Data hubs are data stores that act as an integration point in a hub-and-spoke architecture. They physically move and integrate multi-structured data and store it in an underlying database.

### Here are some of the key advantages of a data hub

*   Data hubs are powered by an underlying multi-model database (which data lakes and virtual databases do not have), which gives them the ability to serve as a system of truth with all the required enterprise security including data confidentiality (access control), data availability (HA/DR), and data integrity (distributed transactions) capabilities
*   Data hubs have the tools to curate the data (enriching, mastering, harmonizing) and they support progressive harmonization, the result of which is persisted in the database.
*   Data hubs support operational and transactional applications, something data lakes are not designed for. And, while virtual databases can support transactions, the load is throttled by the performance of the underlying database systems

With these advantages, a data hub can act as a strong complement to data lakes and data virtualization by providing a governed, transactional data layer. We discuss this more in depth below.

Here are some of the signs that indicate a data hub is a good choice for your architecture:

*   **When you want to integrate multi-model data —** Data hubs are good at integrating multi-structured, changing data. They are ideal if you want to track where your data comes from and impose a single, easy-to-govern security data model. They also provide built-in curation capabilities to enrich, harmonize, and master data (including deduplication)
*   **When the business needs a data service fast —** Data hubs provide agility both in terms of getting data in and also getting value fast. They are much more than just analytical sandboxes. A data hub full of well-curated data can begin delivering business value with data services in weeks
*   **When you need real-time, operational views —** Data hubs are operational and transactional, providing real-time views and acting as a single source of truth. This makes them a good choice when your analytics team needs a real-time, operational analytics, not a historical snapshot
*   **When you need a stable platform and trusted point of integration —** Data hubs are backed by a database. They operate independently of other systems and thus are not tied to network or infrastructure constraints of other systems. And, they persist data, provide HA/DR, transactional consistency, enterprise security, and all the other capabilities required to act as a stable platform

Our customers typically use the MarkLogic Data Hub Platform for use cases such as building a unified view, operational analytics, content monetization, research and development, industrial IoT, regulatory compliance, ERP integration, and mainframe migrations.

Data Lakes are best for streaming data, and they serve as good repositories when organizations need a low-cost option for storing massive amounts of data, structured or unstructured. Most data lakes are backed by HDFS and connect easily into the broader Hadoop ecosystem. This makes it a good choice for large development teams that want to use open source tools, and need a low-cost analytics sandbox. Many organizations rely on their data lake as their “data science workbench” to drive machine learning projects where data scientists need to store training data and feed Jupyter, Spark, or other tools.

Data virtualization is the best option for certain analytics use cases that may not require the robustness of a data hub for data integration use cases. They can be deployed quickly and because the physical data is never moved, they do not require much work to provision infrastructure at the beginning of a project. Another common use for data virtualization is for data teams to run ad-hoc SQL queries on top of non-relational data sources.

Data hubs and data virtualization approaches are two different approaches to data integration and may compete for the same use case. We find that customers who are using a data hub usually do not need to implement data virtualization as well. The data hub covers almost all of the same benefits. For instance, many MarkLogic customers have built metadata (or content) repositories to virtualize their critical data assets using MarkLogic Data Hub.

That said, it is possible to treat a MarkLogic Data Hub as a data source to be federated, just like any other data source. For example, MarkLogic Data Hub can be used to integrate data from multiple sources and can be accessed as a federated data source using tools like Spark for training and scoring machine learning models.

Data lakes are very complementary to data hubs. There are many of our customers that have utilized the MarkLogic Connector for Hadoop to move data from Hadoop into MarkLogic Data Hub, or move data from MarkLogic Data Hub to Hadoop. The Data Hub sits on top of the data lake, where the high-quality, curated, secure, de-duplicated, indexed and query-able data is accessible. Additionally, to manage extremely large data volumes, MarkLogic Data Hub provides automated data tiering to securely store and access data from a data lake.

Most commonly, customers either have an existing data lake and are in the process of migrating off of it, or they are choosing to off-load low-usage data into Hadoop to get the benefits of low-cost storage or support machine learning projects.

When considering what the next step is in planning your architecture, here is the summary of options to consider:

*   Choose to build a new data hub, with [MarkLogic Data Hub Service](https://www.marklogic.com/product/data-hub-service/), for your next big data integration project instead of using a data lake or data virtualization (or trying to build a custom made ‘data hub’ with a bunch of bolted-together components)
*   Build a data hub on top of a data lake, using MarkLogic Data Hub Service as the integration point for curating and governing data and the data lake for batch processing and data science
*   Consolidate as much data as possible via integration into one or more data hubs and expose that via data virtualization

We have many customers who chose to supplement or replace their data lake or data virtualization with a [MarkLogic Data Hub](https://www.marklogic.com/product/data-hub/). Some examples you can explore include [Northern Trust](https://www.marklogic.com/customers/northern-trust/), [AFRL](https://www.marklogic.com/customers/afrl/), and [Chevron](https://www.marklogic.com/customers/chevron/).


[Source](https://www.marklogic.com/product/comparisons/data-hub-vs-data-lake/)