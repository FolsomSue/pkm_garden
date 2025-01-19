---
title: What is Azure Synapse ?
source: https://medium.com/microsoftazure/what-is-azure-synapse-e56f2a8b8d31
author:
  - "[[Patrick Alexander]]"
published: 2020-08-20
created: 2024-10-02
description: Azure Synapse is a limitless analytics service that brings together enterprise data warehousing and Big Data analytics. It gives you the freedom to query data on your terms, using either server-less…
tags:
  - EA_Data
  - Azure
  - Synapse
  - Data_Lake
  - Data_Pipeline
  - Data_Platform
  - Analytics
  - definition
  - Resources
---

Azure Synapse is a limitless analytics service that brings together enterprise data warehousing and Big Data analytics. It gives you the freedom to query data on your terms, using either server-less or provisioned resources at scale. Azure Synapse brings these two worlds together with a unified experience to ingest, prepare, manage, and serve data for immediate BI and machine learning needs.

Architecture and Design of a data warehouse depends on many factors. A dynamic and well performing DW should guaranty the data validity, concurrency, low latency and capability to integrate with other systems.

![](https://miro.medium.com/v2/resize:fit:875/1*PQj1_lausUVsL-pxsJSbqQ.png)

Azure Synapse provides you the platform to build and mange a modern DW with limitless analytics service that brings together enterprise data warehousing and Big Data analytics. It gives you the freedom to query data on your terms, using either server less on-demand or provisioned resources at scale.

Recently I had to work on a Synapse project and I collected the following references and now I’m sharing it with you.

**Cheatsheet**

- [https://docs.microsoft.com/en-us/azure/sql-data-warehouse/cheat-sheet](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fsql-data-warehouse%2Fcheat-sheet&data=02%7C01%7Cpaalexan%40microsoft.com%7Ce02a8d2cf38c43fcb21608d83ec7986b%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637328374306728951&sdata=ehRGw4IQjOdLrT%2Bh0rG%2F%2FxiZJ1I7MkGfyLiTEpIZb%2F0%3D&reserved=0)

**Best Practices**

- [https://docs.microsoft.com/en-us/azure/sql-data-warehouse/sql-data-warehouse-best-practices](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fsql-data-warehouse%2Fsql-data-warehouse-best-practices&data=02%7C01%7Cpaalexan%40microsoft.com%7Ce02a8d2cf38c43fcb21608d83ec7986b%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637328374306738941&sdata=Q2CHGce18yCct5T6uy57yR8Mq6YT%2FTwz73OrCSGcByg%3D&reserved=0)
- [https://docs.microsoft.com/en-us/azure/synapse-analytics/sql/best-practices-sql-pool](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fsynapse-analytics%2Fsql%2Fbest-practices-sql-pool&data=02%7C01%7Cpaalexan%40microsoft.com%7Ce02a8d2cf38c43fcb21608d83ec7986b%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637328374306738941&sdata=oH6EZHTGCLwWvOlot%2FUcMoe08ngeArQZNJJZFJ4WRWE%3D&reserved=0)
- [https://docs.microsoft.com/en-us/azure/synapse-analytics/sql/best-practices-sql-on-demand](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fsynapse-analytics%2Fsql%2Fbest-practices-sql-on-demand&data=02%7C01%7Cpaalexan%40microsoft.com%7Ce02a8d2cf38c43fcb21608d83ec7986b%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637328374306748942&sdata=KvmHR1QLUGXMjERWKF%2BA1c7DROatr7qBnCkbXac6TD0%3D&reserved=0)
- [https://docs.microsoft.com/en-us/azure/synapse-analytics/sql/develop-best-practices](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fsynapse-analytics%2Fsql%2Fdevelop-best-practices&data=02%7C01%7Cpaalexan%40microsoft.com%7Ce02a8d2cf38c43fcb21608d83ec7986b%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637328374306748942&sdata=KVIdXu8cN0JnaASzm7VjhFfgl0cr00tmSeIr66diP%2B8%3D&reserved=0)

**Best practice and guide on Loading Data**

- [https://docs.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/guidance-for-loading-data](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fsynapse-analytics%2Fsql-data-warehouse%2Fguidance-for-loading-data&data=02%7C01%7Cpaalexan%40microsoft.com%7Ce02a8d2cf38c43fcb21608d83ec7986b%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637328374306758938&sdata=dk%2FkDuLAiVeEocd1FujaYRhM0sCaxNo%2Fz2aGsLRJdrA%3D&reserved=0)
- [https://docs.microsoft.com/en-us/azure/synapse-analytics/sql/data-loading-best-practices](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fsynapse-analytics%2Fsql%2Fdata-loading-best-practices&data=02%7C01%7Cpaalexan%40microsoft.com%7Ce02a8d2cf38c43fcb21608d83ec7986b%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637328374306758938&sdata=8GJed5i4tcmqUYyWDjRwzZPBaD2CKnJFfCSOnFGZQR0%3D&reserved=0)

**Designing Tables**

- [https://docs.microsoft.com/en-us/azure/sql-data-warehouse/sql-data-warehouse-tables-overview](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fsql-data-warehouse%2Fsql-data-warehouse-tables-overview&data=02%7C01%7Cpaalexan%40microsoft.com%7Ce02a8d2cf38c43fcb21608d83ec7986b%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637328374306768928&sdata=g3EvipqqRgtT1Y3CMdqTP0kSZOhz0hIeofVv8%2FqbRhs%3D&reserved=0)

**Indexing Tables**

- [https://docs.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-tables-index](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fsynapse-analytics%2Fsql-data-warehouse%2Fsql-data-warehouse-tables-index&data=02%7C01%7Cpaalexan%40microsoft.com%7Ce02a8d2cf38c43fcb21608d83ec7986b%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637328374306768928&sdata=Kn8YDTR0e1HnhISGF00r4w5KqIcDSuoHCWICV4AoOMU%3D&reserved=0)

**Heaps**

- [https://docs.microsoft.com/en-us/sql/relational-databases/indexes/heaps-tables-without-clustered-indexes?view=sql-server-ver15](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fsql%2Frelational-databases%2Findexes%2Fheaps-tables-without-clustered-indexes%3Fview%3Dsql-server-ver15&data=02%7C01%7Cpaalexan%40microsoft.com%7Ce02a8d2cf38c43fcb21608d83ec7986b%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637328374306778921&sdata=Ryr2WAyB6wfnZs9SwP6DbCMLr9P1GqQ0Q9ec2au%2B%2Fa4%3D&reserved=0)

**Clustered Columnstore Index**

- [https://docs.microsoft.com/en-us/sql/relational-databases/indexes/columnstore-indexes-overview?view=sql-server-ver15](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fsql%2Frelational-databases%2Findexes%2Fcolumnstore-indexes-overview%3Fview%3Dsql-server-ver15&data=02%7C01%7Cpaalexan%40microsoft.com%7Ce02a8d2cf38c43fcb21608d83ec7986b%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637328374306778921&sdata=gbdfMpoQKKEb0lfzDoGo6bz%2BQKisEjle8Ikg%2FeV%2FVfA%3D&reserved=0)
- [https://docs.microsoft.com/en-us/sql/relational-databases/indexes/columnstore-indexes-overview?view=sql-server-ver15#can-i-combine-rowstore-and-columnstore-on-the-same-table](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fsql%2Frelational-databases%2Findexes%2Fcolumnstore-indexes-overview%3Fview%3Dsql-server-ver15%23can-i-combine-rowstore-and-columnstore-on-the-same-table&data=02%7C01%7Cpaalexan%40microsoft.com%7Ce02a8d2cf38c43fcb21608d83ec7986b%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637328374306788918&sdata=FQoRYIPbrwOrEfh0yFK1FYze74qejBeOjnIiL2GtNoQ%3D&reserved=0)

**Designing Distributed Tables — Round Robin vs Hash vs Replicated**

- [https://docs.microsoft.com/en-us/azure/sql-data-warehouse/sql-data-warehouse-tables-distribute](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fsql-data-warehouse%2Fsql-data-warehouse-tables-distribute&data=02%7C01%7Cpaalexan%40microsoft.com%7Ce02a8d2cf38c43fcb21608d83ec7986b%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637328374306798910&sdata=6PDaeqz%2F0A2UGoCJvlei0uOTAJEqFZgLIv2RNpmpE%2F8%3D&reserved=0)
- [https://docs.microsoft.com/en-us/azure/sql-data-warehouse/sql-data-warehouse-tables-overview#common-distribution-methods-for-tables](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fsql-data-warehouse%2Fsql-data-warehouse-tables-overview%23common-distribution-methods-for-tables&data=02%7C01%7Cpaalexan%40microsoft.com%7Ce02a8d2cf38c43fcb21608d83ec7986b%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637328374306798910&sdata=uLAFzqqOIku%2Fl7v9HzsRvBtNnu%2FkXYBVLt7lEPcK%2BVU%3D&reserved=0)

*Hash-Distribution — Use this distribution methodology for large fact tables with clustered columnstore index.*

*Replicated — Use this distribution strategy for smaller tables (<2GB), which can be replicated to each compute node, typically used for Dimension Tables.*

*Round-Robin — Use this strategy for staging tables or for loading data or when there is no clear choice for distribution.*

**Load data from external tables using polybase**

- [https://docs.microsoft.com/en-us/azure/sql-data-warehouse/load-data-from-azure-blob-storage-using-polybase#load-the-data-into-your-data-warehouse](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fsql-data-warehouse%2Fload-data-from-azure-blob-storage-using-polybase%23load-the-data-into-your-data-warehouse&data=02%7C01%7Cpaalexan%40microsoft.com%7Ce02a8d2cf38c43fcb21608d83ec7986b%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637328374306808905&sdata=6ZGaY2K%2FxBhP4TE6CL0%2BI0KH%2FumQ7nG%2FO2uPEM9lQlk%3D&reserved=0)

**Azure Synapse SQL Extension**

The Azure Synapse SQL Extension contain a collection of User Defined Functions (UDFs) and Views that extend the capabilities of Azure Synapse SQL. This is especially useful when you’re migrating from legacy on premise systems such as Teradata and need to emulate functionality in Synapse.

***Most often the question on how to size a proper cluster is asked. The general guidelines are:***

1. Number of concurrent Queries — [https://docs.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/memory-concurrency-limits](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fazure%2Fsynapse-analytics%2Fsql-data-warehouse%2Fmemory-concurrency-limits&data=02%7C01%7Cpaalexan%40microsoft.com%7Ce02a8d2cf38c43fcb21608d83ec7986b%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637328374306728951&sdata=WFEFWjuZzGkcKMv3em1Bo5DJlB4K6ZtjCT3rklEq%2B%2Bs%3D&reserved=0). Result set caching can reduce the number of concurrent queries.
2. Size of the Active data set being queried Daily. — 1.5 TB per compute node
3. Size of the Memory need to perform Calculations in Memory. — 300GB per compute node. This often matches or exceeds existing source systems.
4. Necessary size of Temp DB the ETL and Queries need (difficult to get from source systems). This is rare, but, I have seen companies need to increase DWU to get additional TempDB space. This typically happens with very large Datasets but have few concurrent queries.

***There is also bench marking practices that are published here:***

[https://techcommunity.microsoft.com/t5/azure-synapse-analytics/performance-benchmark-azure-synapse-analytics-data-warehouse/ba-p/1381302](https://techcommunity.microsoft.com/t5/azure-synapse-analytics/performance-benchmark-azure-synapse-analytics-data-warehouse/ba-p/1381302)

**If you are interested to check the GitHub Azure Samples for Synapse see the link**

***Attention to Resource Classes will help you !***

***Materialized Views***

Materialized views in Synapse SQL pool provide a low maintenance method for complex analytical queries to get fast performance without any query change. This article discusses the general guidance on using materialized views.

[Performance tune with materialized views — Azure Synapse Analytics | Microsoft Docs](https://docs.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/performance-tuning-materialized-views?view=azure-sqldw-latest)

[CREATE MATERIALIZED VIEW AS SELECT (Transact-SQL) — SQL Server | Microsoft Docs](https://docs.microsoft.com/en-us/sql/t-sql/statements/create-materialized-view-as-select-transact-sql?toc=%2Fazure%2Fsynapse-analytics%2Fsql-data-warehouse%2Ftoc.json&bc=%2Fazure%2Fsynapse-analytics%2Fsql-data-warehouse%2Fbreadcrumb%2Ftoc.json&view=azure-sqldw-latest)

[DBCC PDW\_SHOWMATERIALIZEDVIEWOVERHEAD (Transact-SQL) — SQL Server | Microsoft Docs](https://docs.microsoft.com/en-us/sql/t-sql/database-console-commands/dbcc-pdw-showmaterializedviewoverhead-transact-sql?toc=%2Fazure%2Fsynapse-analytics%2Fsql-data-warehouse%2Ftoc.json&bc=%2Fazure%2Fsynapse-analytics%2Fsql-data-warehouse%2Fbreadcrumb%2Ftoc.json&view=azure-sqldw-latest)