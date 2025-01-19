---
title: Intro to Microsoft Fabric | endjin
source: https://endjin.com/blog/2023/05/intro-to-microsoft-fabric
author:
  - "[[Ed Freeman"
  - //header/h1
  - //article[@id='content']/p]]
published: 2023-05-23T23:01:00.0000000&#x2B;00:00, //header/h1, //article[@id='content']/p
created: 2024-10-02
description: Microsoft Fabric unifies data & analytics, building on Azure Synapse Analytics for improved data-level interoperability. Explore its offerings & pros/cons.
tags:
  - EA_Data
  - Analytics
  - Azure
  - Microsoft_Fabric
  - Data_Platform
  - Data_Pipeline
  - Synapse
  - Data_Lake
  - Lakehouse
  - definition
---
On May 23rd 2023 (at the Microsoft Build conference), [Microsoft Fabric](https://azure.microsoft.com/en-us/blog/introducing-microsoft-fabric-data-analytics-for-the-era-of-ai/) was announced in Public Preview, a brand new unified data & analytics platform that brings together, and improves upon, Microsoft's existing suite of data products. We've been fortunate enough to have been a part of the private preview for the last 6 months, and we're here to share our views.

## So what is Microsoft Fabric?

Microsoft Fabric can be thought of as the third generation of Microsoft data platforms, where first generation (e.g. HDInsight, SQL Data Warehouse) were somewhat isolated takes on traditional data products; second generation was Azure Synapse Analytics, which integrated platforms at a UX level but still felt a little disjointed at the data level; and now we have Microsoft Fabric which builds upon the Synapse "unification" vision, with a particular focus on enabling deep data-level interoperability.

To do that, there's been a huge investment in standardizing the foundations of the platform to enable compute models to integrate and interoperate seamlessly. Then, these compute models have been surfaced in an experience-oriented UX that maps to common data personas, like Data Engineers, Data Scientists, Citizen Analysts, and so on. The UI is very Power BI-like, which should hopefully be familiar with a lot of you reading this blog.

The other big shift is that Microsoft Fabric is SaaS rather than PaaS. That brings with it a more opinionated view of how a modern data platform should take shape, and enables a shift even further towards data democratization (i.e. "more self service") for all personas. It also introduces a standardized capacity-based commercial model, where users don't need to manage billing for different computes separately. (For those of you squirming at this last sentence, don't despair - the entry point is nowhere near the entry point for Power BI Premium capacities.)

## How does Microsoft Fabric compare to Azure Synapse Analytics?

If you're familiar with [Azure Synapse Analytics](https://azure.microsoft.com/en-gb/products/synapse-analytics), you can see Fabric as the next generation of Synapse ("Synapse Gen3", if you will) with a bit of extra flourish. Synapse experiences have been largely lifted and shifted, so the UX within the constituent elements of Fabric (e.g. notebooks/pipelines) should feel relatively familiar. Compared to Azure Synapse Analytics, Microsoft Fabric keeps some functionality, improves some, adds some and removes some. Check out Barry's blog [Synapse versus Fabric: A Side by Side Comparison](http://endjin.com/blog/2023/05/azure-synapse-analytics-versus-microsoft-fabric-a-side-by-side-comparison) for a detailed comparison. And of course, we can't forget that Power BI has essentially become part of Microsoft Fabric, whereas in Synapse it was only really an integration point.

Microsoft acknowledges that a large number of Azure Synapse Analytics customers will have a large existing data estate in Synapse and will need a way of migrating. We understand that there's been quite a bit of thought put into how to make this migration exercise as easy as possible, such that every element of Synapse has some sort of recommended migration strategy - some direct technical solutions, some process-based. And I think it's fair to assume Azure Synapse won't be going anywhere anytime soon, so if migrating to Fabric isn't on your short-term radar, you have nothing to worry about. Although I think it's also fair to assume that Microsoft Fabric will be getting the lion's share of attention and investment within Microsoft, so I wouldn't expect much more innovation on the Synapse side, unless it benefits Fabric as well.

## How does Microsoft Fabric compare to Databricks/Snowflake?

We're not yet quite comparing apples with apples. Databricks and Snowflake are slightly narrower and deeper in focus. Databricks is still widely seen by customers as the cross-Cloud platform for data science and machine learning workloads, though its marketing strategy would suggest it's now the "home of the Lakehouse", and has even more recently branched into a fully-fledged data warehouse offering. Snowflake is maybe best known as an innovative SaaS cloud data warehouse, which more recently has started releasing features (like Snowpark) which would appeal to data engineer type personas.

Fabric from the outset has a much broader vision innovating all the way up and down the stack from the low-level data and compute nuts and bolts through to these "knowledge-worker" experiences that you've probably seen in the Microsoft demos. I wouldn't expect any of them to stand still, though; there is a general convergence to this "unified analytics platform" happening for the whole industry. Stay tuned for more blogs in this space!

## More specifically - what does Microsoft Fabric allow me to do?

Microsoft Fabric contains a feature set spanning descriptive, diagnostic, predictive and prescriptive analytics, from batch through streaming workloads. More specifically, it is broken down into several top-level "experiences" aligned to a range of personas:

- **[Data Factory](https://learn.microsoft.com/en-gb/fabric/data-factory/data-factory-overview) (data integration)​**
- Based off [Azure Data Factory](https://azure.microsoft.com/en-gb/products/data-factory) (and Azure Synapse Analytics Pipelines). Note: feature set currently not as mature as Azure Data Factory
- **[Synapse Data Engineering](https://learn.microsoft.com/en-gb/fabric/data-engineering/data-engineering-overview)**
- Primarily comprising "Lakehouses", Notebooks, Spark Job Definitions
- **[Synapse Data Warehouse](https://learn.microsoft.com/en-gb/fabric/data-warehouse/data-warehousing)​**
- An evolution of [Synapse SQL Dedicated Pools](https://learn.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-overview-what-is)
- **[Synapse Data Science](https://learn.microsoft.com/en-gb/fabric/data-science/data-science-overview)​**
- Full-suite of Data Science capabilities including creation and deployment of models, all within Fabric. Think of it as [Synapse ML capabilities](https://learn.microsoft.com/en-us/azure/synapse-analytics/machine-learning/what-is-machine-learning) and [Azure Machine Learning](https://learn.microsoft.com/en-us/azure/machine-learning/overview-what-is-azure-machine-learning?view=azureml-api-2) rolled into one.
- **[Synapse Real-Time Analytics](https://learn.microsoft.com/en-gb/fabric/real-time-analytics/overview)​**
- Evolution of [Synapse Data Explorer](https://learn.microsoft.com/en-us/azure/synapse-analytics/data-explorer/data-explorer-overview)
- Also introduces "Eventstreams" - feature very similar to [Azure Stream Analytics no-code editor](https://techcommunity.microsoft.com/t5/analytics-on-azure-blog/build-real-time-dashboard-with-power-bi-dataset-produced-by/ba-p/3747528)
- **[Power BI](https://learn.microsoft.com/en-us/power-bi/fundamentals/power-bi-overview) (Business Intelligence)​**
- The same [Power BI](https://learn.microsoft.com/en-us/power-bi/fundamentals/power-bi-service-overview) we all know and love, with some new close integrations with other Fabric artifacts
- **Data Activator**
- Brand new event-driven stream processing tool integrating closely with Power BI and Event Hubs. Branded as a "digital nervous system".

Note the continued use of "Synapse" terminology.

It's worth giving a shout-out to ["OneLake"](https://learn.microsoft.com/en-gb/fabric/onelake/onelake-overview), which is a single logical data lake provisioned with every Fabric tenant which stores/surfaces all of your Fabric related data. This isn't shown on the experience-switcher within the Fabric UI, but it's there - trust me. Take a read of the ["What is OneLake"](https://endjin.com/blog/2023/05/what-is-onelake) blog for more information.

## What's good (and bad) about Microsoft Fabric?

Let's remember that Fabric is still in Public Preview, so not all features have been released, things are still buggy, and work is still being done to finalize elements of the UX/UI. But here are some of the main points:

### 🎉 Everything (and I mean everything's) under one roof

- Products spanning Data Integration, Data Engineering, Data Warehousing, Real-time processing all integrated. "But Synapse has this!" I hear you. I really do. But just because a new product is following that principle doesn't make this a bad thing.
- Being SaaS, from a data perspective all data is stored in OneLake. As the name suggests, there's only one of these. So it's not like you have to manage and provision multiple storage accounts for all your separate workloads. It's your "OneDrive for data".
- Like Power BI, where all artifacts can be found in the Power BI Service, Fabric is also presented in a Power BI-like UI. Many data personas of all types already spend a good amount of time in this UI, which will accelerate the transition to self-service analytics "higher up the stack" for personas like Data Analysts and Data Citizens. And Data Scientists/Engineers already familiar with Power BI/Azure Synapse/Azure Databricks will find the experience close enough to current reality for them to get up and running very quickly.

The underlying theme here is "democratization" - Fabric is equipping personas of all types with the tools and data they need to be successful. Theoretically, at least.

### 🎉 Tight integration between experiences - enabled by embracing OSS tech

In the aforementioned section we saw all the different experiences that Fabric surfaces. Fundamentally, all these experiences work with/operate on data, stored in [OneLake](https://endjin.com/blog/2023/05/what-is-onelake). Coupled with the fact that all data tables are stored in the [Delta Lake open table format](https://docs.delta.io/latest/delta-intro.html), this leads to Fabric being able to capitalize on the standardization and create tight integration between different compute engines within Fabric. This standardization on a single format has also meant that optimizations have been made that multiple engines can benefit from.

### 🎉(Certain) Things are better/quicker

The Fabric team has not only focused on the high-level feature set and new UX, but they've also put a lot of effort into making existing services better. For example, spinning up a Spark Session in Fabric (be it through a notebook/Spark Job Definition) now takes ~30 seconds, rather than ~3 minutes, which is a huge improvement. Separately, "Direct Lake" is an incredible new piece of functionality which makes querying over Delta tables within your Data Lake from a Power BI report feel like you're using a dataset in Import mode, but without having to duplicate & manually refresh the data. This is largely down to a new ["VORDER" optimization](https://learn.microsoft.com/en-us/fabric/data-engineering/delta-optimization-and-v-order?tabs=sparksql) that's automatically applied to Delta tables written by Fabric, which introduces a new compression for Delta data files, while still conforming to the Delta Lake specification.

Other features we're excited by are the improvements to the Power BI developer workflow, where the fabled "desktop hardening" is starting to come to fruition. And, to be fair, this isn't the only "DevOps" feature that is welcome news - there's end-to-end git integration littered throughout the whole of Fabric, with Deployment Pipelines for all artifacts on the near roadmap and workspace [Git Integration](https://learn.microsoft.com/en-gb/fabric/cicd/git-integration/intro-to-git-integration) already available. On the Spark-dev front, we've been given a VS Code extension which allows us to connect to our Fabric Spark runtime remotely to enable easier local development. We'll be posting more content about this feature in particular in the weeks to come.

### 😩 Some Synapse features haven't made the cut

When building a new product, naturally there are going to be tradeoffs with respect to the functionality the product will offer. However, we are particularly sad that a few products/features (or equivalents) haven't made it into Fabric:

1. **Synapse SQL Serverless** (pay-per-query). For those that follow our blog, it'll come as no surprise that this was one of the first features we noticed that was missing. SQL Serverless allowed querying over raw csv/parquet/json files or existing Delta tables in the lake. Not only was it a great (low-cost) replacement for a SQL engine as a foundational part of data platforms, it enabled really easy ad-hoc analysis and quick previewing of data that resided in your data lake. Fabric currently has no replacement for this functionality. Ad-hoc analysis over files in OneLake isn't possible using T-SQL. Previewing of data in OneLake is only possible for certain file types (parquet is somehow not one of them). To do ad-hoc analysis of files in Fabric you'll either need to use Spark notebooks, or load the corresponding data into managed Delta tables before that becomes possible.
2. **Mapping Data Flows**. This ETL GUI embedded within Azure Data Factory/Azure Synapse is extremely popular amongst our customers. It is easy to use and easy to upskill, allowing people to take advantage of Spark without having to understand its ins and outs. Time had been spent designing core elements of data pipelines using Mapping Data Flows and generating IP (sometimes in the form of [Flowlets](https://learn.microsoft.com/en-us/azure/data-factory/concepts-data-flow-flowlet)). People had learned the expression syntax to allow them to do more complex expressions. Fabric hasn't inherited the MDF feature, instead prioritizing Dataflows Gen2. It's our understanding that there will be a migration path for organizations using Mapping Data Flows, but how seamless an experience that will be remains to be seen. What isn't a secret, though, is that Dataflows Gen2 are the future of low-code ELT pipelines in Fabric, so it's worth investing in that.
3. **Spark .NET**. Sorry C# developers - .NET for Apache Spark hasn't made the cut for the Fabric Spark runtime, even though you could create C# notebooks and create [Custom C# Spark Jobs in Azure Synapse](https://endjin.com/what-we-think/talks/custom-csharp-spark-jobs-in-azure-synapse). .NET is great for high performance computation and Spark is a perfect alternative to Azure Batch, so we're sad that this isn't a part of the Fabric release.

### 😩 The UX can be quite frictional

The UX/UI is likely to evolve over the Public Preview period, so we won't spend much time going over it. But since Fabric has now introduced a number of "new" artifacts, including organizational abstractions such as experiences, workspaces and domains, we've found ourselves getting a little lost in the UI on numerous occasions. We now have vertical tabs instead of the horizontal tabs we had in Synapse, which I'm finding harder to quickly navigate. To be honest, I wasn't a fan of [Power BI's UI revamp back in 2020](https://powerbiweekly.info/issue-55.html), and this builds on those UI building blocks. So it's maybe no real surprise I'm finding it difficult to navigate!

### 😩 Capacity-based commercial model

At endjin, we are huge proponents for the pay-per-query (consumption) style commercial model. Whether that was Azure Data Lake Analytics (now deprecated), or Synapse SQL Serverless - the technology didn't matter. This commercial model opens doors in a couple of ways:

- Organizations/teams wanting to dip their toes and experiment with new technology had an easy way to rigourously test without having to commit to any specific spend level. This was, in our opinion, the USP of Synapse SQL Serverless - pay for what you use/query.
- Once live, data pipeline costs could be attributed at a granular level to specific teams that owned that specific workload. Being able to put an accurate cost on individual pipelines was invaluable for charge-back scenarios, but also just to understand the relative pricing of running different workloads.

Not only that, but we have implemented numerous data platforms using these types of technologies at the core, and they have been both economical and performant.

Fabric loses the notion of consumption-based pricing, and in doing so, we think it will lose out on a number of prospective customers. It has unified all computes into a single, capacity based commercial model which uses Capacity Units (CUs) as its core unit. It's unclear yet as to the weighting that each compute engine will have towards the consumption of the CUs, and its unclear exactly how much friction it will be to pause/resume capacities as and when needed, and how auto-scale will work (and how much it will cost). Fabric capacities will start at a much lower price point than Power BI Premium capacities, but will it still be too much for newcomers to stomach? And will the lower-scale capacities be "production ready"?

## Microsoft Fabric - final thoughts for Public Preview

The future is certainly bright for all things data at Microsoft. The vision is sound, and the feature set is very exciting. Though there's certainly a long way to go.

[![The best hour you can spend to refine your own data strategy and leverage the latest capabilities on Azure to accelerate your road map.](https://endjin.com/assets/sign-up-for-azure-data-strategy-briefing-DXDjusPd.svg)](https://endjin.com/what-we-do/azure-data-strategy-briefing.html)

[Organizations should use this public preview period](https://learn.microsoft.com/en-gb/fabric/admin/fabric-switch) to run some PoV/PoC exercises on some example workloads of theirs. We certainly wouldn't recommend starting a full, formal migration process to Fabric yet - at this point we think that it would be too much of a time sink while the platform lacks stability. Start thinking about building internal expertise that precipitates ["Champion(s) of Enablement"](https://youtu.be/Vv8TRvGCOZc?t=1278), so that when Fabric does become GA, there is an understanding about how Fabric can be utilized across the wider business in an efficient and positive manner.

[![Azure Weekly is a summary of the week's top Microsoft Azure news from AI to Availability Zones. Keep on top of all the latest Azure developments!](https://endjin.com/assets/subscribe-to-azure-weekly-CqRFKcX3.svg)](https://azureweekly.info/)

Stay tuned for much more Fabric content from endjin over the next few weeks!