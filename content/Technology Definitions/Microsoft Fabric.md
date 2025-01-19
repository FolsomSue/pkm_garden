---
tags:
  - Fabric
  - Data_Fabric
  - Data_Platform
  - Data_Pipeline
  - Data_Lake
  - Analytics
  - EA_Data
  - Microsoft
  - Azure
  - definition
---
**What is Microsoft Fabric?**

Article • 05/21/2024

https://learn.microsoft.com/en-us/fabric/get-started/media/microsoft-fabric-overview/onelake-architecture.png#lightbox
![[Pasted image 20241004105012.png]]
Microsoft Fabric is an end-to-end analytics and data platform designed for enterprises that require a unified solution. It encompasses data movement, processing, ingestion, transformation, real-time event routing, and report building. It offers a comprehensive suite of services including Data Engineering, Data Factory, Data Science, Real-Time Analytics, Data Warehouse, and Databases.

With Fabric, you don't need to assemble different services from multiple vendors. Instead, it offers a seamlessly integrated, user-friendly platform that simplifies your analytics requirements. Operating on a Software as a Service (SaaS) model, Fabric brings simplicity and integration to your solutions.

Microsoft Fabric integrates separate components into a cohesive stack. Instead of   
relying on different databases or data warehouses, you can centralize data storage with OneLake. AI capabilities are seamlessly embedded within Fabric, eliminating the need   
for manual integration. With Fabric, you can easily transition your raw data into actionable insights for business users.

**Unification with SaaS foundation**

Microsoft Fabric is built on a foundation of Software as a Service (SaaS). It combines both new and existing components from Power BI, Azure Synapse Analytics, Azure Data Factory, and more services into a unified environment. These components are then tailored into customized user experiences.

![](media/b509708711273df0505d0920f2d1f57d.png)

[](https://learn.microsoft.com/en-us/fabric/get-started/media/microsoft-fabric-overview/fabric-architecture.png#lightbox)

Fabric integrates workloads such as Data Engineering, Data Factory, Data Science, Data Warehouse, Real-Time Intelligence, Industry solutions, and Power BI into a shared SaaS foundation. Each of these experiences is tailored for distinct user roles like data

engineers, scientists, or warehousing professionals, and they serve a specific task. The entire Fabric stack has AI integration and it accelerates the data journey. These workloads work together seamlessly and provide the following advantages:

Access to an extensive range of deeply integrated analytics in the industry.   
Shared experiences across experiences that are familiar and easy to learn.

Easy access to, and readily reuse all assets.

Unified data lake storage that preserves data in its original location while using your preferred analytics tools.

Centralized administration and governance across all experiences.

Fabric seamlessly integrates data and services, enabling unified management, governance, and discovery. It ensures security for items, data, and row-level access. You can centrally configure core enterprise capabilities. Permissions are automatically applied across all the underlying services. Additionally, data sensitivity labels inherit automatically across the items in the suite. Governance is powered by Purview which is built into Fabric.

Fabric allows creators to concentrate on producing their best work, freeing them from the need to integrate, manage, or even understand the underlying infrastructure.

**Components of Microsoft Fabric**

Fabric offers a comprehensive set of analytics experiences designed to work together seamlessly. The platform tailors each of these experiences to a specific persona and a ![](media/fe3a5a7f130e772e67719d99702e2c4c.png)specific task:

**Power BI** - Power BI lets you easily connect to your data sources, visualize and discover what's important, and share that with anyone or everyone you want. This integrated experience allows business owners to access all data in Fabric quickly   
and intuitively and to make better decisions with data. For more information, see [What is Power BI?](https://learn.microsoft.com/en-us/power-bi/fundamentals/power-bi-overview)

**Data Factory** - Data Factory provides a modern data integration experience to ingest, prepare, and transform data from a rich set of data sources. It incorporates the simplicity of Power Query, and you can use more than 200 native connectors to connect to data sources on-premises and in the cloud. For more information, see [What is Data Factory in Microsoft Fabric?](https://learn.microsoft.com/en-us/fabric/data-factory/data-factory-overview)

**Data Activator** - Data Activator is a no-code experience in Fabric that allows you to specify actions, such as email notifications and Power Automate workflows, to launch when Data Activator detects specific patterns or conditions in your

changing data. It monitors data in Power BI reports and eventstreams; when the data hits certain thresholds or matches other patterns, it automatically takes the appropriate action. For more information, see [What is Data Activator?](https://learn.microsoft.com/en-us/fabric/data-activator/data-activator-introduction)

**Industry Solutions** - Fabric provides industry-specific data solutions that address unique industry needs and challenges, and include data management, analytics,   
and decision-making. For more information, see [Industry Solutions in Microsoft](https://learn.microsoft.com/en-us/industry/industry-data-solutions-fabric) [Fabric](https://learn.microsoft.com/en-us/industry/industry-data-solutions-fabric).

**Real-Time Intelligence** - Real-time Intelligence is an end-to-end solution for event-driven scenarios, streaming data, and data logs. It enables the extraction of insights, visualization, and action on data in motion by handling data ingestion, transformation, storage, analytics, visualization, tracking, AI, and real-time actions. The Real-Time hub in Real-Time Intelligence provides a wide variety of no-code connectors, converging into a catalog of organizational data that is protected, governed, and integrated across Fabric. For more information, see [What is Real-](https://learn.microsoft.com/en-us/fabric/real-time-intelligence/overview) [Time Intelligence in Fabric?](https://learn.microsoft.com/en-us/fabric/real-time-intelligence/overview).

**Synapse Data Engineering** - Synapse Data Engineering provides a Spark platform with great authoring experiences. It enables you to create, manage, and optimize infrastructures for collecting, storing, processing, and analyzing vast data volumes. Fabric Spark's integration with Data Factory allows you to schedule and orchestrate notebooks and Spark jobs. For more information, see [What is Data engineering in](https://learn.microsoft.com/en-us/fabric/data-engineering/data-engineering-overview) [Microsoft Fabric?](https://learn.microsoft.com/en-us/fabric/data-engineering/data-engineering-overview)

**Synapse Data Science** - Synapse Data Science enables you to build, deploy, and operationalize machine learning models from Fabric. It integrates with Azure Machine Learning to provide built-in experiment tracking and model registry. Data

scientists can enrich organizational data with predictions and business analysts can integrate those predictions into their BI reports, allowing a shift from descriptive to predictive insights. For more information, see [What is Data science in Microsoft](https://learn.microsoft.com/en-us/fabric/data-science/data-science-overview)

[Fabric?](https://learn.microsoft.com/en-us/fabric/data-science/data-science-overview)

**Synapse Data Warehouse** - Synapse Data Warehouse provides industry leading   
SQL performance and scale. It separates compute from storage, enabling independent scaling of both components. Additionally, it natively stores data in   
the open Delta Lake format. For more information, see [What is data warehousing](https://learn.microsoft.com/en-us/fabric/data-warehouse/data-warehousing)   
[in Microsoft Fabric?](https://learn.microsoft.com/en-us/fabric/data-warehouse/data-warehousing)

Microsoft Fabric enables organizations and individuals to turn large and complex data repositories into actionable workloads and analytics, and is an implementation of data mesh architecture. For more information, see [What is a data mesh?](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/scenarios/cloud-scale-analytics/architectures/what-is-data-mesh)

**OneLake: The unification of lakehouses**

The Microsoft Fabric platform unifies the OneLake and lakehouse architecture across an enterprise.

**OneLake**

A data lake is the foundation on which all the Fabric workloads are built. Microsoft   
Fabric Lake is also known as [OneLake](https://learn.microsoft.com/en-us/fabric/onelake/onelake-overview). OneLake is built into the Fabric platform and provides a unified location to store all organizational data where the workloads operate.

OneLake is built on ADLS (Azure Data Lake Storage) Gen2. It provides a single SaaS experience and a tenant-wide store for data that serves both professional and citizen developers. OneLake simplifies Fabric experiences by eliminating the need for you to understand infrastructure concepts such as resource groups, RBAC (Role-Based Access Control), Azure Resource Manager, redundancy, or regions. You don't need an Azure account to use Fabric.

OneLake eliminates data silos, which individual developers often create when they provision and configure their own isolated storage accounts. Instead, OneLake provides   
a single, unified storage system for all developers. It ensures easy data discovery,   
sharing, and uniform enforcement of policy and security settings. For more information, see [What is OneLake?](https://learn.microsoft.com/en-us/fabric/onelake/onelake-overview)

**OneLake and lakehouse data hierarchy**

OneLake is hierarchical in nature to simplify management across your organization. Microsoft Fabric includes OneLake and there's no requirement for any up-front provisioning. There's only one OneLake per tenant and it provides a single-pane-of-   
glass file-system namespace that spans across users, regions, and clouds. OneLake organizes data into manageable containers for easy handling.

The tenant maps to the root of OneLake and is at the top level of the hierarchy. You can create any number of workspaces, which you can think of as folders, within a tenant.

The following image shows how Fabric stores data in various items within OneLake. As shown, you can create multiple workspaces within a tenant, and create multiple lakehouses within each workspace. A lakehouse is a collection of files, folders, and tables that represents a database over a data lake. To learn more, see [What is a lakehouse?](https://learn.microsoft.com/en-us/fabric/data-engineering/lakehouse-overview).

![](media/14fbffcb7301035468ade69490126b9d.png)

Every developer and business unit in the tenant can easily create their own workspaces in OneLake. They can ingest data into their own lakehouses, then start processing, analyzing, and collaborating on the data, just like OneDrive in Microsoft Office.

All the Microsoft Fabric compute experiences are prewired to OneLake, just like the Office applications are prewired to use the organizational OneDrive. The experiences such as Data Engineering, Data Warehouse, Data Factory, Power BI, and Real-Time Intelligence use OneLake as their native store. They don't need any extra configuration.

![](media/cdfb5903a8444e54669cce9cf8c61c04.png)

[](https://learn.microsoft.com/en-us/fabric/get-started/media/microsoft-fabric-overview/onelake-architecture.png#lightbox)

OneLake allows instant mounting of your existing Platform as a Service (PaaS) storage accounts into OneLake with the [Shortcut](https://learn.microsoft.com/en-us/fabric/onelake/onelake-shortcuts) feature. You don't need to migrate or move any of your existing data. Using shortcuts, you can access the data stored in your Azure Data Lake Storage.

Shortcuts also allow you to easily share data between users and applications without moving or duplicating information. You can create shortcuts to other storage systems, allowing you to compose and analyze data across clouds with transparent, intelligent caching that reduces egress costs and brings data closer to compute.

**Real-Time hub - the unification of data streams**

The Real-Time hub is a foundational location for data in motion.

The Real-Time hub provides a unified SaaS experience and tenant-wide logical place for all data-in-motion. The Real-Time hub lists all data in motion from all sources that customers can discover, ingest, manage, and consume and react upon, and contains both [streams](https://learn.microsoft.com/en-us/fabric/real-time-intelligence/event-streams/overview) and [KQL database](https://learn.microsoft.com/en-us/fabric/real-time-intelligence/create-database) tables. Streams includes [**Data streams**](https://learn.microsoft.com/en-us/fabric/real-time-intelligence/event-streams/create-manage-an-eventstream), **Microsoft** **sources** (for example, [Azure Event Hubs](https://learn.microsoft.com/en-us/fabric/real-time-hub/add-source-azure-event-hubs), [Azure IoT Hub](https://learn.microsoft.com/en-us/fabric/real-time-hub/add-source-azure-iot-hub), [Azure SQL DB Change Data](https://learn.microsoft.com/en-us/fabric/real-time-hub/add-source-azure-sql-database-cdc) [Capture (CDC)](https://learn.microsoft.com/en-us/fabric/real-time-hub/add-source-azure-sql-database-cdc), [Azure Cosmos DB CDC](https://learn.microsoft.com/en-us/fabric/real-time-hub/add-source-azure-cosmos-db-cdc), and [PostgreSQL DB CDC](https://learn.microsoft.com/en-us/fabric/real-time-hub/add-source-postgresql-database-cdc)), and [**Fabric events**](https://learn.microsoft.com/en-us/fabric/real-time-intelligence/event-streams/add-source-fabric-workspace) (Fabric system events and external system events brought in from Azure, Microsoft 365, or other clouds).

The Real-Time hub enables users to easily discover, ingest, manage, and consume data- in-motion from a wide variety of source so that they can collaborate and develop

streaming applications within one place. For more information, see [What is the Real-](https://learn.microsoft.com/en-us/fabric/real-time-hub/real-time-hub-overview) [Time hub?](https://learn.microsoft.com/en-us/fabric/real-time-hub/real-time-hub-overview)

**Fabric solutions for ISVs**

If you're an Independent Software Vendors (ISVs) looking to integrate your solutions   
with Microsoft Fabric, you can use one of the following paths based on your desired   
level of integration:

**Interop** - Integrate your solution with the OneLake Foundation and establish basic connections and interoperability with Fabric.

**Develop on Fabric** - Build your solution on top of the Fabric platform or seamlessly embed Fabric's functionalities into your existing applications. You can easily use Fabric capabilities with this option.

**Build a Fabric workload** - Create customized workloads and experiences in Fabric tailoring your offerings to maximize their impact within the Fabric ecosystem.

For more information, see the [Fabric ISV partner ecosystem](https://learn.microsoft.com/en-us/fabric/cicd/partners/partner-integration).

**Related content**

Microsoft Fabric terminology

Create a workspace

Navigate to your items from Microsoft Fabric Home page End-to-end tutorials in Microsoft Fabric
