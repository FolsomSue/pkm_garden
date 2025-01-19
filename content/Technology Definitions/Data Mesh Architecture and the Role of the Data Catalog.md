#Technology #definition #Data #Mesh 
# Data Mesh Architecture and the Role of the Data Catalog
The “data textile” wars continue! In [our first blog in this series](https://www.alation.com/blog/data-mesh-vs-data-fabric/), we define the terms _data fabric_ and _data mesh_. The [second blog](https://www.alation.com/blog/what-is-a-data-fabric/) took a deeper dive into data fabric, examining its key pillars and the role of the [data catalog](https://www.alation.com/blog/what-is-a-data-catalog/) in each. In this blog, we’ll do the same with data mesh, unpacking the four key pillars, with a few notes on the role of the data catalog.

While data fabric takes a product-and-tech-centric approach, data mesh takes a completely different perspective. Data mesh inverts the common model of having a centralized team (such as a data engineering team), who manage and transform data for wider consumption. In contrast to this common, centralized approach, a data mesh architecture calls for responsibilities to be distributed to the people closest to the data. Zhamak Dehghani of Thoughtworks [defined data mesh](https://martinfowler.com/articles/data-monolith-to-mesh.html#DataAndDistributedDomainDrivenArchitectureConvergence) in 2019, tying it to domain-driven design and calling upon data users to “embrace the reality of _ever present, ubiquitous_ and _distributed_ nature of data.”

Indeed, decentralization is at the core of domain-driven design (DDD), which divides a large domain into different zones, to be managed by the stakeholders who know those zones best. (This is a software-design approach favored by software leaders, and it’s quickly gaining traction for data leaders of all kinds.) In other words, under a data mesh framework, domain product owners are responsible for delivering _data as a product_.

But why is such an inversion needed? Because those closest to the data are best equipped to manage it capably. Furthermore, centralization creates bottlenecks. Middlemen — [data engineering](https://www.alation.com/solutions/data-engineers/) or IT teams — can’t possibly possess all the expertise needed to serve up quality data to the growing range of data consumers who need it.

As data collection has surged, and demands for data have grown in the enterprise, one single team can no longer meet the data demands of every department. The growing interest in data mesh signals an organizational (rather than technological) shift.

Yet technology still plays a key enabling role in making this shift a reality. So how can you seize the data mesh, and up-level your [data management](https://www.alation.com/data-management-with-data-catalogs/) and governance practices to catalyze business success? In this blog, we’ll answer that question by exploring the [four underpinning principles of data mesh](https://martinfowler.com/articles/data-mesh-principles.html#DomainOwnership), according to Dehghani:

-   Domain-oriented decentralized data ownership and architecture
-   Data as a product
-   Federated computational governance
-   Self-serve data infrastructure as a platform

Throughout, we’ll also explain how a data catalog plays an instrumental role in supporting a data mesh, particularly as they jointly support all data users with a self-serve platform.

![4 Principles of Data Mesh ](https://www.alation.com/wp-content/uploads/4-Principles-of-Data-Mesh.png)

## Principle #1: Domain Ownership and Architecture

The challenge of centralized data ownership comes down to lack of depth and breadth of expertise. When the central team lacks the expertise of, say, a marketing function — yet are tasked with serving up marketing data — the quality of that data becomes suspect, and distrust in that data is likely to become a problem. That lack of expertise may lead to bottlenecks in service, as distributors struggle to understand the nature of the request and serve up the data best equipped to address it.

The first principle of data mesh springs from a simple concept: _those closest to the data should be responsible for that data_. By “responsibility,” we mean the manipulation (creation and transformation), maintenance, and distribution of the data to the consumers who need it within the organization. This stands in contrast to the de _facto models_ of data ownership (lakes and warehouses), in which the people responsible for the data _infrastructure_ are also responsible for _serving_ the data.

Data mesh supporters argue that this centralized model is no longer tenable in the expanding data universe of the enterprise. As data landscapes grow more wild, vast, and complex, centralized data ownership has become unwieldy and impossible to scale.

Remember the idea that those who _build_ the data infrastructure are best positioned to manage its distribution? That model has failed to support rapid data growth. And the central responsible party has grown far removed from the data it is tasked with managing _and_ sharing.

A data mesh architecture distributes responsibility of data ownership to those who know that _domain_ of data best. Making the experts responsible for service streamlines the data-request pipeline, delivering higher quality data into the hands of those who need it more rapidly.

Yet some potential downsides to this model exist. Some argue that data governance and quality practices may vary between domains. Duplication of data, too, may become a problem, as siloed patterns emerge unique to the domains that host them. Yet these challenges can be mitigated by putting the appropriate technology in place (more on that later).

## Principle #2: Data as a product

Thus far, we’ve borrowed language from the world of economics to describe the challenge at hand. Data consumers need access to data products they can trust, and distributors play a key role in delivering the best quality data as quickly as they can to serve that need. Small wonder that the idea of “data as a product” has taken off, as demand for great data within the enterprise has surged.

Let’s dive into this idea and unpack how data as a product is a key principle to the value of data mesh.

Physical products make up the fabric of our lives. Let’s take a real-world example in blue jeans. What’s important to buyers (i.e., consumers) of blue jeans?

-   **Purchase experience.** _How easy is it to find your size and click “buy”? Are there reviews or useful details that inform your decision? How satisfied are you overall with the purchase experience?_
-   **Speed of delivery.** _How quickly did the jeans arrive? If delayed, did you get updates on when to expect them?_
-   **Quality of the product.** _Once purchased, did the jeans tear easily? (setting current fashion aside). Did they shrink two sizes after the first wash? Are they just for this season, or an article you can rely on for life?_

To ensure consumer satisfaction, the jeans producer (e.g., Levi’s, etc.) needs to think about all of the above — and then some!

Now let’s apply the same principles to data. If we consider data as a product, the data producers must ensure that their data products check the following boxes (with credit, again, to Dehghani for enumerating these boxes).

### What makes a valuable data product?

-   **Discoverable.** _Easy to find in natural language._
-   **Addressable.** _Easy to access (once found), assuming the end user has permissions. If they don’t have permissions, it’s vital they have a means to request access, or work with someone granted access._
-   **Trustworthy and truthful.** _Signals around the quality and integrity of the data are essential if people are to understand and trust it. Data provenance and lineage, for example, clarify an asset’s origin and past usages, important details for a newcomer to understand and trust that asset. Data observability — comprising identifying, troubleshooting, and resolving data issues — can be achieved through quality testing built by teams within each domain._
-   **Self-describing.** _The data must be easily understood and consumed — e.g., through data schemas, wiki-like articles, and other crowdsourced feedback, like deprecations or warnings._
-   **Interoperable and governed by global standards.** _With different teams responsible for data, governance will be federated (more on this later). But everyone must still abide by a global set of rules that reflect current regulatory laws that respect geography._
-   **Secure and governed by a global access control.** _Users must be able to access data securely — e.g., through RBAC policy definition._

Readers may notice these attributes echo other data management frameworks. The ‘[FAIR Guiding Principles for scientific data management and stewardship](https://www.nature.com/articles/sdata201618)’ is one such framework. FAIR emphasizes that data must be **F**indable, **A**ccessible, **I**nteroperable, and **R**eusable to benefit humans and machines alike. Similar to the data-as-a-product approach outlined here, the goal of applying FAIR principles is to optimize the reusability of data. “To achieve this,” the report argues, “metadata and data should be well-described so that they can be replicated and/or combined in different settings.”1

A data catalog is essential for several of these capabilities, according to Thoughtworks. In the last section, we’ll tie these key points to data catalog features to demonstrate how they support a self-service data environment.

## Principle #3: Federated computational governance

The problem of ownership has its roots in the overlap between data _management_ and _governance_. Historically, data governance and data management were conflated. This is changing. Gartner argues:

> _Many IT practices proceed from the false assumption that centralized governance also means centralized data management. In IT, we have made it a practice to conflate governance with management; this results in the fallacy that a data management instance has its own authority. \[However\] Authority is bestowed upon a data asset by the governance model. (“Gartner Quick Answer: Are Data Mesh and Fabric the Same or Different?”)._

As compliance laws grow more onerous, and data landscapes more complex, the need to separate management and governance into distinct disciplines grows pronounced. A data mesh emphasizes human expertise as the engine that drives these disciplines — and interweaves them into a coherent whole.

Indeed, a core appeal of a data mesh and fabric is the implication of interwoven technologies. And as [Dehghani points out](https://martinfowler.com/articles/data-mesh-principles.html#DomainOwnership), “to get value in forms of higher order datasets, insights, or machine intelligence, there is a need for these independent data products to interoperate.”

As previously stated, a data mesh _decentralizes_ the management of data to the relevant subject matter experts. As such, [a data mesh implementation](https://martinfowler.com/articles/data-mesh-principles.html#DomainOwnership) “requires a governance model that embraces _decentralization and domain self-sovereignty, interoperability through global standardization, a dynamic topology, and, most importantly, automated execution of decisions by the platform._” In this way, a conflict arises: which _rules_ are universal, and which are centralized? Which _practices_ are universal, and which must be tailored by domain?

This is a difficult task to unpack. It demands “maintaining an [_equilibrium_](https://martinfowler.com/articles/data-mesh-principles.html#DomainOwnership) _between centralization_ _and_ _decentralization_.” It also requires that data governance leaders determine “what decisions need to be localized to each domain and what decisions should be made globally for all [domains](https://martinfowler.com/articles/data-mesh-principles.html#DomainOwnership).” Again, the expertise of those closest to the data is a crucial guiding light to these decisions. These experts will have a comprehensive view of what it takes to produce data of value, and deliver it to consumers in such a way as to guarantee their success.

### The future of federated governance

Automation will play an increasingly vital role in this realm. After all, governance policies and their standards are associated with root data assets, jurisdictions, data locations, consumer locations, and intended uses.

Those associations ‘tell’ data owners who produce products what can and can’t be done — both from a regulatory viewpoint and a best practices one. Rules can be automated based on these associations. These automated rules, in turn, ‘tell’ consumers who request product access that they must adhere to a contract of usage (like a Data Sharing Agreement). Such rules can monitor behavior and ‘tell’ the governing body if everyone is in compliance (and who’s breaking the rules!) These are valuable systems for enterprise risk management. Automation is rapidly making these use-case visions a reality.

Yet traditional data governance has been a challenging legacy to shake off. It forced a top-down, centralized approach to compliance that over-burdened IT, creating data bottlenecks (and frustrated consumers). What’s needed today is a global view of all data, alongside the policies that dictate its appropriate usage.

Ideally, folks have access to the data they need, with just-in-time governance guardrails that guide smart, compliant use. In this way, the regulatory and compliance needs of the business are met, but so too are the needs of data consumers who seek to use data wisely and compliantly.

## Principle #4: The Self-Serve Data Infrastructure as a Platform

We’ve discussed expertise and domain ownership and how this supports data as a product. Now, we turn our attention to technology. What role does technology play in the data mesh? And how can technology utilize a mesh infrastructure to support a self-service environment? Let’s answer this question by persona needs.

### What personas benefit from a self-service data mesh?

-   **For producers:** _Producers need a place to manage their data products (store, create, curate, destroy, etc.) and make those products accessible to consumers._
-   **For consumers:** _Consumers need a place to find data products, within a UI that guides how to use these products compliantly and successfully._

But to what use case does this apply? Storage? Compute? Networking? Data development environment? Discovery environment? Yes to all use cases!

Three separate _planes_ are needed for both producers and consumers within the self-serve data platform, according to Thoughtworks.

### The three technology planes of a self-service data mesh are:

-   **Plane 1: Data Infrastructure Plane.** _Addresses networking, storage, access control. Examples include public cloud vendors like AWS, Azure, and GCP._
-   **Plane 2:** **Data Product Developer Experience Plane.** _This plane uses “[declarative interfaces to manage the lifecycle of a data product](https://www.idc.com/getdoc.jsp?containerId=US45633720)” to help developers, for example, build, deploy, and monitor data products. This is relevant to many development environments, depending on the underlying repository, e.g., SQL for cloud data warehouses._
-   **Plane 3:** **Mesh Supervision Plane.** _This is a consumer-facing place to discover & explore data products, curate data, manage security policies, etc. While some may call it a data marketplace, others see the data catalog as the mesh supervision plane. Simply put, this plane addresses the consumer needs discussed above: discoverability, trustworthiness, etc. And this is where the data catalog plays a role._

### How does the Alation Data Catalog support data consumers and producers?

To answer this question, let’s tie data catalog features to our initial points around **what makes a valuable data product?**

**Discoverability:** Google-like search connects _consumers_ to the data products most relevant to their search and project. _Producers_ can influence search rankings by endorsing data, indicating that it’s of high quality and fit for use for a wider audience. And query log processing determines popularity, thereby lightening the producer’s load.

![Alation’s data product registry spanning all domains.](https://www.alation.com/wp-content/uploads/data-product-registry.png)

_**Data product search & discovery** lets users browse for data products by domain, classifiers, certification, and other facets._

**Addressability:** _Consumers_ can use the data products they’ve found by referencing the consumable API endpoints, which appears in the data catalog. _Producers_ get the lineage details they need to create models and new assets that don’t break.

![Dashboard of Alation’s data catalog surfacing key domain related data assets to ensure addressability. ](https://www.alation.com/wp-content/uploads/domains.png)

_Alation surfaces domain related key data assets including terms, metrics, data products, and policies to ensure **addressability.**_

**Trustworthiness:** Data lineage flags assets that may have issues. The _producer_ can use manual lineage to signal where data came from and whether it should be trusted. The _consumer_ views lineage to understand the trustworthiness and provenance of supplied data.

![Dashboard of a data catalog displaying how compliance demands are satisfied by capabilities like data lineage. ](https://www.alation.com/wp-content/uploads/beverage-sales-data-source.png)

_Compliance demands are satisfied by capabilities like data lineage, which track data source and transformation, and flag data that may be of low quality or subject to compliance laws._

**Self-describing** data surfaces valuable metadata so consumers and producers alike can holistically understand an asset before using it for analysis.

![Description of a data product in a single, user-friendly interface.](https://www.alation.com/wp-content/uploads/general-ledger-chart-of-accounts.png)

_Data producers describe and classify their data products associating policies that enforce how it should (and should not) be used._

**Secure, interoperable,** and **governed** data adheres to global access control & standards and enforces policies. This empowers consumers to use data compliantly, and helps producers do the same.

![Dashboard of Alation’s data catalog policy center enabling governance leaders to enforce data policies at scale. ](https://www.alation.com/wp-content/uploads/policy-center-workflow.png)

_Policy Center enables governance leaders to enforce data policies at scale._

### When do you need a data mesh?

Upon achieving a certain level of data maturity, every organization will need a data fabric. At that stage, _some_ will require a data mesh to complement the data fabric. If your organization has a decentralized structure and boasts mature, agile governance processes, which can be federated, then you should consider a data mesh.

It’s also vital that you consider the people who manage your data. How far along is the maturity of your data management team? Are they overwhelmed and inundated by requests to distribute data? Is quality suffering because your engineers are responsible for distribution?If so, a data mesh can help decentralize those painful processes, and connect data consumers to the right experts (serving as data producers) more quickly.

## Conclusion

A surplus of data has led to a surplus of concomitant challenges. To many, data mesh emerges as a promising solution. And as demand for data-driven decision making surges, so too does the need for trustworthy data products that can fuel such informed choices. Business teams are tired of waiting on IT to deliver data they can use quickly. And as Gartner puts it, “A data mesh is a solution architecture for the specific goal of building business-focused data products _without_ preference or specification of the technology involved” (emphasis added).

It’s tempting to think that technology alone can solve the challenges of the modern data landscape. Proponents of the data mesh architecture see things differently. They realize that human expertise — with the right supporting technology — is a powerful means of solving modern data challenges. Data catalogs, which offer global standards around compliant data use, alongside data labeling, curation, and valuable crowdsourced feedback, leverage human signals and expertise at all levels to guide smarter human usage. Policy interpretation, meanwhile, is left to the domain owners who know best.