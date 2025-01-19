---
aliases: [data pipeline, data pipelines]
---
#Technology 
# Data Pipeline
It seems as if every business these days is seeking ways to integrate data from multiple sources to gain business insights for competitive advantage.

A **data pipeline** is a set of actions that ingest raw data from disparate sources and move the data to a destination for storage and analysis. A pipeline also may include filtering and features that provide resiliency against failure.

## Data pipeline process

To understand how a [data pipeline](https://www.talend.com/resources/what-is-a-data-pipeline/) works, think of any pipe that receives something from a source and carries it to a destination. What happens to the data along the way depends upon the business use case and the destination itself. A data pipeline may be a simple process of data extraction and loading, or, it may be designed to handle data in a more advanced manner, such as training datasets for machine learning.

**Source**: Data sources may include relational databases and data from SaaS applications. Most pipelines ingest raw data from multiple sources via a push mechanism, an API call, a replication engine that pulls data at regular intervals, or a webhook. Also, the data may be synchronized in real time or at scheduled intervals.

**Destination**: A destination may be a data store — such as an on-premises or cloud-based data warehouse, a data lake, or a data mart — or it may be a BI or analytics application.

**Transformation**: Transformation refers to operations that change data, which may include data standardization, sorting, deduplication, validation, and verification. The ultimate goal is to make it possible to analyze the data.

**Processing**: There are two data ingestion models: **batch processing**, in which source data is collected periodically and sent to the destination system, and **stream processing**, in which data is sourced, manipulated, and loaded as soon as it’s created

**Workflow**: Workflow involves sequencing and dependency management of processes. Workflow dependencies can be technical or business-oriented.

![data_pipeline](https://images.ctfassets.net/k49d63tr8kcn/4jbw1fdWLuMUh0Ztlb2dOn/6964e6b873b904392990355ed48c983a/data_pipeline-1-.svg)

A data pipeline is a series of processes that migrate data from a source to a destination database.

-   An example of a **technical dependency** may be that after assimilating data from sources, the data is held in a central queue before subjecting it to further validations and then finally dumping into a destination.
-   An example of a **business dependency** may be data that must be cross-verified from one source against another for maintaining accuracy before consolidation.

**Monitoring**: Data pipelines must have a monitoring component to ensure data integrity. Examples of potential failure scenarios include network congestion or an offline source or destination. The pipeline must include a mechanism that alerts administrators about such scenarios.

## In-house or in the cloud?

Many companies build their own data pipelines. [Spotify](https://labs.spotify.com/2013/05/13/analytics-at-spotify/), for example, developed a pipeline to analyze its data and understand user preferences. Its pipeline allows Spotify to see which region has the highest user base, and it enables the mapping of customer profiles with music recommendations.

But there are challenges when it comes to [developing an in-house pipeline](https://www.stitchdata.com/blog/why-you-shouldnt-build-your-own-data-pipeline/). Different data sources provide different APIs and involve different kinds of technologies. Developers must write new code for every data source, and may need to rewrite it if a vendor changes its API, or if the organization adopts a different data warehouse destination.

Speed and scalability are two other issues that data engineers must address. For time-sensitive analysis or business intelligence applications, ensuring low latency can be crucial for providing data that drives decisions. And the solution should be elastic as data volume and velocity grows. The high costs involved and the continuous efforts required for maintenance can be major deterrents to building a data pipeline in-house.

### Modern data pipelines and ETL

ETL tools that work with in-house data warehouses do as much prep work as possible, including transformation, prior to loading data into data warehouses. Today, however, cloud data warehouses like Amazon Redshift, Google BigQuery, Azure SQL Data Warehouse, and Snowflake can scale up and down in seconds or minutes, so developers can replicate raw data from disparate sources and define transformations in SQL and run them in the data warehouse after loading or at query time.

Just as there are cloud-native data warehouses, there also are ETL services built for the cloud. Businesses can set up a cloud-first platform for moving data in minutes, and data engineers can rely on the solution to monitor and handle unusual scenarios and failure points.

In a SaaS solution, the provider monitors the pipeline for these issues, provides timely alerts, and takes the steps necessary to correct failures. Business leaders and IT management can focus on improving customer service or optimizing product performance instead of maintaining the data pipeline.

## Getting started with a data pipeline

Before you try to build or deploy a data pipeline, you must understand your business objectives, designate your data sources and destinations, and have the right tools. But setting up a reliable data pipeline doesn’t have to be complex and time-consuming. Stitch makes the process easy. [Sign up for Stitch for free](https://www.stitchdata.com/signup) and get the most from your data pipeline, faster than ever before.