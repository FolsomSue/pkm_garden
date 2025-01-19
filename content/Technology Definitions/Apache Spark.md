---
aliases: [Apache Spark, spark]
---
# Apache Spark
#Technology 
Apache Spark is a lightning-fast, open source data-processing engine for machine learning and AI applications, backed by the largest open source community in big data.

## What is Apache Spark?

Apache Spark (Spark) is an open source data-processing engine for large data sets. It is designed to deliver the computational speed, scalability, and programmability required for Big Data—specifically for streaming data, graph data, machine learning, and [artificial intelligence (AI)](https://www.ibm.com/cloud/learn/what-is-artificial-intelligence "artificial-intelligence") applications.

Spark's analytics engine processes data 10 to 100 times faster than alternatives. It scales by distributing processing work across large clusters of computers, with built-in parallelism and fault tolerance. It even includes APIs for programming languages that are popular among data analysts and data scientists, including Scala, [Java](https://www.ibm.com/cloud/learn/java-explained "java-explained"), Python, and R.

Spark is often compared to Apache Hadoop, and specifically to MapReduce, Hadoop’s native data-processing component. The chief difference between Spark and MapReduce is that Spark processes and keeps the data in memory for subsequent steps—without writing to or reading from disk—which results in dramatically faster processing speeds. (You’ll find more on how Spark compares to and complements Hadoop elsewhere in this article.)

Spark was developed in 2009 at UC Berkeley. Today, it’s maintained by the Apache Software Foundation and boasts the largest open source community in big data, with over 1,000 contributors. It’s also included as a core component of several commercial big data offerings.

## How Apache Spark works

Apache Spark has a hierarchical master/slave architecture. The _Spark Driver_ is the master node that controls the cluster manager, which manages the worker (slave) nodes and delivers data results to the application client.

Based on the application code, Spark Driver generates the _SparkContext_, which works with the cluster manager—Spark’s Standalone Cluster Manager or other cluster managers like Hadoop YARN, [Kubernetes](https://www.ibm.com/cloud/learn/kubernetes "kubernetes"), or Mesos— to distribute and monitor execution across the nodes. It also creates Resilient Distributed Datasets (RDDs), which are the key to Spark’s remarkable processing speed.

### Resilient Distributed Dataset (RDD)

Resilient Distributed Datasets (RDDs) are fault-tolerant collections of elements that can be distributed among multiple nodes in a cluster and worked on in parallel. RDDs are a fundamental structure in Apache Spark.

Spark loads data by referencing a data source or by parallelizing an existing collection with the SparkContext parallelize method into an RDD for processing. Once data is loaded into an RDD, Spark performs transformations and actions on RDDs in memory—the key to Spark’s speed. Spark also stores the data in memory unless the system runs out of memory or the user decides to write the data to disk for persistence.

Each dataset in an RDD is divided into logical partitions, which may be computed on different nodes of the cluster. And, users can perform two types of RDD operations**:** transformations and actions**.** Transformations are operations applied to create a new RDD**.** Actions are used to instruct Apache Spark to apply computation and pass the result back to the driver.

Spark supports a variety of actions and transformations on RDDs. This distribution is done by Spark, so users don’t have to worry about computing the right distribution.

### Directed Acyclic Graph (DAG)

As opposed to the two-stage execution process in MapReduce, Spark creates a Directed Acyclic Graph (DAG) to schedule tasks and the orchestration of worker nodes across the cluster. As Spark acts and transforms data in the task execution processes, the DAG scheduler facilitates efficiency by orchestrating the worker nodes across the cluster. This task-tracking makes fault tolerance possible, as it reapplies the recorded operations to the data from a previous state.

### DataFrames and Datasets

In addition to RDDs, Spark handles two other data types: DataFrames and Datasets.

DataFrames are the most common structured application programming interfaces (APIs) and represent a table of data with rows and columns. Although RDD has been a critical feature to Spark, it is now in maintenance mode. Because of the popularity of Spark’s Machine Learning Library (MLlib), DataFrames have taken on the lead role as the primary API for MLlib. This is important to note when using the MLlib API, as DataFrames provide uniformity across the different languages, such as Scala, Java, Python, and R.

Datasets are an extension of DataFrames that provide a type-safe, object-oriented programming interface. Datasets are, by default, a collection of strongly typed JVM objects, unlike DataFrames.

Spark SQL allows data to be queried from DataFrames and SQL data stores, such as Apache Hive. Spark SQL queries return a DataFrame or Dataset when they are run within another language.

### Spark Core

Spark Core is the base for all parallel data processing and handles scheduling, optimization, RDD, and data abstraction. Spark Core provides the functional foundation for the Spark libraries, Spark SQL, Spark Streaming, the MLlib machine learning library, and GraphX graph data processing. The Spark Core and cluster manager distribute data across the Spark cluster and abstract it. This distribution and abstraction make handling Big Data very fast and user-friendly.

### Spark APIs

Spark includes a variety of application programming interfaces (APIs) to bring the power of Spark to the broadest audience. Spark SQL allows for interaction with RDD data in a relational manner. Spark also has a well-documented API for Scala, Java, Python, and R. Each language API in Spark has its specific nuances in how it handles data. RDDs, DataFrames, and Datasets are available in each language API. With APIs for such a variety of languages, Spark makes Big Data processing accessible to more diverse groups of people with backgrounds in development, data science, and statistics.

## Apache Spark and machine learning

Spark has various libraries that extend the capabilities to [machine learning, artificial intelligence (AI)](https://www.ibm.com/cloud/blog/ai-vs-machine-learning-vs-deep-learning-vs-neural-networks "AI-vs-Machine-Learning-vs-Deep-Learning-vs-Neural-Networks-What’s-the-Difference?"), and stream processing.

### Apache Spark MLlib

One of the critical capabilities of Apache Spark is the machine learning abilities available in the Spark MLlib. The Apache Spark MLlib provides an out-of-the-box solution for doing classification and regression, collaborative filtering, clustering, distributed linear algebra, decision trees, random forests, gradient-boosted trees, frequent pattern mining, evaluation metrics, and statistics. The capabilities of the MLlib, combined with the various data types Spark can handle, make Apache Spark an indispensable Big Data tool.

### Spark GraphX

In addition to having API capabilities, Spark has Spark GraphX, a new addition to Spark designed to solve graph problems. GraphX is a graph abstraction that extends RDDs for graphs and graph-parallel computation. Spark GraphX integrates with graph databases that store interconnectivity information or webs of connection information, like that of a social network.

### Spark Streaming

Spark Streaming is an extension of the core Spark API that enables scalable, fault-tolerant processing of live data streams. As Spark Streaming processes data, it can deliver data to file systems, databases, and live dashboards for real-time streaming analytics with Spark's machine learning and graph-processing algorithms. Built on the Spark SQL engine, Spark Streaming also allows for incremental batch processing that results in faster processing of streamed data.

## Spark vs. Apache Hadoop and MapReduce

“Spark vs. Hadoop” is a frequently searched term on the web, but as noted above, Spark is more of an enhancement to Hadoop—and, more specifically, to Hadoop's native data processing component, MapReduce. In fact, Spark is built on the MapReduce framework, and today, most Hadoop distributions include Spark.

Like Spark, MapReduce enables programmers to write applications that process huge data sets faster by processing portions of the data set in parallel across large clusters of computers. But where MapReduce processes data on disk, adding read and write times that slow processing, Spark performs calculations in _memory_, which is much faster. As a result, Spark can process data up to 100 times faster than MapReduce. 

Spark's built-in APIs for multiple languages make it more practical and approachable for developers than MapReduce, which has a reputation for being difficult to program. Unlike MapReduce, Spark can run stream-processing applications on Hadoop clusters using YARN, Hadoop's resource management and job scheduling framework. As noted above, Spark adds the capabilities of MLlib, GraphX, and SparkSQL. And Spark can handle data from other data sources outside of the Hadoop Application, including [Apache Kafka](https://www.ibm.com/cloud/learn/apache-kafka "apache-kafka").

Otherwise, Spark is compatible with and complementary to Hadoop. It can process Hadoop data, including data from HDFS (the Hadoop Distributed File System), HBase (a non-relational database that runs on HDFS), Apache Cassandra (a [NoSQL](https://www.ibm.com/cloud/learn/nosql-databases "nosql-databases") alternative to HDFS), and Hive (a Hadoop-based [data warehouse](https://www.ibm.com/cloud/learn/data-warehouse "data-warehouse")).

## Apache Spark and IBM Cloud

Spark is a powerful tool to add to an enterprise data solution to help with Big Data analysis or [AIOps](https://www.ibm.com/cloud/learn/aiops "aiops"). It also ties in well with existing IBM Big Data solutions.

[IBM Spectrum Conductor](https://www.ibm.com/products/spark-workload-management "spark-workload-management") is a [multi-tenant platform](https://www.ibm.com/cloud/learn/multi-tenant "multi-tenant") for deploying and managing Apache Spark other application frameworks on a common shared cluster of resources. Spectrum Conductor offers workload management, monitoring, alerting, reporting, and diagnostics and can run multiple current and different versions of Spark and other frameworks concurrently. Users can easily deploy and maintain Apache Spark with an integrated Spark distribution.

[IBM Watson](https://www.ibm.com/watson "watson") can be added to the mix to enable building AI, machine learning, and deep learning environments. IBM Watson provides an end-to-end workflow, services, and support to ensure your data scientists can focus on tuning and training the AI capabilities of a Spark application.

[IBM Analytics Engine](https://www.ibm.com/cloud/analytics-engine "analytics-engine") allows you to build a single advanced analytics solution with Apache Spark and Hadoop. IBM Analytics Engine lets users store data in an object storage layer, such as [IBM Cloud Object Storage](https://www.ibm.com/cloud/object-storage "object-storage"), only serving up clusters of compute notes when needed to help with flexibility, scalability, and maintainability of Big Data analytics platforms.

To get started, sign up for an IBMid and [create your IBM Cloud account](https://cloud.ibm.com/registration).