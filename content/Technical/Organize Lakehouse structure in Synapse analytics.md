---
tags:
  - Data
  - Data_Architecture
  - EA_Data
  - Data_Lake
  - Analytics
---
## Overview
The lakehouse pattern enables you to keep a large amount of your data in Data Lake and to get the analytic capabilities without a need to move your data to some data warehouse to start an analysis. A lakehouse represents a good trade-off between query performance and the ability to access the latest version of data without the need to wait for data to be reloaded.

Azure Synapse Analytics workspace enables you to implement the Lakehouse pattern on top of Azure Data Lake storage.

When you think about your lakehouse solution, be aware that there are two options for creating databases over the lake:

-   **Lake databases** that are created using Spark or database template
-   **SQL databases** that are created using serverless SQL pools on top of data lake.

Although you might use different tools and languages to create these types of databases, the principles described in this article apply to both types. I will use the term "lakehouse" whenever i reference Spak Lake database or SQL database created using the serverless SQL pools.

While designing the Lakehouse solution, you should carefully organize your databases and tables based on the underlying folder structure. In this article, you will find some best practices and recommendations that can help you to organize your lakehouses if you are using Synapse Analytics workspace to implement them.

## **Deploying synapse workspace**

Azure Synapse Analytics enables you to use T-SQL (Transact-SQL) and Spark languages to implement a Lakehouse pattern and access your data in the lake. The first step that you need to take is to create a Synapse Analytics workspace service.

You can easily [create your workspaces using the Azure Deployment Template](https://docs.microsoft.com/azure/synapse-analytics/quickstart-deployment-template-workspaces) available on the [Azure Synapse samples GitHub repository](https://github.com/Azure-Samples/Synapse/tree/main/Manage/DeployWorkspace). In this section, we will discuss some naming conventions that you can use with this template.

By using this template, you will see the following form where you can deploy a new workspace on top of the existing Azure Data Lake Storage (or the storage will be created as a part of the creation process).

![thumbnail image 1 of blog post titled 
The best practices for organizing Synapse workspaces and lakehouses
](https://techcommunity.microsoft.com/t5/image/serverpage/image-id/329200i3CE6D547D380765C/image-size/large?v=v2&px=999)

When you fill in this form, you should have in mind some best practices:

-   You need to have **a unique name for your workspace**. The workspace name must be globally unique, so you might add your company name (e.g., Contoso) as a workspace prefix to differentiate it from the others. You can also use some suffixes to differentiate different departments (HR, Finance, Sales), groups, or teams who are using the workspaces within your company. You might use some [recommended prefixes like syn- or synw-](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/azure-best-practices/resource-abbreviations#databases), or suffixes like **\-ws** or **\-workspace**, to classify the resource. Just note that you would need to use all these prefixes in any connection string, so longer names will be harder to write.
    -   Use dash separator (-) to separate the prefix, complex name, and suffix, to improve readability.
    -   If you are using workspaces in different regions, a good practice might be to put the region code (weu2, eus1) in the workspace and storage account name. This way you will easily verify that you are not dislocating the workspace and the underlying storage.
-   Prefer to use a single storage account for the workspaces in the same region (note that you can use additional storage account for data if needed). Using separate Data Lakes for different workspaces might unnecessarily increase the complexity, without benefit. You can configure permissions on a single shared Data Lake storage account to ensure who is accessing data. Use separate default storages for the workspaces only if you have some company/security/privacy policy or other reason to do this.

The default assumption should be that there should be multiple workspaces in the same region referencing a single Data Lake. The workspaces might reference different Data Lake storages, but this should be an exception. Try to follow **multiple-workspaces-single-lake** idea whenever it is applicable, and use multile lakes if you have some special requirements that are explained in the next section.

### When to use multiple Data Lakes?

You should use one shared Data Lake for multiple workspaces. The important decision is should you place your data in a single Data Lake or place it into multiple storage account.

and you can also place data in that shared Data Lake.

One shared lake for the workspaces extremely simplifies management, sharing, and security configuration. One data lake should satisfy your data size requirement, but there are other characteristics such as security, geo-redundancy, or bandwidth, that might force you to place some parts of your data into multiple accounts.

-   If your workspaces are placed in different regions, you should use a collocated data lake placed in the same region as the workspace. Only the workspaces in the same region should share the same data lake.
-   If your data sets require different security settings or geographical distribution, you should place them into separate accounts. You might need to balance cost/availability by placing your bronze data [locally redundant storage](https://docs.microsoft.com/en-us/azure/storage/common/storage-redundancy#locally-redundant-storage) and gold data in [zone-redundant-storage](https://docs.microsoft.com/en-us/azure/storage/common/storage-redundancy#zone-redundant-storage), you might need to put private endpoints on some data sets, while keeping other without private endpoints. Some data should be accessed using Azure AD passthrough, while you might need to protect other data with the service principals. If you believe that there might be different physical or security configurations for some parts of your data sets, move them into different storage accounts. It might be hard to make this kind of movement when you load petabytes of data.
-   If you are hitting some physical limits of data lake like a throughput you would need to move your critical data into a separate storage account.
-   In many cases, you might need to have separate data lakes for bronze, silver, and gold data.

Azure Could Adoption Framework recommends using [three different storage accounts](https://docs.microsoft.com/azure/cloud-adoption-framework/scenarios/data-management/best-practices/data-lake-services) for raw, enriched/curated, and workspace zones. This way you might organize your workspaces and assign them to the different zones.

![thumbnail image 2 of blog post titled 
The best practices for organizing Synapse workspaces and lakehouses
](https://techcommunity.microsoft.com/t5/image/serverpage/image-id/329547i2772B7CAB7809492/image-size/large?v=v2&px=999)

Some workspaces might be dedicated to the Raw and Curated/Enriched zones. Some workspaces might reference both Raw and Curated/Enriched or Curated/Enriched and Workspace zone to move the data. Then you might have the workspaces associated directly to the Workspace zone.

As you might see, increasing the number of Data Lake storages might improve performance/security, but also might complicate the management of the links from the workspaces to the storage accounts.

This configuration does not affect the Spark/SQL pools in Synapse and will not introduce any perf impact. Synapse Spark and SQL pools enable you to work with multiple storages from a single workspace. You can create your Lakehouse database over multiple storage or CosmoosDB accounts and create tables/views that reference data in different storage accounts. Lakehouse databases will abstract the access to the storage and the clients will not see any difference while accessing different storage. However, increasing the number of storage account might increase the complexity of your solution. You would need to explicitly create linked services/external data sources, and keep them in sync on all workspaces, refresh credentials if you are using SAS tokens, etc.  You need to balance between scalability and configuration that provide multiple accounts and complexity of management on the multiple storages. The recommendations and the best practices for these scenarios cannot be covered in this article.

## **Organize your workspaces**

A workspace is a collection of lakehouse databases that are exposing Data Lake files, scripts/notebooks, and other artifacts that you are using to analyze data. Data Lake should be able to store all data that you need in a single region. Let's use the simplest solution where have one Data Lake and point multiple workspaces to the same lake.

![thumbnail image 3 of blog post titled 
The best practices for organizing Synapse workspaces and lakehouses
](https://techcommunity.microsoft.com/t5/image/serverpage/image-id/329208iB7342FDA6E791635/image-size/medium?v=v2&px=400)

Imagine a workspace as a "project" where you create Lakehouse databases, scripts, notebooks, and all other artifacts that engineers and analysts will need to use. The underlying data lake contains the real data.

If the workspaces share the same data lake, they need to have separate folders for the workspace-specific data. Therefore, you should have a separate Data Lake container for each workspace within the data lake that will contain workspace-specific data.

Under the assumption that the ContosoDataLakeStorage is one Data Lake used by multiple workspaces in Contoso company, you should have the Data Lake containers that match workspace names.

Having separate containers for the workspace-level data still enables you to easily share the data between the workspaces. All workspace containers will automatically appear in the Synapse Studio and be available for querying.

![thumbnail image 4 of blog post titled 
The best practices for organizing Synapse workspaces and lakehouses
](https://techcommunity.microsoft.com/t5/image/serverpage/image-id/329201iB96CD153243B25A3/image-size/large?v=v2&px=999)

Synapse Studio will clearly mark the primary container for the current workspace and show the containers for the other workspaces. You can easily access data placed in other workspaces if you have permission.

With the **multiple-workspaces-single-lake** schema, all workspaces can easily access other workspace data and implement easy data sharing, while the security and the access right are controlled at the storage layer.

You might have some scenarios where you would like to put your data on a separate storage account to avoid the possibility that someone will accidentally access sensitive data. In that case, make sure that you are also using different workspaces that the end-users will use to analyze data. The workspaces within the same region should be grouped by underlying data lakes. This pattern enables multiple workspaces to easily share the data.

## **Organize your storage**

It is important to organize your Data Lake storage and choose the proper folder hierarchy to organize your data. Placing the data into the deeply nested subfolders might cause some issues when you look at the data and try to figure out does the folder contains a table, partition, or multiple tables.

You should consistently use something like a three-level hierarchy structure, shown in the following figure:

![thumbnail image 5 of blog post titled 
The best practices for organizing Synapse workspaces and lakehouses
](https://techcommunity.microsoft.com/t5/image/serverpage/image-id/329202i42B83FD3D9BD9455/image-size/large?v=v2&px=999)

Within the Data Lake you should have a three-level hierarchy:

-   On the first level, you should have the containers that represent the workspaces associated with the shared Data Lake storage.
-   Within each workspace container you should have lakehouse folders that represent the databases that contain metadata.
-   Within each lakehouse folder, you should have table folders. Every table folder contains a set of files, with uniform schema/partitioning and can be represented as a single table.

You might want to introduce additional folder levels between the lakehouse-level folders and table-level folders to group the tables. This folder level could be easily mapped to schemas in SQL pools. Synapse SQL pools enable you to use a 3-part-name in the format database.schema.table. The SQL schema can be easily mapped to this additional layer. However, since Spark does not support 3-part-names, you might have a problem if you want to process this structure with Spark.

## **Organize your lakehouses**

Lakehouses are databases created on top of some Data Lake folders that contain meta-data about the different data sets that you want to analyze. Every dataset should have a uniform schema so it can be represented as a table. You should create a separate folder within your workspace container for each lakehouse in your workspace.

This way you can easily establish 1:1 mapping between your workspace lakehouses/databases and “lakehouse folders”:

![thumbnail image 6 of blog post titled 
The best practices for organizing Synapse workspaces and lakehouses
](https://techcommunity.microsoft.com/t5/image/serverpage/image-id/329203i5FA595EFC60FB480/image-size/large?v=v2&px=999)

If you are analyzing Green and Yellow taxi data in TaxiLakehouse, you should have TaxiLakehouse folder that will contain all green and yellow taxi files. You might match the names of folders and databases, or you can add a suffix Lakehouse to each folder/database.

Make sure that you have a 1:1 relationship between your lakehouse databases and the lakehouse folders. This way you will be able to easily find the tables that are referencing the folders. You might even create the lakehouses for staging folders where you are ingesting initial data or refining data (for example bronze or silver folders). In many situations, you might need to create tables or views on top of staging data, and you should know where to locate the tables that are referencing the staging data.

**You just need to decide if you would use SQL or Spark to create the lakehouses on your Data Lake folder. You can create a "Lake database" using Spark or database templates and this database will be analyzed with T-SQL. Another option is to create an SQL database with the serverless SQL pool, but this lakehouse will not be available in Spark.**

If you create a lake database using the Spark pool in Synapse, that lakehouse database will be immediately available for querying with the serverless SQL pool, but it will be read-only. You will be able to analyze your lake databases using the T-SQL language in serverless SQL pools but not to change them. This way you can do data engineering with Spark and serving with SQL – this is the default Lakehouse database setup in Synapse.

![thumbnail image 7 of blog post titled 
The best practices for organizing Synapse workspaces and lakehouses
](https://techcommunity.microsoft.com/t5/image/serverpage/image-id/329206iAD1B6F56B8C16E88/image-size/large?v=v2&px=999)

You can also create a SQL database over your lake using the serverless SQL pools that will be shown as a SQL database in the Synapse Studio. If you create a SQL database that represents your Lakehouse, that lakehouse will be fully managed using SQL language, but will not be available in Spark. In this type of SQL lakehouse, you will have full T-SQL experience both for engineering and analytics, but the engineering features that are available in SQL cannot be compared with Spark features.

## **Organize your tables**

Within the lakehouse folders, you should place a layer of folders that represent your data. If you have the tables GreenTaxi, YellowTaxi, and Population in the TaxiLakehouse, you should have the matching folders in the TaxiLakehouse folder.

![thumbnail image 8 of blog post titled 
The best practices for organizing Synapse workspaces and lakehouses
](https://techcommunity.microsoft.com/t5/image/serverpage/image-id/329204i236E1296E425BC1A/image-size/large?v=v2&px=999)

Matching database artifacts and folder hierarchies will enable you to easily locate the data and the database artifacts that reference them.

Even if you have a single file (for example population.parquet) that could be represented as a table, make sure that you are placing it into a separate folder. In the future, you might need to replace it with multiple files, add more files, or even organize the files in some partition folder structure. Therefore, it is better to hide the physical organization within the table-level folder, reference the folder from an external table and make all physical changes within the folder without major refactoring of the tables.

Table folders might contain a single file, a set of files, or even hierarchically organized folders that represent partitioned data. The physical organization of the files should be encapsulated with the table-level folder.

## **Conclusion**

It is especially important to organize your data lake storage to match the structure of your workspaces, lakehouses, and tables. This way you would avoid a mess where different database artifacts might reference scattered folders and files.

If you organize your data lake folders as workspace/lakehouse/table hierarchy, you can easily identify where your data is stored and how it is organized.

Microsoft has published guidance on scalable data management and analytics which incorporates the building practices of the cloud adoption framework as well as aligning to well-architected framework principles. The guidance above can be adapted to work within this, and we recommend looking at the following articles:

-   [Azure data management and analytics scenario overview](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fcloud-adoption-framework%2Fscenarios%2Fdata-management%2F&data=04%7C01%7Cjovanpop%40microsoft.com%7Cbe2bfb893977486b036808d9b0d0fed7%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637735233940534842%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C3000&sdata=om95%2B203SWYAoaJKrJztOoLVetsxf5orTWLOV3mdvmA%3D&reserved=0)
-   [Data Management and Analytics Scenario Multiple Lakes](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fcloud-adoption-framework%2Fscenarios%2Fdata-management%2Fbest-practices%2Fdata-lake-overview%2523the-three-data-lakes&data=04%7C01%7Cjovanpop%40microsoft.com%7Cbe2bfb893977486b036808d9b0d0fed7%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637735233940534842%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C3000&sdata=LbmGhj922hURZSVZewKj5XRck4LIS0el2dzN3eKaKJs%3D&reserved=0)
-   [Access control and data lake configurations in Azure Data Lake Storage Gen2](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fcloud-adoption-framework%2Fscenarios%2Fdata-management%2Fbest-practices%2Fdata-lake-access&data=04%7C01%7Cjovanpop%40microsoft.com%7Cbe2bfb893977486b036808d9b0d0fed7%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637735233940544837%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C3000&sdata=m7qnK9bFBRRhtbo5NWelepzpdEINl0V4gk2m0wuN4AA%3D&reserved=0)
-   [Data Lake Zones](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fcloud-adoption-framework%2Fscenarios%2Fdata-management%2Fbest-practices%2Fdata-lake-services&data=04%7C01%7Cjovanpop%40microsoft.com%7Cbe2bfb893977486b036808d9b0d0fed7%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637735233940554828%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C3000&sdata=n2D9o9NzDSNGT2iv3CqVPK8PT%2FlqEI6xwA%2B2dKhjuHQ%3D&reserved=0)