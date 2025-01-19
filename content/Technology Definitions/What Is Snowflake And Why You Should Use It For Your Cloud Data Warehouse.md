---
title: What Is Snowflake And Why You Should Use It For Your Cloud Data Warehouse
source: https://medium.com/coriers/what-is-snowflake-and-why-you-should-use-it-for-your-cloud-data-warehouse-199c62b0a09e
author:
  - "[[Ben Rogojan]]"
published: 2021-07-27
created: 2024-09-20
description: Snowflake is a cloud data platform. To be more specific it’s the first cloud built data platform. Its architecture allows data specialists to not only create data warehouses but also cloud data…
tags:
  - EA_Data
  - Analytics
  - Data_Lake
  - Lakehouse
  - definition
  - Snowflake
---
## From Tasks To Snowpipes



![](https://miro.medium.com/v2/resize:fit:1400/1*9slI_2HPFKtr1uehNuSFoA.png)

[Source](https://aws.amazon.com/financial-services/partner-solutions/snowflake-data-warehouse/)

[Snowflake](https://www.snowflake.com/) is a cloud data platform. To be more specific it’s the first cloud built data platform. Its architecture allows data specialists to not only create data warehouses but also cloud data lake-houses because it can manage both structured and unstructured data easily.

Being that Snowflake is based in the cloud, this means that it allows developers to take advantage of elasticity and scalability without worrying about things like high up front costs, performance, or complexity of managing the system.

## So Why Use Snowflake?

There are a lot of options when it comes to [cloud data warehouses](https://www.theseattledataguy.com/what-are-the-benefits-of-cloud-data-warehousing-and-why-you-should-migrate/#page-content) and everyone has specific use cases. However, our team is finding more and more users are either selecting or switching over to Snowflake for its many useful features and overall ease of use.

Here are just some of the reasons why we are finding people enjoy using SnowflakeDB.

## Cloud Agnostic

Snowflake is not limited to one specific cloud provider. Instead, companies can seamlessly scale their [data warehouse](https://seattledataguy.substack.com/p/what-is-cloud-data-warehousing) across Amazon Web Services (AWS), Microsoft Azure, and GCP.

Meaning companies don’t need to spend time setting up hybrid cloud systems.

## Performance and Speed

Snowflake is built for performance. Starting with the underlying infrastructure that is built to run analytical queries. To add to that the elastic nature of the cloud means if you want to load data faster, or run a high volume of queries, you can scale up your virtual warehouse to take advantage of extra compute resources.

## User-friendly UI/UX

Snowflake’s UI/UX is easy to use and also very feature-rich. It’s easy to find old queries you have run, or even other user queries that are running(depending on your access level).

There are also a whole host of other features that are button clicks away rather than hidden behind settings and configuration drops downs that you may not even know exist. This makes Snowflake very user friendly and I often find that many analysts are finding working with Snowflake very easy.

## Reduced Administration Overhead

Cloud services often require less administration overhead because companies don’t need to manage hardware and often can take advantage of scaling. In addition, Snowflake is a SaaS and this means set-up, updates, and general management is mostly managed by Snowflake and not your company.

Much of this management and scaling can be done by anyone with the proper rights without much knowledge in terms of servers, command lines, or coding.

This isn’t to say that you should just quickly click around and switch server sizes. You may find yourself suddenly paying a much higher bill.

## On-Demand Pricing

Snowflake offers on-demand pricing, meaning that you will only pay based on the amount of data you store and the compute hours/minutes you use. Unlike a traditional data warehouse, Snowflake also gives you the flexibility to easily set up the idle time so you don’t need to pay if the warehouse is inactive.

## Support Variety of File Formats

Data doesn’t just come in CSV, XML, pipe-delimited, and TSV anymore. In turn, Snowflake supports the structured data as well as a wide variety of semi-structured data including Parquet, Avro, and JSON.

## Snowflake Features

Another great reason to migrate to Snowflake is because of the many technical features it offers end-users.

## Snowflake Tasks

Snowflakes tasks are single SQL statements used independently for analytics reports. This process occurs by combining or inserting rows into a report table. These tasks run at a specific time and skip any other tasks running during each new execution.

The tasks run via cron expressions and allow the user to specify their time zone and have configurations for daylight saving time. Tasks begin with a root task that can link with other tasks like a tree.

The tasks derive from a single node to a particular end node destination rather than a DAG structure. A total of 1000 tasks per tree is the maximum, which also includes the root task. Keep in mind that all the tasks need to have a single role or owner.

## Snowflake Snowpipes

With a Snowpipe, you can load data in micro-batches when they’re ready in a stage. This provides a faster solution than the traditional method of executing a COPY statement manually.

Users define the referenced pipe, which is a Snowflake object with a COPY statement. The great thing about a Snowpipe is that it can accommodate all structured data types.

Some other significant features include automation using cloud messaging and calling REST endpoints. When new data loads arrive, they trigger an event notification for cloud storage.

Once this occurs, Snowpipe can then copy a file and load it into a queue in the target table. The client application then calls the public REST endpoint. The list of filenames and pipe objects prompts this action, and new data loads from the queue based on the definition for parameters within the pipe.

## Snowflake Streams

A Snowflake stream (or simply ‘stream’) records data manipulation language. It records changes from deletes, inserts, updates, and metadata related to any change. This allows actions to take place by using this recorded change data.

The stream doesn’t have table data, but stores offset for the source table. This happens if the versioning history is used for the source table. Stream can ‘mark’ a point when changes occur, such as those within the source table. Streams can be created and dropped as needed, thus providing a substantial amount of flexibility.

A new table version occurs when DML statements are committed to the table. This process allows for minimal changes from current offsets to the current version of the table.

The timestamp is queried for the stream advance point when SQL statements query an explicit transaction. It is true for both CREATE TABLE and DML when existing stream statements populate a new table row.

## Snowflake Solution With Streams and Tasks

The time travel feature of Snowflake powers its table stream, which contains the latest row changes. It functions much like a query, and once the data is used, it moves forward and changes metadata for each row.

As mentioned regarding tasks, they execute via the SQL statement and provide designated actions by a tree structure. If they’re used together, these functions create an ELT pipeline.

This solution is ready to go and pre-built with Table Stream and Task. Used together, you can capture changes, including the following.

- Inserts
- Updates
- Deletes
- Metadata

It’s a cost-effective option that helps you eliminate the need for many third-party tools. You get a high level of usability and modern features that make using Snowflake a better option for many business needs.

## Is Snowflake for You?

If you’re wondering why you should use Snowflake, consider the range of possibilities and affordable solutions you can implement to replace an outdated system. You get all the security and top features of a cloud environment with plenty of flexibility and control options to help customize your solutions.

Snowflake might be right for your needs if you’ve considered implementing cloud-based data solutions. Even if you currently need a single-tenant solution because of corporate policies, Snowflake also offers that option.

Snowflake also offers an on-premises data solution that replaces the need for physical data storage by implementing the cloud. You also get the ability to use scalable features that can operate semi-structured data, much like structured data. However, the data size load for semi-structured data is 16MB.

Snowflake can load and query data such as XML and JSON and allows for separate computing and storage. However, you can’t load pdf files, audio, and images into Snowflake unless you convert them to character strings or binary files, limited to 8 MG and 16 MB if you use character strings. Optimal files sizes are 1 GB, and for best results, Snowflake support recommends breaking down larger files.