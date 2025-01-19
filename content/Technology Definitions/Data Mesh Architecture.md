#Technology #definition #Data #Mesh
# Data Mesh Architecture
## Why You May Need a Data Mesh[](https://www.datamesh-architecture.com/#why)

Many organizations have invested in a central data lake and a data team with the expectation to drive their business based on data. However, after a few initial quick wins, they notice that **the central data team often becomes a bottleneck**. The team cannot handle all the analytical questions of management and product owners quickly enough. This is a massive problem because making timely data-driven decisions is crucial to stay competitive. For example: Is it a good idea to offer free shipping during Black Week? Do customers accept longer but more reliable shipping times? How does a product page change influence the checkout and returns rate?

The data team wants to answer all those questions quickly. In practice, however, they struggle because they need to spend too much time fixing broken data pipelines after operational database changes. In their little time remaining, **the data team has to discover and understand the necessary domain data**. For every question, they need to learn domain knowledge to give meaningful insights. Getting the required domain expertise is a daunting task.

![The central data team in the middle surrounded by all domain teams, CEO, CFO, and marketing who all have an information need the central data team must fulfill, and for that, the central data team needs to import and understand the data of all domain teams.](https://d33wubrfki0l68.cloudfront.net/5ef8ca2ccbc6958154d934f4e0055431ee94e7a5/aa2f3/images/whyteam.png.webp)

![You already scaled up your software development by: 1. Decentralize business into domains; 2. Decentralize engineering into autonomous teams; 3. Decentralize monolith into microservices; 4. Decentralize operations into DevOps teams. Next step: scale up data analytics by decentralizing data lake into data mesh](https://d33wubrfki0l68.cloudfront.net/b0e3bc95a0e6cf6a03b8dc6bbeb2707544f0cba5/18737/images/whychecklist.png.webp)

On the other hand, organizations have also invested in domain-driven design, autonomous domain teams (also known as stream-aligned teams or product teams) and a decentralized microservice architecture. These **domain teams own and know their domain**, including the information needs of the business. They design, build, and run their web applications and APIs on their own. Despite knowing the domain and the relevant information needs, the domain teams have to reach out to the overloaded central data team to get the necessary data-driven insights.

With the eventual growth of the organization, the situation of the domain teams and the central data team becomes worse. A way out of this is to shift the responsibility for data from the central data team to the domain teams. This is the core idea behind the data mesh concept: **Domain-oriented decentralization for analytical data**. A data mesh architecture enables domain teams to perform cross-domain data analysis on their own and interconnects data, similar to APIs in a microservice architecture.

## What Is Data Mesh?[](https://www.datamesh-architecture.com/#what-is-data-mesh)

[![What Is Data Mesh? Includes the four principles Domain Ownership, Data as a Product, Self-serve Data Platform, and Federated Governance.](https://d33wubrfki0l68.cloudfront.net/53d758b104301dd53246aee7ecf406e1267455f2/61a59/images/datamesh.png.webp)](https://www.datamesh-architecture.com/images/datamesh.png.webp)

The term _data mesh_ was coined by [Zhamak Dehghani](https://martinfowler.com/articles/data-mesh-principles.html)  in 2019 and is based on four fundamental principles that bundle well-known concepts:

The **domain ownership** principle mandates the domain teams to take responsibility for their data. According to this principle, analytical data should be composed around domains, similar to the team boundaries aligning with the system’s bounded context. Following the domain-driven distributed architecture, analytical and operational data ownership is moved to the domain teams, away from the central data team.

The **data as a product** principle projects a product thinking philosophy onto analytical data. This principle means that there are consumers for the data beyond the domain. The domain team is responsible for satisfying the needs of other domains by providing high-quality data. Basically, domain data should be treated as any other public API.

The idea behind the **self-serve data infrastructure platform** is to adopt platform thinking to data infrastructure. A dedicated data platform team provides domain-agnostic functionality, tools, and systems to build, execute, and maintain interoperable data products for all domains. With its platform, the data platform team enables domain teams to seamlessly consume and create data products.

The **federated governance** principle achieves interoperability of all data products through standardization, which is promoted through the whole data mesh by the governance guild. The main goal of federated governance is to create a data ecosystem with adherence to the organizational rules and industry regulations.

## How To Design a Data Mesh?[](https://www.datamesh-architecture.com/#how-to-design-a-data-mesh)

A data mesh architecture is a decentralized approach that enables domain teams to perform cross-domain data analysis on their own. At its core is the domain with its responsible team and its operational and analytical data. The domain team ingests operational data and builds analytical data models to perform their own analysis. It uses analytical data to build data products based on other domains’ needs.

![Data Mesh Architecture](https://d33wubrfki0l68.cloudfront.net/d4af4102e2132f5087f4227023e9246eca2d0ecd/e5f0e/images/datamesharchitecture.png.webp)

The domain team agrees with others on global policies, such as interoperability, security, and documentation standards in a federated governance guild, so that domain teams know how to discover, understand and use data products available in the data mesh. The self-serve domain-agnostic data platform, provided by the data platform team, enables domain teams to easily build their own data products and do their own analysis effectively. An enabling team guides domain teams on how to model analytical data, use the data platform, and build and maintain interoperable data products.

Let’s zoom in to the core components of a data mesh architecture and their relationships:

#### Data Product[](https://www.datamesh-architecture.com/#data-product)

A data product usually is a published **data set** that can be accessed by other domains, similar to an API. For example, the history of inventory updates in a Google BigQuery table or a daily JSON file with purchase orders on an AWS S3 bucket. A data product can take other forms as well, including a sales report containing KPIs and charts as a PDF or even a machine learning model to predict shipping dates as an ONNX file.

To discover, access, and use the data product, it is described with **metadata**, including ownership and contact information, data location and access, update frequency, and a specification of the data model.

The domain team is responsible for the **operations** of the data product during its entire lifecycle. The team needs to continuously monitor and ensure data quality and availability. For example, keep the data without duplicates or react to missing entries.

![Data Product consists of Data, Metadata, and Operations](https://d33wubrfki0l68.cloudfront.net/00b0ebca74c0d26c71cfbd3c5d662d01ddd6b1ca/8759a/images/dataproduct.png.webp)

#### Federated Governance[](https://www.datamesh-architecture.com/#federated-governance)

The federated governance body is typically organized as a guild consisting of representatives of all teams taking part in the data mesh. They agree on global policies, which are the rules of play in the data mesh. These rules define how the domain teams have to build their data products.

Policies on **interoperability** are the starting point. They allow other domain teams to use data products in a consistent way. For example, global policies could define that the standard way to provide data is as a CSV file on AWS S3 in a bucket owned by the corresponding domain team.

Next, there has to be some form of **documentation** to discover and understand available data products. A simple policy for this could be a wiki page with a predefined set of metadata, such as owner of the data product, location URL, and descriptions of the CSV fields.

A uniform way to access the actual data product in a **secure** way could be using role-based access in AWS IAM, managed by the domain team.

Global policies such as **privacy** and **compliance** are also common. Think about protection of personally identifiable information (PII) or industry-specific legal requirements.

![Four examples of global polices](https://d33wubrfki0l68.cloudfront.net/16a49f44c78d1b317f7441891beb2b26a0657666/da734/images/globalpolicies.png.webp)

#### Analytical Data[](https://www.datamesh-architecture.com/#analytical-data)

Diving into the analytical data, we can see the data flows that lead toward the data products. Operational data is often ingested as some kind of **raw** and unstructured data.

In a preprocessing step, raw data is cleaned and structured into events and entities. **Events** are small, immutable, and highly domain oriented, such as _OrderPurchased_ or _ShipmentDelivered_. **Entities** represent business objects such as _shipments_ or _articles_ with their state changing over time. That’s why the entities often are represented as a list of snapshots, the history, with the latest snapshot being the current state.

In practice, we often see **manually** entered or imported data. For example, forecast data sent via email as CSV files or text descriptions for business codes.

Data from other teams are integrated as **external** data. When using data products from other teams that are well governed, this integration might be implemented in a very lightweight way. In case of importing data from legacy systems, the external area acts as an [anti-corruption layer](https://www.domainlanguage.com/ddd/reference/) .

The published data product is derived by **aggregating** a subset of the events, entities, manual, and external data.

[![More detailed view on the analytical data of the data mesh architecture](https://d33wubrfki0l68.cloudfront.net/86052f6d53e89b986bbb06cdfae9d88919ba9efc/9c3b6/images/analyticaldata.png.webp)](https://www.datamesh-architecture.com/images/analyticaldata.png.webp)

#### Ingesting[](https://www.datamesh-architecture.com/#ingesting)

How can domain teams ingest their operational data into the data platform? A software system designed according to domain-driven design principles contains data as mutable entities/aggregates and immutable domain events.

**Domain events** are a great fit to be ingested into the data platform as they represent relevant business facts. If there’s a messaging system in place domain events can be forwarded to the data platform by attaching an additional message consumer. Data can be collected, processed, and forwarded to the data platform in real time. With this **streaming ingestion**, data is sent in small batches when they arrive, so they are immediately available for analytics. As domain events are already well defined, there is little to do in terms of cleaning and preprocessing, except deduplication and anonymization of PII data. Sometimes, it is also advisable to define and ingest internal analytical events that contain information that is relevant only for analytical use cases so that domain events don’t have to be modified.  
_Examples for streaming ingestion: Kafka Connect, Kafka Streams, AWS Lambda_

Many business objects are persisted as **entities and aggregates** in SQL or NoSQL databases. Their state changes over time, and the latest state is persisted in the database only. Strong candidates for entities with state are _articles_, _prices_, _customer data_, or _shipment status_. For analytical use cases, it is often required to have both the latest state and the history of states over time. There are several approaches to ingest entities. One way is to generate and publish an **onCreate/onUpdate/onDelete event** with the current state every time an entity is changed, e.g. by adding an [aspect](https://en.wikipedia.org/wiki/Aspect-oriented_programming)  or [EntityListeners](https://docs.spring.io/spring-data/jpa/docs/current/api/index.html?org/springframework/data/jpa/domain/support/AuditingEntityListener.html) . Then streaming ingestion can be used to ingest the data as described above. When it is not feasible to change the operational software, **change data capture (CDC)** may be used to listen to database changes directly and stream them into the data platform.  
_Examples for CDC streaming: [Debezium](https://debezium.io/)_ 

Lastly, traditional scheduled **ELT or ETL jobs** that export data to file and load them into the platform can be set up, with the downside of not having real-time data, not having all stage changes between exports, and some work to consolidate exported data again. However, they are a viable option for legacy systems, such as mainframes.

![Closer look at ingesting and cleaning of data](https://d33wubrfki0l68.cloudfront.net/34bfd7f3b3fc45ae382e0a13bcd8e2a2de143ba7/8f7ad/images/ingestingandcleaning.png.webp)

#### Clean Data[](https://www.datamesh-architecture.com/#clean-data)

Clean data is the foundation for effective data analytics. With data mesh, domain teams are responsible for performing data cleaning. They know their domain and can identify why and how their domain data needs to be processed.

Data that is ingested into the data platform is usually imported in its original raw and unstructured format. When using a columnar database, this might be a row per event that contains a [CLOB](https://en.wikipedia.org/wiki/Character_large_object)  field for the event payload, which may be in JSON format. Now it can be preprocessed to get data clean:

-   **Structuring:** Transform unstructured and semi-structured data to the analytical data model, e.g., by extracting JSON fields into columns.
-   **Mitigation of structural changes:** When data structures have changed, mitigate them, e.g., by filling null values with sensible defaults.
-   **Deduplication:** As most analytical storage systems are append-only, entities and events cannot be updated. Remove all duplicate entries.
-   **Completeness:** Ensure that data contain agreed periods, even when there were technical issues during ingestion.
-   **Fix outliers:** Invalid data that may occur through bugs get identified and corrected.

From an implementation perspective, these preprocessing steps can be implemented as simple SQL views that project the raw data. The queries may be organized through [common table expressions](https://cloud.google.com/bigquery/docs/reference/standard-sql/query-syntax#with_clause)  (CTEs) and may be enhanced with [user-defined functions](https://cloud.google.com/bigquery/docs/reference/standard-sql/user-defined-functions)  (UDFs), e.g., for JSON processing. As an alternative, the cleaning steps can be implemented as lambda functions that operate on topics. More complex pipelines can be built with frameworks like [dbt](https://www.getdbt.com/)  or [Apache Beam](https://beam.apache.org/)  that offer an advanced programming model, but also require more skills to master.

<table data-tab-size="8" data-paste-markdown-skip="" data-tagsearch-lang="SQL" data-tagsearch-path="entities__inventory_history.sql"><tbody><tr><td id="file-entities__inventory_history-sql-L1" data-line-number="1"></td><td id="file-entities__inventory_history-sql-LC1"><span><span>--</span> Step 1: Deduplicate</span></td></tr><tr><td id="file-entities__inventory_history-sql-L2" data-line-number="2"></td><td id="file-entities__inventory_history-sql-LC2">WITH inventory_deduplicated <span>AS</span> (</td></tr><tr><td id="file-entities__inventory_history-sql-L3" data-line-number="3"></td><td id="file-entities__inventory_history-sql-LC3"><span>SELECT</span> <span>*</span></td></tr><tr><td id="file-entities__inventory_history-sql-L4" data-line-number="4"></td><td id="file-entities__inventory_history-sql-LC4">EXCEPT (row_number)</td></tr><tr><td id="file-entities__inventory_history-sql-L5" data-line-number="5"></td><td id="file-entities__inventory_history-sql-LC5"><span>FROM</span> (</td></tr><tr><td id="file-entities__inventory_history-sql-L6" data-line-number="6"></td><td id="file-entities__inventory_history-sql-LC6"><span>SELECT</span> <span>*</span>,</td></tr><tr><td id="file-entities__inventory_history-sql-L7" data-line-number="7"></td><td id="file-entities__inventory_history-sql-LC7">ROW_NUMBER() OVER (PARTITION BY id <span>ORDER BY</span> <span>time</span> <span>DESC</span>) row_number</td></tr><tr><td id="file-entities__inventory_history-sql-L8" data-line-number="8"></td><td id="file-entities__inventory_history-sql-LC8"><span>FROM</span> <span><span>`</span>datameshexample-fulfillment.raw.inventory<span>`</span></span>)</td></tr><tr><td id="file-entities__inventory_history-sql-L9" data-line-number="9"></td><td id="file-entities__inventory_history-sql-LC9"><span>WHERE</span> row_number <span>=</span> <span>1</span></td></tr><tr><td id="file-entities__inventory_history-sql-L10" data-line-number="10"></td><td id="file-entities__inventory_history-sql-LC10">),</td></tr><tr><td id="file-entities__inventory_history-sql-L11" data-line-number="11"></td><td id="file-entities__inventory_history-sql-LC11"><span><span>--</span> Step 2: Parse JSON to columns</span></td></tr><tr><td id="file-entities__inventory_history-sql-L12" data-line-number="12"></td><td id="file-entities__inventory_history-sql-LC12">inventory_parsed <span>AS</span> (</td></tr><tr><td id="file-entities__inventory_history-sql-L13" data-line-number="13"></td><td id="file-entities__inventory_history-sql-LC13"><span>SELECT</span></td></tr><tr><td id="file-entities__inventory_history-sql-L14" data-line-number="14"></td><td id="file-entities__inventory_history-sql-LC14">json_value(data, <span><span>"</span>$.sku<span>"</span></span>) <span>AS</span> sku,</td></tr><tr><td id="file-entities__inventory_history-sql-L15" data-line-number="15"></td><td id="file-entities__inventory_history-sql-LC15">json_value(data, <span><span>"</span>$.location<span>"</span></span>) <span>AS</span> location,</td></tr><tr><td id="file-entities__inventory_history-sql-L16" data-line-number="16"></td><td id="file-entities__inventory_history-sql-LC16">CAST(json_value(data, <span><span>"</span>$.available<span>"</span></span>) <span>AS</span> int64) <span>AS</span> available,</td></tr><tr><td id="file-entities__inventory_history-sql-L17" data-line-number="17"></td><td id="file-entities__inventory_history-sql-LC17">CAST(json_value(data, <span><span>"</span>$.updated_at<span>"</span></span>) <span>AS</span> <span>timestamp</span>) <span>AS</span> updated_at,</td></tr><tr><td id="file-entities__inventory_history-sql-L18" data-line-number="18"></td><td id="file-entities__inventory_history-sql-LC18"><span>FROM</span> inventory_deduplicated</td></tr><tr><td id="file-entities__inventory_history-sql-L19" data-line-number="19"></td><td id="file-entities__inventory_history-sql-LC19">)</td></tr><tr><td id="file-entities__inventory_history-sql-L20" data-line-number="20"></td><td id="file-entities__inventory_history-sql-LC20"><span><span>--</span> Step 3: Actual Query</span></td></tr><tr><td id="file-entities__inventory_history-sql-L21" data-line-number="21"></td><td id="file-entities__inventory_history-sql-LC21"><span>SELECT</span> sku, location, available, updated_at</td></tr><tr><td id="file-entities__inventory_history-sql-L22" data-line-number="22"></td><td id="file-entities__inventory_history-sql-LC22"><span>FROM</span> inventory_parsed</td></tr><tr><td id="file-entities__inventory_history-sql-L23" data-line-number="23"></td><td id="file-entities__inventory_history-sql-LC23"><span>ORDER BY</span> sku, location, updated_at</td></tr></tbody></table>

#### Analytics[](https://www.datamesh-architecture.com/#analytics)

To gain insights, domain teams query, process, and aggregate their analytical data together with relevant data products from other domains.

**SQL** is the foundation for most analytical queries. It provides powerful functions to connect and investigate data. The data platform should perform join operations efficiently, even for large data sets. Aggregations are used to group data and window functions help to perform a calculation across multiple rows. Notebooks help to build and document exploratory findings.  
_Examples: Jupyter Notebooks, Presto_

Humans understand data, trends, and anomalies much easier when they perceive them visually. There are a number of great data **visualization** tools that build beautiful charts, key performance indicator overviews, dashboards and reports. They provide an easy-to-use UI to drill down, filter, and aggregate data.  
_Examples: Looker, Tableau, Metabase, Redash_

For more advanced insights, **data science and machine learning** methods can be applied. These enable correlation analyses, prediction models, and other advanced use cases. Special methodological, statistical, and technological skills are required.  
_Examples: scikit-learn, PyTorch, TensorFlow_

![Jupyter Notebook executing queries on Google BigQuery](https://d33wubrfki0l68.cloudfront.net/dd22a591a07a195d60e3f514a91da7a2a15fcd4a/572cd/images/notebook.png.webp)

#### Data Platform[](https://www.datamesh-architecture.com/#data-platform)

The self-serve data platform may vary for each organization. Data mesh is a new field and vendors are starting to add data mesh capabilities to their existing offerings.

Looking from the desired capabilities, you can distinguish between analytical capabilities and data product capabilities: **Analytical capabilities** enable the domain team to build an analytical data model and perform analytics for data-driven decisions. The data platform needs functions to ingest, store, query, and visualize data as a self-service. Typical data warehouse and data lake solutions, whether on-premise or a cloud provider, already exist. The major difference is that each domain team gets its own isolated area.

A more advanced data platform for data mesh also provides additional domain-agnostic **data product capabilities** for creating, monitoring, discovering, and accessing data products. The self-serve data platform should support the domain teams so that they can quickly build a data product as well as run it in production in their isolated area. The platform should support the domain team in publishing their data products so that other teams can discover them. The discovery requires a central entry point for all the decentralized data products. A data catalog can be implemented in different ways: as a wiki, git repository, or there are even already vendor solutions for a cloud-based data catalog such as Select Star, Google Data Catalog, or AWS Glue Data Catalog. The actual usage of data products, however, requires a domain team to access, integrate, and query other domains' data products. The platform should support, monitor, and document the cross-domain access and usage of data products.

An even more advanced data platform supports **policy automation**. This means that, instead of forcing the domain team to manually ensure that the global policies are not violated, the policies are automatically enforced through the platform. For example, that all data products have the same metadata structure in the data catalog, or that the PII data are automatically removed during data ingestion.

Efficiently combining data products from multiple domains, i.e., having large cross-domain join operations within a few seconds, ensures developer acceptance and happiness. That's why the **query engine has a large influence on the architecture of the data platform**. A shared platform with a single query language and support for separated areas is a good way to start as everything is highly integrated. This could be Google BigQuery with tables in multiple projects that are discoverable through Google Data Catalog. In a more decentralized and distributed data mesh, a distributed query engine such as Presto can still perform cross-domain joins without importing data, but they come with their own limitations, e.g., limited pushdowns require that all underlying column data need to be transferred.

#### Enabling Team[](https://www.datamesh-architecture.com/#enabling-team)

The enabling team spreads the idea of data mesh within the organization. In the beginning of data mesh adoption, a lot of explanatory efforts will be required and the enabling team can act as data mesh advocates. They help domain teams [on their journey to become a full member of the data mesh](https://www.datamesh-architecture.com/#domain-teams-journey). The enabling team consists of specialists with extensive knowledge on data analytics, data engineering, and the self-serve data platform.

A member of the enabling team temporarily joins a domain team for a limited time span like a month as an **internal consultant** to understand the team’s needs, establish a learning environment, upskill the team members in data analytics, and guide them on how to use the self-serve data platform. They don’t create data products by themselves.

In between their consulting engagements, they **share learning materials** such as walking skeletons, examples, best practices, tutorials, or even podcasts.

The _mesh_ emerges when teams use other domain's data products. Using data from upstream domains simplifies data references and lookups (such as getting an article's price), while data from downstream domains enables analyzing effects, e.g. for A/B tests (such as changes in the conversion rate). Data from multiple other domains can be aggregated to build comprehensive reports and new data products.

Let's look at a simplified e-commerce example:

[![Domains access data products from other domains](https://d33wubrfki0l68.cloudfront.net/48284e2ba830702691941fdf7cc38db8c37bf3a0/f97ce/images/mesh.png.webp)](https://www.datamesh-architecture.com/images/mesh.png.webp)

Domains can be classified by data characteristics and data product usage. We adopt Zhamak Dehghani’s classification:

## Source-aligned[](https://www.datamesh-architecture.com/#source-aligned)

In this example, an online shop is subdivided into domains along the customer journey, from _product search_ over _checkout_ to _payment_. In a data mesh, these domains publish their data as data products, so others can access them. The engineers do analytics on their own data to improve their operational systems and validate the business value of new features. They use domain neighbor’s data to simplify their queries and get insights on effects in downstream domains. These domain data can be referred to as **source-aligned**, as most of their published data products correspond closely to the _domain events_ and _entities_ generated in their operational systems.

## Aggregate[](https://www.datamesh-architecture.com/#aggregate)

For [complicated subsystems](https://teamtopologies.com/key-concepts) , it can be efficient that a team focuses solely on delivering a data product that is **aggregated** of various data products from other domains. A typical example is a 360° customer view that includes relevant data from multiple domains, such as account data, orders, shipments, invoices, returns, account balance, and internal ratings. With respect to different bounded contexts, a comprehensive 360° customer view is hard to build, but it might be useful for many other domains. Another example for a complicated subsystem is building sophisticated ML models that require enhanced data science skills. It may be sensible that a data scientists team develops and trains a recommendation model by using data from checkout and the 360° customer view, and another team uses this model and focuses to present the calculated recommendations in the online shop or in promotional emails.

## Consumer-aligned[](https://www.datamesh-architecture.com/#consumer-aligned)

In a company, there are also business departments that need data from the whole value stream to make sensible decisions, with people working in these departments are business experts but not engineers or technology-savvy. Management and controlling requires detailed reports and KPIs from all domains to identify strengths and deviations. Marketing does funnel and web analysis over all steps in the customer journey in their own optimized tools, such as Google Analytics or Adobe Analytics. In these domains, the data model is optimized for a specific department's needs and can therefore be described as **consumer-aligned**. Consumer-aligned reports were often one of the main tasks of central data teams. With data mesh, (new) consumer-aligned domain teams focus on fulfilling data needs of one specific business domain, allowing them to gain deep domain knowledge and constantly develop better analytical results. Business and IT grow closer together, either by building integrated domain teams or by having engineering teams that provide domain data as a service for the business, e.g., to support C-level or controlling. Their data are typically used for their analytics and reports, but does not need to be published and managed as data products for other domains.

## Tech Stacks[](https://www.datamesh-architecture.com/#tech-stacks)

Data mesh is primarily an organizational approach, and that's why you can't buy a data mesh from a vendor. Technology, however, is important still as it acts as an enabler for data mesh, and only useful and easy to use solutions will lead to domain teams' acceptance. The available offerings of cloud providers already provide a sufficient set of good self-serve data services to let you form a data platform for your data mesh. We want to show which services can be used to get started.

There are a lot of different ways to implement a data mesh architecture. Here is a selection of typical tech stacks that we saw:

-   [Google Cloud BigQuery](https://www.datamesh-architecture.com/tech-stacks/google-cloud-bigquery)
-   [AWS S3 and Athena](https://www.datamesh-architecture.com/tech-stacks/aws-s3-athena)
-   Azure (TBD)
-   On-Premise (TBD)

If you want to share your tech stack here, feel free to [reach out to us](https://www.datamesh-architecture.com/#authors).

## Domain Team’s Journey[](https://www.datamesh-architecture.com/#domain-teams-journey)

[![The five levels of the domain team's journey: (Level 0) No Data Analytics; (Level 1) Operational Database Queries; (Level 2) Analyze Own Data; (Level 3) Analyze Cross-domain Data; (Level 4) Publish Data as a Product](https://d33wubrfki0l68.cloudfront.net/adc4aa784b0e7727f50325cc47a69af3bcee3b8c/d8005/images/domainteamjourney.png.webp)](https://www.datamesh-architecture.com/images/domainteamjourney.png.webp)

Just as the [data team has a journey to go on](https://www.datamesh-architecture.com/#data-teams-journey), each of your domain teams has to go on a journey to become a contributing part of your data mesh as well. Each team can start their journey whenever they are ready and at their own pace. The benefits arise already along the journey. Teams will quickly gain from first data-driven decisions, starting an avalanche to use more and better data for even deeper insights. The data mesh evolves with each team that shares their data as products, enabling data-driven innovation.

To make this journey successful, the team needs three things: a clear data mesh vision from top management to get everybody moving in the same direction, a supportive environment including an easy-to-use self-serve data platform to get the engineering team on a learning path toward data analytics, and a high trust environment to walk the journey in their own way and pace.

So let’s start your journey!

### Level 0 No Data Analytics[](https://www.datamesh-architecture.com/#level-0-no-data-analytics)

Your team is responsible for a domain and builds and operates [self-contained systems](https://scs-architecture.org/)  including the necessary infrastructure. It was quite an effort to build these systems, and you were highly focused on delivery excellence. These operational systems now generate domain data.

Data analytics was just not relevant.

[![Level 0: No Data Analytics](https://d33wubrfki0l68.cloudfront.net/f1d1296d6a437bb1e52726323f0b940c4ae58f29/d165b/images/domainteamjourney_level0.png.webp)](https://www.datamesh-architecture.com/images/domainteamjourney_level0.png.webp)

### Level 1 Operational Database Queries[](https://www.datamesh-architecture.com/#level-1-operational-database-queries)

Being in production, you probably have to investigate an incident and need to analyze how many customers are affected. Also, some stakeholders might have questions regarding your data, such as "Which in-stock articles haven’t been sold in the last six months?" or "What were the shipping times during the last Black Week?" To answer all these questions, you send analytical queries to your operational database. Over time, you also do some first explorative analytics to get a deeper understanding of your system’s behavior.

This increases load on your production database, and you might be tempted to change the production database to better support your analytical queries, like creating additional indices. You might offload the additional load to read replicas. But analytical queries are still slow and cumbersome to write.

[![Level 1: Operational Database Queries](https://d33wubrfki0l68.cloudfront.net/12e75d4e16430c4297899154a34d16307741bb62/107fc/images/domainteamjourney_level1.png.webp)](https://www.datamesh-architecture.com/images/domainteamjourney_level1.png.webp)

### Level 2 Analyze Own Data[](https://www.datamesh-architecture.com/#level-2-analyze-own-data)

With the pains of slow and hard-to-write analytical queries in the back of your mind, you try out the self-serve data platform that’s being promoted by the data platform team. For example, you now have access to Google BigQuery. On this platform, your team starts to build an analytical data model from your operational databases. This allows you to analyze data covering your own systems with maintainable and fast queries, while keeping the schemas of your operational databases untouched. You learn how to structure, preprocess, clean, analyze, and visualize analytical data—that’s a lot to learn even though most is SQL, which you are already familiar with.

As questions regarding your own data can now be answered quickly, you and your product owner now enter the cycle of making data-driven decisions: define hypotheses and verify with data.

[![Level 2: Analyze Own Data](https://d33wubrfki0l68.cloudfront.net/ffa9b2bd1a676d5b270369073c0dc87fed0fdb39/3bffe/images/domainteamjourney_level2.png.webp)](https://www.datamesh-architecture.com/images/domainteamjourney_level2.png.webp)

### Level 3 Analyze Cross-domain Data[](https://www.datamesh-architecture.com/#level-3-analyze-cross-domain-data)

Analyzing your own domain data is a great start, but combining it with data from other domains is where the magic begins. It allows you to get a comprehensive view despite the decentralization of data. Examples are A/B tests of the effect of a UI change to the conversion rate or building up machine learning models for fraud detection that include previous purchasing history and current click stream behavior. This requires that other teams share their data in a way that your team can discover, access, and use it. This is when the mesh begins to form itself.

When a team becomes a consuming member of the data mesh, it starts to gain interest in the interoperability and governance of the data mesh. Ideally, the team will send a representative to the data mesh governance body.

In case you are the first team, you may have to skip this step for now and move on to level 4 and be the first to provide data for others.

[![Level 3: Analyze Cross-domain Data](https://d33wubrfki0l68.cloudfront.net/6b5155447e6654185b2005f587ab4c352f237ea0/27995/images/domainteamjourney_level3.png.webp)](https://www.datamesh-architecture.com/images/domainteamjourney_level3.png.webp)

### Level 4 Publish Data as a Product[](https://www.datamesh-architecture.com/#level-4-publish-data-as-a-product)

Based on other teams' needs, you share your data with others as products. For example, you provide the confirmed, rejected, and aborted orders so others can correlate their events to the conversion rate. Instead of just being a consumer of data products, you become a producer of data products. You generate value for other teams. But at the same time, it increases your responsibility and operational duties in the long term.

Data products must comply with the global policies defined by the federated governance body. You have to know and understand the current global policies. Now, at the latest, you need to participate in and contribute to the federated governance body.

[![Level 4: Publish Data as a Product](https://d33wubrfki0l68.cloudfront.net/84fb6e4cba6321e84dfded9ec3e212dce8ccb1e6/fdc61/images/domainteamjourney_level4.png.webp)](https://www.datamesh-architecture.com/images/domainteamjourney_level4.png.webp)

## Data Team’s Journey[](https://www.datamesh-architecture.com/#data-teams-journey)

[![Data Team's Journey: From a central data team toward an enablement team, data platform team, and (new) domain teams with data expertise](https://d33wubrfki0l68.cloudfront.net/df5bba2fc21f433e9f4e53063e038b9c85f0f3b1/19490/images/datateamjourney.png.webp)](https://www.datamesh-architecture.com/images/datateamjourney.png.webp)

Data mesh is primarily an organizational construct and fits right into the [principles of team topologies](https://teamtopologies.com/key-concepts) . It shifts the responsibilities for data toward domain teams which are supported by a data platform team and a data enabling team. Representatives of all teams come together in a federated governance guild to define the common standards.

Today, in many organizations a central data team is responsible for a wide range of analytical tasks, from data engineering and managing data infrastructure to creating C-level reports. Such a central data team suffers from cognitive overload, including domain, technical, and methodical knowledge. data mesh mitigates this.

Data mesh offers new perspectives for members of the central data team as their analytical and data engineering skills remain highly necessary. For example, they are a perfect fit to establish the data platform for people that prefer to work on the infrastructure. Some of them can form a data enabling team to act as internal consultants, [helping domain teams on their journey](https://www.datamesh-architecture.com/#domain-teams-journey). Regardless of their new roles, many of them will meet again in the data mesh federated governance guild to shape the future of the data mesh.

The real mind shift, however, happens when founding new data-centric domains as shown in the figure above. Let’s look at typical management reports that large central data teams usually produce based on monolithic data warehouses or data lakes. With data mesh, the data engineers who created those management reports build a new domain team together with a dedicated product owner. As engineers of the new domain team, they now can focus on their new domain and their consumers. This allows them to gain deep domain knowledge over time, resulting in better reports and continuous optimizations. In addition, they switch from using that monolith data warehouse to data products from other domains. This switch is a gradual process driven by the demand for data products, accelerating the forming of a data mesh. The product owner negotiates with other domain teams about the required data products and makes sure that the reports and other products the new domain team will build in the future fulfill the needs of the business.

As existing domain teams on their journey do more and more data analytics, another perspective for members of the central data team is to join one of those teams. With their existing knowledge, they can accelerate the domain teams’ journeys toward a data mesh by spreading and teaching their knowledge and skills to the others in the team. It is important that they become full members of the team and not founding a data sub-team within the domain team. In addition to their knowledge and skills, the data engineers may also bring responsibilities and artifacts from the central data team to their domain teams. For example, customer profiling, which was previously done by the central data team, will move into the responsibility of the recommendation domain team.

The data scientists, typically, are centrally organized as well. That’s why their future, organizational-wise, is quite similar to that of the central data team. The data products in the data mesh they focus on are machine learning features and models. When joining an existing domain team, such a machine learning model might be fully integrated in a microservice. So, data mesh enables such machine-learning-based services because the required [MLOps](https://ml-ops.org/)  capabilities can be easily built on top of the data mesh.

[![Migrating an existing data product and some data engineers from the central data team to a (new) domain team](https://d33wubrfki0l68.cloudfront.net/db3e9d18a6f3a964dc12e68ea4ab0fa2d77bd381/1b46d/images/newdomainteam.png.webp)](https://www.datamesh-architecture.com/images/newdomainteam.png.webp)

## FAQ[](https://www.datamesh-architecture.com/#faq)

#### So, what's really behind the hype?[](https://www.datamesh-architecture.com/#so-whats-really-behind-the-hype)

Data mesh is primarily an organizational change. The responsibilities of data are shifted closer to the business value stream. This enables faster data-driven decisions and reduces barriers for data-centric innovations.

#### How to get started?[](https://www.datamesh-architecture.com/#how-to-get-started)

Start small and agree on the big picture. Find two domain teams (that are around level 2) that have a high value use case where one team needs data from the other team. Let one team build a data product (level 4) and another team use that data product (level 3). You don’t need a sophisticated data platform yet. You can start sharing the files via AWS S3, a Git repository, or use a cloud-based database, such as Google BigQuery.

#### Is Data Mesh for my company?[](https://www.datamesh-architecture.com/#is-data-mesh-for-my-company)

It depends, of course. There are a few prerequisites that should be in place: You should have modularized your software system following domain-driven design principles or something similar. You should have a good number (5+) of independent domain teams that have their systems already running in production. And finally, you should trust your teams to make data-driven decisions on their own.

#### When should I avoid a Data Mesh?[](https://www.datamesh-architecture.com/#when-should-i-avoid-a-data-mesh)

There are some indicators when a data mesh approach might not be suitable for you, including:

-   You are too small and don’t have multiple independent engineering teams.
-   You have low-latency data requirements. Data Mesh is a network of data. If you need to optimize for low-latency, invest in a more integrated data platform.
-   You are happy with your monolithic highly integrated system (such as SAP). It might be more efficient to use their analytical platform.

#### Is the Data Mesh a generic solution to a distributed data architecture?[](https://www.datamesh-architecture.com/#is-the-data-mesh-a-generic-solution-to-a-distributed-data-archit)

No.

By definition, data mesh does not include data products used for serving real-time needs. Data mesh focuses on analytical use cases.

#### What's the difference between data mesh and data fabric?[](https://www.datamesh-architecture.com/#whats-the-difference-between-data-mesh-and-data-fabric)

At first, [data fabric](https://www.ibm.com/analytics/data-fabric)  looks similar to data mesh because it offers a similar self-serve data platform. Looking deeper, it turns out that data fabric is a central and domain-agnostic approach, which is in strong contrast to the domain-centric and decentralized approach of data mesh. [More in this comparison article](https://www.datanami.com/2021/10/25/data-mesh-vs-data-fabric-understanding-the-differences/) .

#### What might a journey be for teams who operate commercial off-the-shelf (COTS) systems?[](https://www.datamesh-architecture.com/#what-might-a-journey-be-for-teams-who-operate-commercial-off-the)

Many COTS systems (such as Salesforce, SAP, Shopify, Odoo) provide domain optimized analytical capabilities. So the journey for domain teams starts directly from [level 2](https://www.datamesh-architecture.com/#level-2-analyze-own-data).

The challenge is to integrate data products from other domains ([level 3](https://www.datamesh-architecture.com/#level-3-analyze-cross-domain-data), which may be skipped if not needed) and to publish data products for other domains ([level 4](https://www.datamesh-architecture.com/#level-4-publish-data-as-a-product)). The system’s data need to be exported to the data platform and managed as data products, conforming the global policies. As data models evolve with system updates, an anti-corruption layer is a must, e.g., as a cleaning step.

#### How might externally acquired datasets be part of a data mesh?[](https://www.datamesh-architecture.com/#how-might-externally-acquired-datasets-be-part-of-a-data-mesh)

Typical examples: Price-Databases or Medical Studies. A team needs to own this dataset and bring it into the datamesh. If this is not a very technical team, the data-platform should offer an easy self-service to upload files and provide Meta-Data. An Excel API or Google Sheets might also be an option here.

#### How might you explain the value of domain teams doing data analysis over delivering user-facing product improvements, especially when data analysts already analyse the data elsewhere in the company?[](https://www.datamesh-architecture.com/#how-might-you-explain-the-value-of-domain-teams-doing-data-analy)

From our experience, this question does not occur in data-driven organizations, where every product improvement is evaluated with data. So, you might face a culture issue here. How important are data-driven decisions for your company?

#### How did you draw the diagrams?[](https://www.datamesh-architecture.com/#how-did-you-draw-the-diagrams)

We got this question quite a lot, so we are happy to share our tooling:  
We use [diagrams.net](https://www.diagrams.net/)  with "Sketch" style and [Streamline Icons](https://streamlinehq.com/) . We automate the conversion to PNG, SVG and WebP with a little [script](https://github.com/datamesh-architecture/datamesh-architecture.com/blob/main/convert).

#### What are your questions?[](https://www.datamesh-architecture.com/#what-are-your-questions)

If you have any more questions, we encourage you to [discuss with us on GitHub](https://github.com/datamesh-architecture/datamesh-architecture.com/discussions) or [reach out to us directly](https://www.datamesh-architecture.com/#authors). But be warned: Your question might end up in the FAQ. :-)

## Learn more[](https://www.datamesh-architecture.com/#learn-more)

Scott started the Data Mesh Learning community [website](https://datameshlearning.com/), a [Slack channel](https://launchpass.com/data-mesh-learning), and issues a [newsletter](https://datameshlearning.substack.com/) every two weeks. He collects articles and experience reports about data mesh, and even has a [podcast](https://daappod.com/data-mesh-radio/) on the topic. It is worth subscribing to stay informed.

In this article, Zhamak Dehghani introduced the idea and core principles of data mesh. It is a must-read for everyone in this field. In her [follow-up article](https://martinfowler.com/articles/data-mesh-principles.html), Zhamak gets into more detail.

Zhamak's book about data mesh. The book not only discusses the principles of data mesh, but also presents an execution strategy.

Data Mesh in Action is a great hands-on book. We really liked the MVP hat shows how to start implementing a data mesh.

In this article, our colleague Philipp gives a nice introduction on how to identify data products using event-storming.

## Contributors[](https://www.datamesh-architecture.com/#contributors)

A ton of people helped us curate our content through their great feedback. Special thanks to: Anja Kammer, Benedikt Stemmhildt, Benjamin Wolf, Eberhard Wolff, Gernot Starke, Jan Schwake, Julian Schikarski, Jörg Müller, Markus Harrer, Matthias Geiger, Philipp Beyerlein, Rainer Jaspert, Stefan Tilkov, Tammo van Lessen, and Theo Pack.

And if you have feedback for us as well, feel free to [discuss with us on GitHub](https://github.com/datamesh-architecture/datamesh-architecture.com/discussions) or [reach out to us directly](https://www.datamesh-architecture.com/#authors)!