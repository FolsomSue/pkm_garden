---
aliases: [Data Fabric]
---
#Technology #definition #Data  #Fabric

# **Data Fabric**  
_(n) A design concept that serves as an integrated layer (fabric) of data and connecting processes._

___

Data fabric is now on the minds of most data management leaders. In our previous blog, [Data Mesh vs. Data Fabric: A Love Story](https://www.alation.com/blog/data-mesh-vs-data-fabric/), we defined data fabric and outlined its uses and motivations. As a reminder, here’s Gartner’s definition of data fabric:

_“A design concept that serves as an integrated layer (fabric) of data and connecting processes. A data fabric utilizes continuous analytics over existing, discoverable, and inferred metadata assets to support the design, deployment, and utilization of integrated and reusable data across all environments, including hybrid and multi-cloud platforms.”1_

In this blog, we will focus on the “integrated layer” part of this definition by examining each of the key layers of a comprehensive data fabric in more detail.

![Gartner’s Key Layers of a Comprehensive Data Fabric diagram displaying data sources and data consumers.](https://www.alation.com/wp-content/uploads/Gartners-key-pillar-of-comprehensive-data-fabric.png)

_The data catalog is a foundational layer of the data fabric. This marketecture diagram2 is a simplified version of its fellow from our [first blog](https://www.alation.com/blog/data-mesh-vs-data-fabric/). (This zoomed-in version has references to corresponding vendor markets removed.)_

Using this diagram as our guide, this blog will deep-dive into each layer of the data fabric, starting with the [data catalog](https://www.alation.com/blog/what-is-a-data-catalog/). Our goal is to demonstrate the foundational role of the data catalog, and how it influences the higher corresponding layers that form an effective data fabric.

Gartner starts with the foundation of the data fabric, the data catalog. The data catalog supports the identification, collection, and analysis of all data sources as well as all types of metadata, including “[technical, business, operational, and social](https://www.gartner.com/smarterwithgartner/data-fabric-architecture-is-key-to-modernizing-data-management-and-integration)” (more on “social” in a moment). I would caution against breezing past this, as there are some important nuances.

One nuance is that **the data catalog is more than a modern-day data dictionary**; it goes beyond basic dictionary features, like names for technical metadata, data types, keying, and constraints.

In a practical sense, a modern data catalog should capture a broad array of metadata that also serves a broader array of consumers. In concrete terms, that includes metadata for a broad array of asset classes, such as BI reports, business metrics, business terms, domains, functional business processes, and more. This is a key component of [active data governance](https://www.alation.com/blog/what-is-active-data-governance/). These capabilities are also key for a robust data fabric.

![Data Catalog Asset Classes broken down into ten boxes that say, data, analytics, BI reports, Business Capabilities, Policies, Metrics, Terms, and Roles/Profiles.](https://www.alation.com/wp-content/uploads/data-catalog-asset.png)

### The Power of Social Metadata

Another key nuance of a data fabric is that it captures social metadata. Social metadata captures the associations that people create with the data they produce and consume. An easy example of this is data usage. People often use the same data sources, so capturing knowledge about that usage, (including their role, team, and expertise), layers on important context.

But social extends even further; it includes the comments users make, assets they flag as favorites, the watches they set on assets, who they tag and how, and their level of expertise.

Social signals around data are powerful. Who uses what asset when? How do people collaborate, innovate, and achieve breakthroughs? Meaningful patterns are at play here. Valuable metadata is the invisible architecture. What can we learn from these hidden systems? Just like Gartner, we’re confident building out this capability will optimize productivity, business optimization, and user experience. The data catalog provides the foundational capabilities for this.

### The Data Catalog as a Business Foundation

Gartner is explicit: Data catalogs play a foundational role in the data fabric. And leaders are recognizing the value of a strong data foundation. Indeed, the foundation of your data architecture and strategy – and thus your business strategy – begins with choosing the best data catalog to support your business.

But how do you go about selecting the right data catalog? These two resources can help you get started:

-   White paper: [How to Evaluate a Data Catalog](https://www.alation.com/how-to-evaluate-a-data-catalog/)
-   Webinar: [Five Must-Haves for a Data Catalog](https://www.brighttalk.com/webcast/13655/499262)

At its best, a data catalog should empower data analysts, scientists, and anyone curious about data with tools to explore and understand it. If people in your organization struggle to find, understand, and trust enterprise data, that’s a clear sign that you’re in need of a data catalog.

In their second layer, Gartner emphasizes ‘activating’ metadata, but what exactly does that mean? If people are able to search and understand their data using metadata, isn’t it already ‘active’?

Gartner offers a concrete concept: **activating metadata involves the continuous analysis of metadata to compute key metrics**. This “analysis” is made possible in large part through machine learning (ML); the patterns and connections ML detects are then served to the data catalog (and other tools), which these tools leverage to make people- and machine-facing recommendations about data management and data integrations.

Simply put? Metadata powers a living, [sentient enterprise](https://www.alation.com/blog/alations-role-in-the-sentient-enterprise/), in which patterns around data usage are woven into a self-improving system.

Raising the level of metadata-driven automation is key to achieving autonomous operations. Automation lets users monitor targets and trigger remediation actions without having to use an intermediary (a human) in a high-touch, coordinating capacity. Realizing that full vision will take some time, so let’s take stock of what you can already do with the data catalog to start down this path.

A modern data catalog should learn from human behavior to better support the people who use it. Alation performs behavioral analysis, which intelligently identifies top users of data, name fields, new glossary terms, and more. [Alation Analytics](https://www.alation.com/solutions/analytics/), too, is a core capability to ‘close the measurement loop’, as it enables leaders to measure performance against specific targets with thresholds.  
![Opened laptop displaying the Top Users in Alation’s Data Catalog.](https://www.alation.com/wp-content/uploads/top-users-on-laptop-screen.png)

_Top users represent valuable metadata, particularly to newcomers with questions._

![AI and ML in action: Auto-suggestions streamline the buildout of business glossaries](https://www.alation.com/wp-content/uploads/ai-and-ml-in-action.png)

_AI and ML in action: Auto-suggestions streamline the buildout of business glossaries._

Forward-thinking users will want to use APIs to create monitoring scripts for all kinds of conditions, and then trigger notifications, Conversation tasks, and other actions. Alation makes all of this possible. These are practical examples of the active use of metadata to optimize the data fabric and reduce the volume of mundane repetitive tasks.

### What is a knowledge graph?

Gartner explicitly calls out the need for a ‘knowledge graph’ to activate data. A [knowledge graph](https://www.stardog.com/knowledge-graph/) is a way of first recording the relationship between assets of different types, capturing a deep, rich set of meaning, and then making that set of relationships easily discoverable and traversable by everyone.

A modern data catalog provides robust metadata assets and powerful features to leverage them, with all of its cross-linking capabilities between different asset types. But what does this look like from a user’s perspective?

As an example, a user may look at a column, click through to the description of a metric, then click through to a supporting policy. They can drill down to understand an asset, the language describing it, and the policies that govern it. The catalog interlinks rich semantics to show relationships and add context.

Some technologists may question the term ‘knowledge graph’. Facebook and Google use a specific implementation of a knowledge graph for what they do. From the perspective of a user’s experience, so do distinct data catalogs. But underlying technologies don’t all need to be the same in order to accomplish their specific objectives.

Modern data management leaders are turning their attention to the user experience, letting the method change ‘beneath the hood’ over time if needed.

Gartner’s fourth layer is aimed mostly at technical consumers who sit in IT or in another functional business organization. The emphasis is on their need to prepare, integrate, explore, and transform data. Gartner calls for the data fabric to provide compatibility and flexibility to serve this broad array of users, using a broad array of tools. The catch is, what does ‘integrated’ really mean?

We all want integration compatibility but don’t want the vendor lock-in and resulting silos that send us into yet another vicious cycle. The answer has three components. The data fabric should provide entitlement rights discovery, automated provisioning, and data exploration.

### Three Keys to Integration Compatibility for Your Data Fabric

**Entitlement rights discovery** means that the data fabric should automate access by user. In other words, the fabric acts as gatekeeper when someone has found data and requests access. In this scenario, the data fabric should be contextually aware of the user and proactively prevent or enable access and make suggestions. A great example of this is the use of Alation ecosystem partners like Immuta or Privacera, who provide attribute-based access control ABAC), which provide this context awareness.

**Automated provisioning** means someone should be able to initiate a request for data access from within the data fabric. On the surface, that seems like a fairly simple ticketing process, but an intelligent data fabric, coupled with governance and IT service management implementations, should do things like check usage and sharing policies based on the location of the requestor, data source origin, and classification of the data. It should also trigger requests for data sharing agreements and privacy impact assessments between organizations when required.

Metadata triggers important processes in the catalog. The [Alation Data Catalog](https://www.alation.com/product/data-catalog/) can trigger a provisioning request into an IT service management process that uses ServiceNow or Jira via the Open with feature extension. On the policy front, a feature like [Policy Center](https://www.alation.com/solutions/data-governance/data-policies/) empowers users to enforce and track policies at scale; this ensures that people use data compliantly, and organizations are prepared for compliance audits.

A practical example of automated provisioning comes from the work we have done on the EDM Council’s new [Cloud Data Management Capability](https://www.alation.com/blog/how-alation-snowflake-integrate-cloud-data-management-framework-cdmc/) framework for managing sensitive data in the cloud. In satisfying one of the thirteen key automation requirements, we used Alation’s deep integration with Snowflake to collect location awareness and combined that with Alation policy-bot automation. The policy bot conditionally triggered actions including provisioning workflows based on knowledge of the user, data location, and associated access policies. All of this is made possible by the richness of metadata and depth of integration with complementary technologies.

Finally, **data exploration** means that the data fabric should let users explore the data (not just the metadata) without having to leave the fabric. This will allow them to be certain it’s the data they need, at which point they can use their data prep or pipeline tools against the actual source to continue with the development phase of their work. Alation partners such as Dataiku, Trifacta, and Tableau are perfect examples. Their users move seamlessly between exploration of metadata and data to accelerate their progress.

You might argue that advocating for a broad array of tools using data sources directly invalidates or weakens the role of the data fabric.

On the contrary! The success of a data fabric depends on a strong ecosystem of complementary and interoperable technologies such as Alation has created. This provides all the power, flexibility, and speed for teams to use the best tools that fit their purpose, while also closing the improvement loop and reflecting that back into the fabric itself.

Alation already provides some of these capabilities and is working on others. For instance, technical power users can explore the actual data through [Compose](https://www.alation.com/resource-center/guides/compose-11-reasons-to-love-this-sql-tool), the intelligent SQL editor.

![Dashboard of Alation’s data catalog providing technical power users how they can explore the actual data through Compose, the intelligent SQL editor.](https://www.alation.com/wp-content/uploads/dashboard-of-alation-data-catalog.png)

_Compose lets people explore the data forming their queries as they query._

Compose supports a broad range of query writers, from experts to newcomers. Those less familiar with SQL can search for technical terms using natural language. And this capability will be built out further with time. Alation’s acquisition of Lyngo Analytics, an NLP pioneer, will allow Alation to lower the barrier to entry to data newcomers, so anyone with a data-driven question can query in natural language to uncover insights instantly.

![Gartner’s Key Layers of a Comprehensive Data Fabric diagram displaying data sources and data consumers.](https://www.alation.com/wp-content/uploads/refresher-key-pillars-of-comprehensive-data-fabric.png)

_As a refresher: this diagram3 depicts the key layers of a data fabric._

We’ve arrived at the top layer of the fabric! Automated data orchestration interweaves data with connecting processes. [DataOps](https://www.gartner.com/smarterwithgartner/how-dataops-amplifies-data-and-analytics-business-value/) is the leading process concept in data today. (See Gartner’s “_[How DataOps Amplifies Data and Analytics Business Value](https://www.gartner.com/smarterwithgartner/how-dataops-amplifies-data-and-analytics-business-value)_”).

On the process side, DataOps is essentially an agile and unified approach to building data movements and transformation pipelines (think streaming and modern ETL). It emphasizes using process control and continuous improvement with integrated quality measurement.

On the data side, the data-fabric design concept focuses on a set of interconnected data services. Spoiler alert!

This is an overlapping data mesh concept that we will highlight in our next blog. These services allow both business consumers of data and DataOps developers to find, understand, and access the entire corporate ‘data estate’. The data services should provide standard mechanisms for these actions but do not stop there. The concept extends into the data services being augmented with rich contextual metadata based on what they can learn through AI/ML, usage patterns, etc.

Data fabric and DataOps are a part of the continued evolution of data management-centric approaches that improve data architecture, efficiency, and quality. These approaches extend the continuum of enterprise data warehouses, federated data marts, big data (Hadoop), and virtualization on top of distributed cloud file storage. How can data users navigate and understand such a complex landscape predictably?

In essence, the data fabric allows the underlying storage mechanisms and structures to be distributed, vary, and rapidly evolve, while providing a consistent and predictable way of understanding it. The data catalog supports human understanding by surfacing useful metadata (like usage statistics, conversations, and wiki-like articles). Real-time alerts about [data quality](https://www.alation.com/blog/what-is-data-quality-why-is-it-important/) in the catalog ensure that users can find the best data inputs to fuel your DataOps programs — and avoid data of dubious quality.

Alation supports several of the key elements in each layer of the data fabric. But there is no single tool that supports all layers comprehensively. In fact, Gartner argues that no single vendor completely addresses a holistic data fabric today. An integrated tech stack is the answer, with layers that interoperate.

An open platform is key, and an interoperable sibling can integrate that platform intelligently into other layers. Organizations must mix and match vendors in different markets to achieve an integrated data fabric that supports the business.

But what does integration look like in action? Tools like an intelligent SQL editor are useful for data prep (at the data integration layer). Alation’s SQL editor, Compose, integrates regulatory laws, compliance guidance, and auto-suggestions into the UX. Tools like this weave the captured knowledge of the catalog into other layers of the fabric.

A data fabric is part of a long evolution and history of improving how we manage data, provide self-service, and continually improve productivity. It has been made possible by decades of work on transaction systems, master data, data warehousing, [metadata management](https://www.alation.com/blog/metadata-management-best-practices), modeling, testing, transforming, and many other critical data disciplines. Data fabric is merely the latest and best approach that advances an organization’s data capabilities and maturity. So, realistically, any data department that aspires to support their organization with world-class capability needs a data fabric. The question becomes not ‘if we need a data fabric’ but ‘when do we implement it?’.

A few weeks ago I had a customer ask me, ‘Is Alation going to support a data fabric?’. In many ways, we already do! And after explaining much of what I’ve written above, they understood how the catalog will support their future data fabric.

Indeed, if you are already using the Alation Data Catalog, you are already in phase I of a data fabric implementation, and should feel confident defending that claim.  
The bottom line is the pursuit of a data fabric for the enterprise is a marathon, not a sprint. As such, it needs to be taken in stages. In fact, the full meaning of data fabric is still being teased out by pundits, researchers, and vendors.

But one point is clear: while a data fabric focuses on interwoven technologies, a data mesh focuses on expertise, emphasizing the role of people over technology. To learn more about a data mesh — and how it differs from data fabric — check out our next blog on the topic [here](https://www.alation.com/blog/data-mesh-architecture/).