Data pipelines move data from one source to another so it can be stored, used for analytics, or combined with other data. That’s the simple definition; more specifically, a data pipeline is an end-to-end process to ingest, process, prepare, transform and enrich structured, unstructured, and semi-structured data in a governed manner.

![c09-tunnel](https://www.informatica.com/content/informatica-www/en_us/resources/articles/data-pipeline/_jcr_content/contentPar/columncontainer_29dd/rightCol/image_d621.img.png/1616004598406.png "c09-tunnel")

As enterprises build, consolidate, or [modernize analytics in the cloud](https://www.informatica.com/solutions/move-to-the-cloud/accelerate-business-insights.html), they need an intelligent, automated cloud-native data pipeline to process raw data coming in from applications, legacy systems, social media, devices, IoT sensors, and more. This allows teams to extract useful insights from the data and make it available for driving business intelligence, predictive and prescriptive analytics, and AI and machine learning use cases. A user can define data-driven workflows so that tasks can depend on the successful completion of previous jobs. Intelligent data pipelines also enable users to identify [data lineage](https://blogs.informatica.com/2019/10/11/the-importance-of-provenance-and-lineage-in-data-informatica/), and they automate extracting, transforming, and loading the data for further analysis and visualization.

## Why Is Building a Data Pipeline Important?

Building a resilient cloud-native data pipeline helps organizations rapidly move their data and analytics infrastructure to the cloud and accelerate digital transformation.

Deploying the data pipeline will help companies build and manage workloads in the cloud efficiently. Organizations can improve [data quality](https://www.informatica.com/resources/articles/what-is-data-quality.html), connect to diverse data sources, ingest structured and unstructured data into a cloud data lake, and manage complex multi-cloud environments. Data scientists and data engineers need reliable data pipelines to access high-quality, trusted data for their cloud analytics and AI/ML initiatives so they can drive innovation and provide a competitive edge for their organizations. 

## Types of Data Pipelines

Data pipelines are categorized based on customer use cases. Two of the most common types of pipelines are batch processing and real-time processing.

### Batch processing pipelines

A batch process is primarily used for traditional analytics use cases where data is periodically collected, transformed, and moved to a cloud data warehouse for conventional BI use cases. Users can quickly mobilize high-volume data from siloed sources into a cloud data lake or data warehouse and schedule the jobs for processing it with minimal human intervention. With batch processing, users collect and store data during an event known as a batch window, which helps manage a large amount of data and repetitive tasks efficiently.

### Real-time processing pipelines

Real-time data pipelines enable users to ingest structured and unstructured data from a wide range of streaming sources such as IoT, connected devices, social media feeds, sensor data, and mobile applications using a high-throughput messaging system making sure that data is captured accurately. [Data transformation](https://www.informatica.com/resources/articles/the-basics-of-data-transformation.html) happens in real time using a real-time processing engine such as Spark streaming to drive real-time analytics use cases such as fraud detection, predictive maintenance, targeted marketing campaigns, and proactive customer care.

## 6 Steps to Building an Efficient Data Pipeline

Building an efficient data pipeline is a simple six-step process that includes:

1.  **Cataloging and governing** **the data,** enabling access to trusted and compliant data at scale across the enterprise.
    
2.  **Efficiently ingesting the data** from various sources such as on-premises databases or data warehouses, SaaS applications, IoT sources, and streaming applications into a cloud data lake.
    
3.  **Integrating the data** by cleansing, enriching, and transforming it by creating zones such as a landing zone, enrichment zone, and an enterprise zone.
    
4.  **Applying data quality rules** to cleanse and manage data while making it available across the organization to support DataOps.
    
5.  **Preparing the data** to ensure that refined and cleansed data moves to a [cloud data warehouse](https://www.informatica.com/resources/articles/cloud-data-warehouse-what-it-is-and-why-your-business-needs-it.html) for enabling self-service analytics and data science use cases.
    
6.  **Stream processing** to derive insights from real-time data coming from streaming sources such as Kafka and then moving it to a cloud data warehouse for analytics consumption.
    

## Data Pipeline Best Practices

When implementing a data pipeline, organizations should consider several best practices early in the design phase to ensure that data processing and transformation are robust, efficient, and easy to maintain. The data pipeline should be up-to-date with the latest data and should handle data volume and data quality to address DataOps and [MLOps practices](https://blogs.informatica.com/2020/05/21/mlops-operationalize-your-machine-learning-models/) for delivering faster results. To support next-gen analytics and AI/ML use cases, your data pipeline should be able to:

1.  Seamlessly deploy and process any data on any cloud ecosystem such as Amazon Web Services (AWS), Microsoft Azure, Google Cloud, and Snowflake for both batch and real-time processing
    
2.  Efficiently ingest data from any source, such as legacy on-premises systems, databases, CDC sources, applications, and IoT sources into any target, such as cloud data warehouses and data lakes
    
3.  Detect schema drift in RDBMS schema in the source database or a modification to a table, such as adding a column or modifying a column size and automatically replicating the target changes in real time for data synchronization and real-time analytics use cases
    
4.  Provide a simple wizard-based interface with no hand-coding for a unified experience
    
5.  Incorporate automation and intelligence capabilities such as auto-tuning, auto-provisioning, and auto-scaling to design time and runtime 
    
6.  Deploy in a fully managed advanced serverless environment for improving productivity and operational efficiency
    
7.  Apply data quality rules to perform cleansing and standardization operations to solve common data quality problems
    

## Customer Success Stories: Modernizing Data Processing

### SparkCognition

[SparkCognition](https://www.informatica.com/about-us/customers/customer-success-stories/sparkcognition.html) partnered with Informatica to offer the AI-powered data science automation platform Darwin, which uses pre-built [Informatica Cloud Connectors](https://www.informatica.com/products/cloud-integration/connectivity/connectors.html) to allow customers to connect it to most common data sources with just a few clicks. Customers can seamlessly discover data, pull their data from virtually anywhere using Informatica's cloud-native data ingestion capabilities, then input the data into the Darwin platform. Through cloud-native integration, users streamline workflows and speed up the model-building process to quickly deliver business value. [Read the full story.](https://www.informatica.com/about-us/customers/customer-success-stories/sparkcognition.html)

### Intermountain Healthcare

Informatica helped [Intermountain Healthcare](https://www.informatica.com/about-us/customers/customer-success-stories/intermountain-healthcare.html) easily locate, better understand, and provision all patient-related data across a complex data landscape spanning on-premises and cloud sources. Informatica data integration and data engineering solutions helped segregate datasets and establish access controls and permissions for different users, strengthening data security and compliance. Intermountain began converting approximately 5,000 batch jobs to use [Informatica PowerCenter](https://www.informatica.com/products/data-integration/powercenter.html), [Informatica Cloud Data Integration](https://www.informatica.com/products/cloud-integration/cloud-data-integration.html), or both. Data is fed into a homegrown, Oracle-based enterprise data warehouse that draws from approximately 600 different data sources, including Cerner EMR, Oracle PeopleSoft, and Strata cost accounting software, as well as laboratory systems. Affiliate providers and other partners often send data in CSV files via secure FTP, which [Informatica Intelligent Cloud Services](https://www.informatica.com/products/cloud-integration.html) loads into a staging table before handing off to PowerCenter for the heavy logic. [Read the full story.](https://www.informatica.com/about-us/customers/customer-success-stories/intermountain-healthcare.html)

## Data Pipelines Support Digital Transformation

As organizations rapidly move to the on their digital transformation journey, they need to build intelligent and automated data management pipelines. This is essential to get the maximum benefit of modernizing analytics in the cloud and unleash the full potential of cloud data warehouses and data lakes across a multi-cloud environment.

## Learn More About Data Pipelines for Cloud Analytics

Check out these additional resources for information on data processing, data pipelines, and cloud modernization.

Blog: [Data Processing Pipeline Patterns](https://blogs.informatica.com/2019/08/20/data-processing-pipeline-patterns/)

White Paper: [The High Cost of Hand Coding](https://www.informatica.com/content/dam/informatica-com/en/collateral/white-paper/the-high-cost-of-handcoding_white-paper_3852.pdf)

[Accelerate Data Engineering Pipelines for AI & Analytics](https://www.informatica.com/content/dam/informatica-com/en/collateral/solution-brief/accelerate-data-engineering-pipelines-for-ai-and-analytics_solution-brief_3708en.pdf)

Blog: [How AI-Powered Enterprise Data Preparation Empowers DataOps Teams](https://blogs.informatica.com/2020/01/30/how-ai-powered-enterprise-data-preparation-empowers-dataops-teams/)

Cloud Analytics Hub: [Get More Out of Your Cloud](https://www.informatica.com/solutions/move-to-the-cloud/cloud-analytics.html)