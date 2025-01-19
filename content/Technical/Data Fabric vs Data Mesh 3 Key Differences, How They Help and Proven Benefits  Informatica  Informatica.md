![](https://www.informatica.com/content/dam/informatica-com/en/blogs/uploads/2021/blogs/b09/b09-data-fabric-vs-data-mesh-3-key-differences-how-they-help-and-proven-benefits.jpg)

Monolithic, legacy architectures and centralized data platforms thwart business’ agility, making it difficult to quickly adjust to the constantly changing data landscape that demands new views, new aggregations, and new projections of the data (aka data products). Both data fabric and data mesh architectures aim to abstract data management complexity and deliver data to the business with agility and scale.

Organizations relying on legacy architectures are struggling to scale data and analytics given the following challenges:

-   Data proliferation and complexity – Increasing data domains (e.g., Product, Supply Chain, Marketing), data consumers, and data sources
-   Lack of agility – Inability to meet data demands in a timely manner  
    
-   Lack of collaboration – Data developers siloed from the domains where the data originates or is used for decision making
-   Lack of trust in data resulting from multiple copies of varying instances of the same data

These challenges hinder organizations from becoming truly data-driven and responding to business demands fast. Although these challenges are not entirely new to the data landscape, they have assumed greater importance as organizations strive to accelerate digital transformation.

Previous approaches to overcome these challenges include semantic layers, data virtualization, and data as a service (a data management strategy aiming to leverage data as a business asset for greater business agility). The objectives of these logical architectures are to scale the delivery of data to satisfy diverse use cases and, most importantly, provide the agility to respond quickly to changing business needs. The data fabric architecture addresses the rising complexity of data management by intelligently integrating and connecting an organization’s data and making reusable data assets available for consumption. Data mesh is an emerging architecture that furthers data fabric objectives. Let’s dive a bit deeper.  

## What is a data fabric?  

[Data fabric](https://www.informatica.com/resources/articles/data-fabric-the-transformative-next-step-in-data-management.html) is a design concept and architecture geared toward addressing the complexity of data management and minimizing disruption to data consumers while ensuring that any data on any platform from any location can be successfully combined, accessed, shared, and governed efficiently and effectively. A data fabric architecture is enabled by AI/ML-driven augmentation and automation, an intelligent [metadata foundation](https://www.informatica.com/products/informatica-platform/metadata-management.html), and a strong technology backbone (i.e., cloud-native, microservices-based, API-driven, interoperable, and elastic.).

## What is a data mesh?  

Data mesh focuses on organizational change – enabling domain teams to own the delivery of data products with the understanding that the domain teams are closer to their data and thus understand their data better.

Positioned by Zhamak Dehghani, a Thoughtworks consultant, in May of 2019 to provide a modern definition of the term, data mesh is a type of data platform architecture that embraces the ubiquity of data in the enterprise by leveraging a domain-oriented, self-serve design. It enables data consumers to discover, understand, trust, and use data/data products (distributed across different domains) to drive data-driven decisions and initiatives.

Just as engineering teams transitioned from monolithic applications to microservice architectures, data teams view data mesh as a prime opportunity to transition from monolithic data platforms to data microservices (business contextual services) architecture.

Core to data mesh is the concept of breaking apart the monolithic architecture and monolithic kind of custodianship or ownership of the data around domains in the organization. [Data warehouses](https://www.informatica.com/resources/articles/what-is-a-data-warehouse.html) and [data lakes](https://www.informatica.com/resources/articles/how-data-lakes-can-help-your-business.html) can still exist in the mesh architecture, but they become just another node in the mesh, rather than a centralized monolith. 

Data mesh advocates distributed, domain-based ownership and custodianship of data and building data products that are self-described and atomic, more easily managed and delivered at the domain level. These data products are sharable with other domains and interoperable with other data products that form the data mesh. A data mesh manages data as a distributed network of self-describing data products.

## What are the 3 key differences between data fabric and data mesh?

Data fabric and data mesh each provides a data architecture that enables an integrated, connected data experience across a distributed, complex data landscape.

1.  Although both data fabric and data mesh deliver data products, data mesh advocates product thinking for data as a core design principle. As a result, data is maintained and provisioned like any other product in the organization with a data mesh.
2.  Where data fabric leverages automation in discovering, connecting, recognizing, suggesting, and delivering data assets to data consumers based on a rich enterprise metadata foundation (e.g., a knowledge graph), data mesh relies on data product/domain owners to drive the requirements up front for data products.
3.  A data mesh relies on organizational structure and culture change to achieve agility. Domain teams own delivery of data products with the understanding that they are closer to their data. This might be an added responsibility on top of their existing responsibilities. Data mesh advocates decentralization of data practitioners, like data scientists and data engineers, as part of the domain/data products teams.

## Data fabric benefits  

-   Integrates and connects all your organization’s data and facilitates frictionless data sharing for improved business outcomes
-   Accelerates self-service data discovery and analytics by making trusted data accessible faster to all data consumers
-   Reduces data management costs and efforts via intelligent automation of data management tasks
-   Delivers real-time analytics and insights by optimizing the data lifecycle and enabling flexible and faster data-driven application development

## Data mesh benefits  

-   Enables delivery of customized data products to meet business demands by linking strategic business objectives to an ecosystem of data products to drive value
-   Scales delivery of data products via decentralized ownership and domain-specific expertise, transforming organizational culture to a data product mindset
-    Improves agility by abstracting complexity and breaking down monolithic, centralized architectures that can be bottlenecks to meeting business demands for data in a timely manner
-   Enables a flexible data governance operating model with federated governance, allowing organizations to enhance the model to meet their unique needs

**How to realize data mesh benefits: Data mesh conceptual architecture**

Data mesh architecture introduces a shift in how [data analytics](https://www.informatica.com/resources/articles/what-is-data-analytics.html) is enabled in the enterprise, built upon the following design principles:

-   **_Domain-oriented decentralized_** _data ownership and architecture_ – Decentralize the ownership of sharing analytical data to business domains closest to the data, usually represented by either the source of the data or its main consumers.
-   **_Data as a product_** _–_ Hold existing or new business domains accountable for sharing their data as a product to data consumers by abstracting all the underlying complexity. Exposing data for multimodal access is a key to this principle. Data products should be discoverable, understandable, addressable, trustworthy, secure, interoperable, accessible, and valuable on their own.
-   **_Self-serve data infrastructure as a platform_** _–_ Enable a new generation of self-serve data infrastructure of choice to empower domain-oriented teams to manage the end-to-end data life cycle (from data acquisition to data democratization) of their data products.
-   **_Federated computational governance_** _–_ Provide federated data governance to ensure data is discoverable, accessible, secure, trusted, and reusable. Each of the data domain teams can manage the implementation of their own, local data products. Concurrently, there is a need for central data discovery, data marketplace, analytics, and auditing to facilitate finding relevant data by users.

## Data mesh adoption and key questions to consider  

There are few publicly available case study references to data mesh architecture implementation by companies. However, data mesh architecture is in the infancy stage of adoption. Its effectiveness has not been widely demonstrated for tangible business benefits, and best practices are still evolving.

**Questions to ask when evaluating data mesh architecture**

Organizations considering a data mesh architecture need to closely evaluate whether data mesh’s domain-oriented design approach is suitable for their needs. They need to ensure that the data products will be reused and fulfill the needs of both local and cross-domain/enterprise users. If you’re considering a data mesh architecture, ask questions like:

-   What is a good data product?
-   Who owns the data?
-   Will data standards be different for each domain?
-   Will it lower or increase costs?
-   How do I onboard new data products?
-   What does the [data governance operating model](https://www.informatica.com/resources/articles/data-governance-framework.html) look like?

Before implementing a data mesh architecture, enterprises need to consider multiple factors for each of the three dimensions identified below.

-   **People**: Data mesh can potentially create a burden for domain teams. Thus, an assessment of their skills, roles, responsibilities, and availability is necessary for establishing the appropriate team structure which will be a prerequisite for success. An organization’s culture is also an important consideration in determining if decentralized domain-based decision making is the optimal strategy.
-   **Process**: Creating data products does not imply that domain teams own the data itself. Rather, the teams assume the role of data custodians. Governance operating models, workflows, and KPIs (e.g., data product quality) for both local and federated governance should be clearly defined and require buy-in from appropriate stakeholders.
-   **Technology**: Enterprises need to carefully evaluate how to provision the self-serve data infrastructure at the domain level and the potential costs associated with it. Consideration such as governance policies, security standards, interoperability, risk assessments, DataOps, data lineage, data provisioning, cloud-native elastic and serverless deployments, and more will be necessary.

**To mesh or not to mesh?**

Since data mesh is an emerging architecture compared to data fabric, companies need to evaluate if data mesh is the appropriate architecture for their needs. In the following scenarios (not an exhaustive list), companies may not benefit significantly from a data mesh architecture:

-   Few data domains or data sources or data team members – applies to small and midsize companies
-   Scaling data delivery, meeting data demands are not issues
-   Centralized decision-making culture
-   Lack of budget for enabling domain-level self-serve data infrastructure
-   Centralization of data (e.g., data warehouse, data lake) is not a bottleneck in meeting data delivery requirements
-    Lack of skills and resources at the domain level to define and build data products

## The Intelligent Data Management Cloud enables data mesh and data fabric architecture 

**Domain-oriented ownership and architecture**: Intelligent Data Management Cloud enables a metadata-driven approach to building and scaling [data pipelines](https://www.informatica.com/resources/articles/data-pipeline.html) for any data consumer or producer. The Intelligent Data Management Cloud platform includes enterprise data catalog, data governance, and data privacy capabilities. This makes it easy for data producers and consumers to register or discover domain-specific, trusted datasets to use within their data pipelines.

**Data product**: The Intelligent Data Management Cloud enables enterprises to visualize, analyze, prepare, and collaborate on their data regardless of location, type, format, or the underlying source. It is a comprehensive cloud-native data management platform with data and [app integration](https://www.informatica.com/solutions/application-modernization.html), [data preparation](https://www.informatica.com/resources/articles/what-is-data-preparation.html), [data quality](https://www.informatica.com/products/data-quality.html), and [API management capabilities](https://www.informatica.com/resources/articles/api-management-and-informatica-intelligent-cloud-services.html), all in a single platform. This accelerates building data pipelines and delivering data products at scale. The Intelligent Data Management Cloud can expose data access via APIs or other modes of data access. It provides a data marketplace for both data suppliers and consumers to share, discover, and consume data products.

**Self-serve data infrastructure**: The Intelligent Data Management Cloud offers cloud-native, elastic self-serve data infrastructure with a low-code or no-code experience, allowing your team to go directly from ideation to implementation, responding to dynamic business requirements and changes in real time without the overhead of developing and maintaining code. The Intelligent Data Management Cloud platform includes purpose-built wizards and user experience for every type of user.

**Federated data governance**: The Intelligent Data Management Cloud has security and trust as a design principle rather than an afterthought. It offers the [highest industry standards for data security](https://www.informatica.com/trust-center.html). It offers an enterprise-scale catalog of catalogs and data privacy. It automates [data governance](https://www.informatica.com/resources/articles/what-is-data-governance.html) capabilities such as data-asset classification based on domains, data curation, policy linking and enforcement. These ensure that appropriate teams (producers/consumers) can quickly access and understand data and other artifacts like AI models and pipelines. The Intelligent Data Management Cloud ensures trust with consistent enterprise-wide data quality, protects data to minimize privacy risks, and facilitates regulatory compliance.

**Here is how the Intelligent Data Management Cloud supports data fabric architecture**

The Intelligent Data Management Cloud enables an intelligent data fabric across a distributed data landscape with an active metadata-based AI and ML engine, CLAIRE, that utilizes breadth of metadata to automate data integration and management tasks.

[Augmented data catalog](https://www.informatica.com/products/data-catalog.html) – AI-powered intelligent data catalog enables you to find, understand, and prepare all your data with AI-driven metadata discovery and data cataloging.

[Knowledge graph enriched with semantics](https://www.informatica.com/blogs/why-a-metadata-knowledge-graph-is-essential-to-an-intelligent-data-fabric.html) – Enterprise knowledge graph puts data in context by linking and enriching semantic metadata and inferencing to deliver intelligence to data management functions.

[Metadata activation and recommendation engine](https://www.informatica.com/about-us/claire.html) – AI-powered CLAIRE engine learns your data landscape to automate thousands of manual tasks and augment human activity with recommendations and insights.

[Data preparation and data delivery](https://www.informatica.com/products/data-integration.html) – Enterprise data preparation enables you to simplify and speed up the data preparation with advanced ML-based automation and data cataloging.

[Orchestration and DataOps](https://www.informatica.com/products/cloud-integration.html) – Enterprise orchestration and XOps enable automatic orchestration of all data delivery flows by employing DataOps, MLOps, and InfosecOps in support of continuous analysis and monitoring.

**Customer Story: HelloFresh Dials Up Data Analytics with a Data Mesh to Meet Demand**

HelloFresh is the world’s leading meal kit company. In 2020, the company more than doubled its annual revenue and met an unprecedented surge in demand for its meal kits during the pandemic. Key to this was scaling up data analytics and making it easy for employees to find key data to accelerate insights such as planning and forecasting cycles.

The company transitioned to a data mesh architecture to decentralize data ownership, enabling data consumers across the organization to easily find and understand relevant data. Data mesh architecture helps to scale data analytics as the company grows to keep customers happy, manage costs, and stay ahead of competitors.

With Informatica’s AI-powered Intelligent Data Management Cloud platform, HelloFresh democratized data, making it easier for more than 11,000 employees in 14 countries to find and use data. By automating the documentation of key data, the company created a single source of truth that is easy for users to discover, understand, and leverage for decision making.

Thanks to the data mesh architecture, HelloFresh was able to meet the unprecedented surge in demand for meal kits during COVID-19, [more than doubling annual revenue](https://www.informatica.com/about-us/customers/customer-success-stories/hellofresh.html).

**Customer Story: BMC Transforms Complex Technology into Extraordinary Business Performance with a Data Fabric**

BMC Software (BMC) helps companies harness technology to improve the delivery and consumption of digital services. The company’s accounts payable and generic ledger operations were handled by decentralized regional services centers using manual processes. This, in turn, caused a lack of standardization across countries, which impacted the BMC treasury team’s ability to view current account balances and resulted in the need to maintain excessive cash reserves to cover the possible occurrence of any unpredicted cash needs.

With Informatica, BMC built a functional system in a very short period of time and then layered on more sophisticated capabilities. The company dramatically improved visibility into actual and projected cash flows, enabling it to better manage cash positions and optimize the use of its working capital.

[BMC saved hundreds of thousands of dollars](https://www.informatica.com/it/about-us/customers/customer-success-stories/bmc-software.html) and has much better reporting and control across the hundreds of bank accounts. It now has accurate and timely visibility into its cash holdings and has been able to elevate the rigor behind its risk management and mitigation strategies.

## Future-proof your investment

Both data fabric and data mesh are revolutionary architectures that enable organizations to connect and deliver data across a distributed data landscape by abstracting the underlying complexity. Since data mesh is an emerging architecture, enterprises embarking on this path should carefully assess whether this is the right architecture for their organization.

Informatica is uniquely positioned to support both your data fabric and data mesh or any other architectures that might emerge in the future via our [Intelligent Data Management Cloud](https://www.informatica.com/platform.html), thus future-proofing your investments in data and analytics. [Explore our enterprise architecture center](https://www.informatica.com/enterprise-architecture.html) to take the next step in your modernization journey.