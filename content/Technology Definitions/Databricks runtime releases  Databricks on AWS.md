# Databricks runtime releases | Databricks on AWS

> Release notes for Databricks runtime releases.

June 16, 2021

This article lists all Databricks runtime releases and the schedule for supported releases. For more information about the Databricks Runtime support policy and schedule, see [Databricks runtime support lifecycle](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/databricks-runtime-ver.html#runtime-support).

Supported releases[](#supported-releases-1 "Permalink to this headline")
------------------------------------------------------------------------

The Databricks runtime versions listed in this section are currently supported.

### Supported Databricks runtime releases and support schedule[](#supported-databricks-runtime-releases-and-support-schedule "Permalink to this headline")

The following table lists the Apache Spark version, release date, and end-of-support date for supported Databricks Runtime releases.

  
| Version | Variant | Apache Spark version | Release date | End-of-support date |
| --- | --- | --- | --- | --- |
| 8.3 |   | 3.1.1 | Jun 08, 2021 | Dec 08, 2021 |
|   | [Databricks Runtime 8.3](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/8.3.html) |   |   |   |
|   | [Databricks Runtime 8.3 for Machine Learning](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/8.3ml.html) |   |   |   |
| 8.2 |   | 3.1.1 | Apr 22, 2021 | Oct 22, 2021 |
|   | [Databricks Runtime 8.2](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/8.2.html) |   |   |   |
|   | [Databricks Runtime 8.2 for Machine Learning](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/8.2ml.html) |   |   |   |
| 8.1 |   | 3.1.1 | Mar 22, 2021 | Sep 22, 2021 |
|   | [Databricks Runtime 8.1](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/8.1.html) |   |   |   |
|   | [Databricks Runtime 8.1 for Machine Learning](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/8.1ml.html) |   |   |   |
| 8.0 |   | 3.1.1 | Mar 02, 2021 | Sep 02, 2021 |
|   | [Databricks Runtime 8.0](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/8.0.html) |   |   |   |
|   | [Databricks Runtime 8.0 for Machine Learning](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/8.0ml.html) |   |   |   |
| 7.6 |   | 3.0.1 | Feb 08, 2021 | Aug 08, 2021 |
|   | [Databricks Runtime 7.6](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/7.6.html) |   |   |   |
|   | [Databricks Runtime 7.6 for Machine Learning](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/7.6ml.html) |   |   |   |
| 7.3 LTS |   | 3.0.1 | Sep 24, 2020 | Sep 24, 2022 |
|   | [Databricks Runtime 7.3 LTS](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/7.3.html) |   |   |   |
|   | [Databricks Runtime 7.3 LTS for Machine Learning](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/7.3ml.html) |   |   |   |
|   | [Databricks Runtime 7.3 LTS for Genomics](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/7.3genomics.html) |   |   |   |
| 6.4 [Extended Support](#extended) |   | 2.4.5 | Mar 05, 2021 | Dec 31, 2021 |
|   | [Databricks Runtime 6.4 Extended Support](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/6.4x.html) |   |   |   |
| 5.5 LTS |   | 2.4.3 | Jul 10, 2019 | Jul 10, 2021 |
|   | [Databricks Runtime 5.5 LTS](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/5.5.html) |   |   |   |
|   | [Databricks Runtime 5.5 LTS for Machine Learning](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/5.5ml.html) |   |   |   |

Note

Databricks Runtime 6.4 Extended Support will be supported through the end of 2021. It is provided for customers who are unable to migrate to Databricks Runtime 7.x or 8.x. Databricks Runtime 6.4 Extended Support uses Ubuntu 18.04.5 LTS instead of the deprecated Ubuntu 16.04.6 LTS operating system used in the original Databricks Runtime 6.4. Ubuntu 16.04.6 LTS support ended on April 1, 2021.

Databricks recommends that you migrate your workloads to Databricks Runtime 7.x or 8.x as soon as you can to get the benefits of Apache Spark 3.x and the many new features and improvements built into these newer runtimes. For migration information, see [Databricks Runtime 7.x migration guide](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/7.x-migration.html).

### Compatibility matrixes[](#compatibility-matrixes "Permalink to this headline")

This section lists Databricks Runtime and Databricks Runtime ML versions and their respective Delta Lake API and MLflow versions.

#### Delta Lake API compatibility matrix[](#delta-api-compatibility-matrix "Permalink to this headline")

  
| Databricks Runtime version | Delta Lake API version |
| --- | --- |
| 8.3 | [1.0.0](https://docs.delta.io/1.0.0/delta-apidoc.html) |
| 8.0 - 8.2 | [0.8.0](https://docs.delta.io/0.8.0/delta-apidoc.html) |
| 7.3 LTS, 7.6 | [0.7.0](https://docs.delta.io/0.7.0/delta-apidoc.html) |
| 6.4 Extended Support | [0.5.0](https://docs.delta.io/0.5.0/delta-apidoc.html) |

#### MLflow compatibility matrix[](#mlflow-compatibility-matrix "Permalink to this headline")

### Supported Databricks Light releases[](#supported-databricks-light-releases "Permalink to this headline")

  
| Version | Apache Spark version | Release date | End-of-support date |
| --- | --- | --- | --- |
| [2.4](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/2.4light.html) | 2.4.0+ | March 26, 2019 | – |

Beta releases[](#beta-releases "Permalink to this headline")
------------------------------------------------------------

Preview releases of Databricks Runtime are always labeled **Beta**. See [Databricks Runtime preview releases](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/release-types.html#runtime-releases). This section lists any current Databricks runtime Beta releases.

_There are no Databricks Runtime Beta releases at this time._

Unsupported releases[](#unsupported-releases "Permalink to this headline")
--------------------------------------------------------------------------

The Databricks runtime versions listed in this section are no longer supported by Databricks. For more information about the Databricks Runtime support policy and schedule, see [Databricks runtime support lifecycle](chrome-extension://cjedbglnccaioiolemnfhjncicchinao/databricks-runtime-ver.html#runtime-support).

### End-of-support history[](#end-of-support-history "Permalink to this headline")

[Release notes for unsupported releases](#unsupported-aws-releases)

  
| Version (all variants) | Apache Spark version | Release date | End-of-support date |
| --- | --- | --- | --- |
| 7.5 | 3.0.1 | Dec 16, 2020 | Jun 16, 2021 |
| 7.4 | 3.0.0 | Nov 03, 2020 | May 03, 2021 |
| 7.2 | 3.0.0 | Aug 11, 2020 | Feb 11, 2021 |
| 7.1 | 3.0.0 | Jul 21, 2020 | Jan 21, 2021 |
| 7.0 | 3.0.0 | Jun 17, 2020 | Jan 14, 2021 |
| 6.6 | 2.4.5 | May 26, 2020 | Nov 26, 2020 |
| 6.5 | 2.4.5 | Apr 14, 2020 | Oct 14, 2020 |
| 6.4 | 2.4.5 | Feb 26, 2020 | Apr 01, 2021 |
| 6.3 | 2.4.4 | Jan 22, 2020 | Jul 22, 2020 |
| 6.2 | 2.4.4 | Dec 03, 2019 | Jun 03, 2020 |
| 6.1 | 2.4.4 | Oct 16, 2019 | Apr 16, 2020 |
| 6.0 | 2.4.3 | Oct 01, 2019 | Apr 01, 2020 |
| 5.4 | 2.4 | Jun 03, 2019 | Dec 03, 2019 |
| 5.3 | 2.4 | Apr 03, 2019 | Dec 03, 2019 |
| 5.2 | 2.4 | Jan 24, 2019 | Sep 30, 2019 |
| 5.1 | 2.4 | Dec 18, 2018 | Aug 19, 2019 |
| 5.0 | 2.4 | Nov 08, 2018 | Jul 08, 2019 |
| 4.3 | 2.3 | Aug 10, 2018 | Apr 09, 2019 |
| 4.2 | 2.3 | Jul 09, 2018 | Mar 05, 2019 |
| 4.1 | 2.3 | May 17, 2018 | Jan 17, 2019 |
| 4.0 | 2.3 | Mar 01, 2018 | Nov 01, 2018 |
| 3.5 LTS | 2.2 | Dec 21, 2017 | Jan 02, 2020 |
| 3.4 | 2.2 | Nov 20, 2017 | Jul 30, 2018 |
| 3.3 | 2.2 | Oct 04, 2017 | Jul 30, 2018 |
| 3.2 | 2.2 | Sep 05, 2017 | Apr 30, 2018 |
| 3.1 | 2.2 | Aug 04, 2017 | Oct 30, 2017 |
| 3.0 | 2.2 | Jul 11, 2017 | Sep 05, 2017 |
| Spark 2.1 (Auto Updating) | 2.1 | Dec 22, 2016 | Jul 30, 2018 |
| Spark 2.1.1-db6 | 2.1 | Aug 03, 2017 | Jul 30, 2018 |
| Spark 2.1.1-db5 | 2.1 | May 31, 2017 | Aug 03, 2017 |
| Spark 2.1.1-db4 | 2.1 | Apr 25, 2017 | Jul 30, 2018 |
| Spark 2.0 (Auto Updating) | 2.0 | Jul 26, 2016 | Apr 30, 2018 |
| Spark 2.0.2-db4 | 2.0 | Mar 24, 2017 | Apr 30, 2018 |
| Spark 1.6.3-db2 | 1.6 | Mar 24, 2017 | Jun 30, 2018 |

### Release notes for unsupported releases[](#release-notes-for-unsupported-releases "Permalink to this headline")


[Source](https://docs.databricks.com/release-notes/runtime/releases.html)