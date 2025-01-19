---
tags:
  - Methods
  - Modelling
  - Data
  - Data_Architecture
  - EA
  - Semantic
aliases:
  - Semantic
  - SDM
---
From Wikipedia, the free encyclopedia

<table><caption>Semantic data model</caption><tbody><tr><th scope="row">Process type</th><td>semantics-based database description</td></tr><tr><th scope="row">Product(s)</th><td><a href="https://en.wikipedia.org/wiki/Gellish" title="Gellish">Gellish</a> (2005), <a href="https://en.wikipedia.org/wiki/ISO_15926" title="ISO 15926">ISO 15926</a>-2 (2002)</td></tr><tr><th scope="row">Leading companies</th><td>U.S. Air Force as <a href="https://en.wikipedia.org/wiki/Integrated_Computer-Aided_Manufacturing" title="Integrated Computer-Aided Manufacturing">Integrated Computer-Aided Manufacturing</a> program</td></tr><tr><th scope="row">Main facilities</th><td>Planning of Data Resources, Building of Shareable Databases, Evaluation of Vendor Software, Integration of Existing Databases</td></tr><tr><th scope="row">Year of invention</th><td>mid-1970s</td></tr></tbody></table>

[![[320px-A2_4_Semantic_Data_Models.svg.png]]](https://en.wikipedia.org/wiki/File:A2_4_Semantic_Data_Models.svg)

The relationship of "Semantic data models" with "physical data stores" and "real world".<sup id="cite_ref-FIPS184_1-0"><a href="https://en.wikipedia.org/wiki/Semantic_data_model#cite_note-FIPS184-1">[1]</a></sup>

A **semantic data model** (**SDM**) is a [high-level](https://en.wiktionary.org/wiki/high-level "wiktionary:high-level") semantics-based database description and structuring formalism ([database model](https://en.wikipedia.org/wiki/Database_model "Database model")) for databases. This database model is designed to capture more of the meaning of an application environment than is possible with contemporary database models. An SDM specification describes a database in terms of the kinds of entities that exist in the application environment, the classifications and groupings of those entities, and the structural interconnections among them. SDM provides a collection of high-level modeling primitives to capture the semantics of an application environment. By accommodating derived information in a database structural specification, SDM allows the same information to be viewed in several ways; this makes it possible to directly accommodate the variety of needs and processing requirements typically present in database applications. The design of the present SDM is based on our experience in using a preliminary version of it. SDM is designed to enhance the effectiveness and usability of database systems. An SDM database description can serve as a formal specification and documentation tool for a database; it can provide a basis for supporting a variety of powerful user interface facilities, it can serve as a conceptual database model in the database design process; and, it can be used as the database model for a new kind of database management system.

## In software engineering\[[edit](https://en.wikipedia.org/w/index.php?title=Semantic_data_model&action=edit&section=1 "Edit section: In software engineering")\]

A **semantic data model** in [software engineering](https://en.wikipedia.org/wiki/Software_engineering "Software engineering") has various meanings:

1.  It is a [conceptual data model](https://en.wikipedia.org/wiki/Conceptual_data_model "Conceptual data model") in which semantic information is included. This means that the model describes the meaning of its instances. Such a semantic [data model](https://en.wikipedia.org/wiki/Data_model "Data model") is an abstraction that defines how the stored [symbols](https://en.wikipedia.org/wiki/Symbol "Symbol") (the instance data) relate to the real world.<sup id="cite_ref-FIPS184_1-1"><a href="https://en.wikipedia.org/wiki/Semantic_data_model#cite_note-FIPS184-1">[1]</a></sup>
2.  It is a [conceptual data model](https://en.wikipedia.org/wiki/Conceptual_data_model "Conceptual data model") that includes the capability to express and exchange information which enables parties to interpret meaning (semantics) from the instances, without the need to know the meta-model. Such semantic models are fact-oriented (as opposed to object-oriented). Facts are typically expressed by [binary relations](https://en.wikipedia.org/wiki/Binary_relations "Binary relations") between [data](https://en.wikipedia.org/wiki/Data "Data") elements, whereas higher order relations are expressed as collections of binary relations. Typically binary relations have the form of triples: Object-RelationType-Object. For example: the Eiffel Tower <is located in> Paris.

Typically the instance data of semantic data models explicitly include the kinds of relationships between the various data elements, such as <is located in>. To interpret the meaning of the facts from the instances, it is required that the meaning of the kinds of relations (relation types) be known. Therefore, semantic data models typically standardize such relation types. This means that the second kind of semantic data models enables that the instances express facts that include their own meanings. The second kind of semantic data models are usually meant to create semantic databases. The ability to include meaning in semantic databases facilitates building [distributed databases](https://en.wikipedia.org/wiki/Distributed_database "Distributed database") that enable applications to interpret the meaning from the content. This implies that semantic databases can be integrated when they use the same (standard) relation types. This also implies that in general they have a wider applicability than relational or [object-oriented databases](https://en.wikipedia.org/wiki/Object-oriented_database "Object-oriented database").

## Overview\[[edit](https://en.wikipedia.org/w/index.php?title=Semantic_data_model&action=edit&section=2 "Edit section: Overview")\]

The logical data structure of a [database management system](https://en.wikipedia.org/wiki/Database_management_system "Database management system") (DBMS), whether [hierarchical](https://en.wikipedia.org/wiki/Hierarchical_model "Hierarchical model"), [network](https://en.wikipedia.org/wiki/Network_model "Network model"), or [relational](https://en.wikipedia.org/wiki/Relational_model "Relational model"), cannot totally satisfy the [requirements](https://en.wikipedia.org/wiki/Requirements_analysis "Requirements analysis") for a conceptual definition of data, because it is limited in scope and biased toward the implementation strategy employed by the DBMS. Therefore, the need to define data from a [conceptual view](https://en.wikipedia.org/wiki/Three_schema_approach "Three schema approach") has led to the development of semantic data modeling techniques. That is, techniques to define the meaning of data within the context of its interrelationships with other data, as illustrated in the figure. The real world, in terms of resources, ideas, events, etc., are symbolically defined within physical data stores. A semantic data model is an abstraction which defines how the stored symbols relate to the real world. Thus, the model must be a true representation of the real world.<sup id="cite_ref-FIPS184_1-2"><a href="https://en.wikipedia.org/wiki/Semantic_data_model#cite_note-FIPS184-1">[1]</a></sup>

According to Klas and Schrefl (1995), the "overall goal of semantic data models is to capture more meaning of data by integrating relational concepts with more powerful abstraction concepts known from the [Artificial Intelligence](https://en.wikipedia.org/wiki/Artificial_Intelligence "Artificial Intelligence") field. The idea is to provide high level modeling primitives as an integral part of a data model in order to facilitate the representation of real world situations".<sup id="cite_ref-2"><a href="https://en.wikipedia.org/wiki/Semantic_data_model#cite_note-2">[2]</a></sup>

## History\[[edit](https://en.wikipedia.org/w/index.php?title=Semantic_data_model&action=edit&section=3 "Edit section: History")\]

The need for semantic data models was first recognized by the U.S. Air Force in the mid-1970s as a result of the [Integrated Computer-Aided Manufacturing](https://en.wikipedia.org/wiki/Integrated_Computer-Aided_Manufacturing "Integrated Computer-Aided Manufacturing") (ICAM) Program. The objective of this program was to increase manufacturing productivity through the systematic application of computer technology. The ICAM Program identified a need for better analysis and communication techniques for people involved in improving manufacturing productivity. As a result, the ICAM Program developed a series of techniques known as the IDEF (ICAM Definition) Methods which included the following:<sup id="cite_ref-FIPS184_1-3"><a href="https://en.wikipedia.org/wiki/Semantic_data_model#cite_note-FIPS184-1">[1]</a></sup>

-   [IDEF0](https://en.wikipedia.org/wiki/IDEF0 "IDEF0") used to produce a “function model” which is a structured representation of the activities or processes within the environment or system.
-   [IDEF1](https://en.wikipedia.org/wiki/IDEF1 "IDEF1") used to produce an “information model” which represents the structure and semantics of information within the environment or system.
    -   [IDEF1X](https://en.wikipedia.org/wiki/IDEF1X "IDEF1X") a semantic data modeling technique used to produce a graphical information model which represents the structure and semantics of information within an environment or system. Use of this standard permits the construction of semantic data models which may serve to support the management of data as a resource, the integration of information systems, and the building of computer databases.
-   [IDEF2](https://en.wikipedia.org/wiki/IDEF2 "IDEF2") used to produce a “dynamics model” which represents the time varying behavioral characteristics of the environment or system.

During the 1990s, the application of semantic modelling techniques resulted in the semantic data models of the second kind. An example of such is the semantic data model that is standardised as [ISO 15926](https://en.wikipedia.org/wiki/ISO_15926 "ISO 15926")\-2 (2002), which is further developed into the semantic modelling language [Gellish](https://en.wikipedia.org/wiki/Gellish "Gellish") (2005). The definition of the Gellish language is documented in the form of a semantic data model. Gellish itself is a semantic modelling language, that can be used to create other semantic models. Those semantic models can be stored in Gellish Databases, being semantic databases.

## Applications\[[edit](https://en.wikipedia.org/w/index.php?title=Semantic_data_model&action=edit&section=4 "Edit section: Applications")\]

A semantic data model can be used to serve many purposes. Some key objectives include:<sup id="cite_ref-FIPS184_1-4"><a href="https://en.wikipedia.org/wiki/Semantic_data_model#cite_note-FIPS184-1">[1]</a></sup>

-   Planning of data resources: A preliminary data model can be used to provide an overall view of the data required to run an enterprise. The model can then be analyzed to identify and scope projects to build shared data resources.
-   Building of shareable databases: A fully developed model can be used to define an application independent view of data which can be validated by users and then transformed into a physical database design for any of the various DBMS technologies. In addition to generating databases which are consistent and shareable, development costs can be drastically reduced through data modeling.
-   Evaluation of vendor software: Since a data model actually represents the infrastructure of an organization, vendor software can be evaluated against a company’s data model in order to identify possible inconsistencies between the infrastructure implied by the software and the way the company actually does business.
-   Integration of existing databases: By defining the contents of existing databases with semantic data models, an integrated data definition can be derived. With the proper technology, the resulting conceptual schema can be used to control transaction processing in a distributed database environment. The U.S. Air Force Integrated Information Support System (I2S2) is an experimental development and demonstration of this kind of technology, applied to a heterogeneous type of DBMS environments.

## See also\[[edit](https://en.wikipedia.org/w/index.php?title=Semantic_data_model&action=edit&section=5 "Edit section: See also")\]

-   [Computational mathematics](https://en.wikipedia.org/wiki/Computational_mathematics "Computational mathematics")
-   [Conceptual schema](https://en.wikipedia.org/wiki/Conceptual_schema "Conceptual schema")
-   [Entity-relationship model](https://en.wikipedia.org/wiki/Entity-relationship_model "Entity-relationship model")
-   [Information model](https://en.wikipedia.org/wiki/Information_model "Information model")
-   [Object-role modeling](https://en.wikipedia.org/wiki/Object-role_modeling "Object-role modeling")
-   [Ontology (information science)](https://en.wikipedia.org/wiki/Ontology_(information_science) "Ontology (information science)")
-   [Relational Model/Tasmania](https://en.wikipedia.org/wiki/Relational_Model/Tasmania "Relational Model/Tasmania")
-   [Semantic technology](https://en.wikipedia.org/wiki/Semantic_technology "Semantic technology")
-   [Three-schema approach](https://en.wikipedia.org/wiki/Three-schema_approach "Three-schema approach")

## References\[[edit](https://en.wikipedia.org/w/index.php?title=Semantic_data_model&action=edit&section=6 "Edit section: References")\]

![[12px-PD-icon.svg.png|Public Domain]] This article incorporates [public domain material](https://en.wikipedia.org/wiki/Copyright_status_of_works_by_the_federal_government_of_the_United_States "Copyright status of works by the federal government of the United States") from the [National Institute of Standards and Technology](https://www.nist.gov/)

1.  ^ [Jump up to: <sup><i><b>a</b></i></sup>](https://en.wikipedia.org/wiki/Semantic_data_model#cite_ref-FIPS184_1-0) [<sup><i><b>b</b></i></sup>](https://en.wikipedia.org/wiki/Semantic_data_model#cite_ref-FIPS184_1-1) [<sup><i><b>c</b></i></sup>](https://en.wikipedia.org/wiki/Semantic_data_model#cite_ref-FIPS184_1-2) [<sup><i><b>d</b></i></sup>](https://en.wikipedia.org/wiki/Semantic_data_model#cite_ref-FIPS184_1-3) [<sup><i><b>e</b></i></sup>](https://en.wikipedia.org/wiki/Semantic_data_model#cite_ref-FIPS184_1-4) [FIPS Publication 184](http://www.itl.nist.gov/fipspubs/idef1x.doc) [Archived](https://web.archive.org/web/20131203223034/http://www.itl.nist.gov/fipspubs/idef1x.doc) 2013-12-03 at the [Wayback Machine](https://en.wikipedia.org/wiki/Wayback_Machine "Wayback Machine") released of IDEF1X by the Computer Systems Laboratory of the National Institute of Standards and Technology (NIST). 21 December 1993.
2.  **[^](https://en.wikipedia.org/wiki/Semantic_data_model#cite_ref-2 "Jump up")** Wolfgang Klas, Michael Schrefl (1995). "Semantic data modeling" In: _Metaclasses and Their Application_. Book Series Lecture Notes in Computer Science. Publisher Springer Berlin / Heidelberg. Volume Volume 943/1995.

## Further reading\[[edit](https://en.wikipedia.org/w/index.php?title=Semantic_data_model&action=edit&section=7 "Edit section: Further reading")\]

-   Naphtali D. Rishe (1992). [Database Design: The Semantic Modeling Approach](https://users.cs.fiu.edu/~sdbtools/hpdrc/library/books/datades-book/). McGraw-Hill.
-   Johan ter Bekke (1992). _Semantic Data Modeling_. Prentice Hall.
-   Alfonso F. Cardenas and Dennis McLeod (1990). _Research Foundations in Object-Oriented and Semantic Database Systems_. Prentice Hall.
-   Peter Gray, Krishnarao G. Kulkarni and, Norman W. Paton (1992). _Object-Oriented Databases: A Semantic Data Model Approach_. Prentice-Hall International Series in Computer Science.
-   Michael Hammer and Dennis McLeod (1978). "The Semantic Data Model: a Modeling Mechanism for Data Base Applications." In: _Proc. ACM SIGMOD Int’l. Conf. on Management of Data_. Austin, Texas, May 31 - June 2, 1978, pp. 26–36.
-   Hammer, Michael, and Dennis McLeod. "Database Description with SDM: A Semantic Database Model." ACM Transactions on Database Systems (TODS) 6.3 (1981): 351-86. Web.

## External links\[[edit](https://en.wikipedia.org/w/index.php?title=Semantic_data_model&action=edit&section=8 "Edit section: External links")\]

-   [Semantic Data Modeling](http://www.jhterbekke.net/SemanticDataModeling.html) Johan ter Bekke tribute site.
-   [Technical analysis of semantic data modeling layer in BI tools](https://www.holistics.io/blog/the-ideal-semantic-layer)