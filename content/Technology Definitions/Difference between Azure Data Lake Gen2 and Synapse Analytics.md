# Difference between Azure Data Lake Gen2 and Synapse Analytics

> Azure Data Lake Storage Gen2 (ADLS Gen2) and Azure Synapse Analytics (formerly, SQL Data Warehouse) both are highly scalable and have the capability to ingest and process huge amounts of data (on a…

Azure Data Lake Storage Gen2 (ADLS Gen2) and Azure Synapse Analytics (formerly, _SQL Data Warehouse_) both are highly scalable and have the capability to ingest and process huge amounts of data (on a Peta Byte scale). But there are some differences :

| **ADLS Gen2** | **Azure Synapse Analytics** |
| --- | --- |
|  Optimized for storing and processing structed and non-structured data | Optimized for processing structured data in a well-defined schema |
| Used for data analytics and exploration by data scientists and engineers | Used for Business Analytics i.e. for disseminating data to business users |
| Built to work with Hadoop | Built on SQL Server |
| No regulatory compliance | Compliant with regulatory standards such as HIPAA |
| USQL (combination of TSQL and C#) and Hadoop used for accessing data | Synapse SQL (improved version of TSQL) used for accessing data |
| Can handle data streaming using tools such as Azure Stream Analytics | Built-in data pipelines and data streaming capabilities (currently in preview) |

Post navigation
---------------


[Source](https://azurede.com/2020/04/29/difference-between-azure-data-lake-gen2-and-synapse-analytics/)