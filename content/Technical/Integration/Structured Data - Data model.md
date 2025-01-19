---
aliases:
  - Structured_Data
  - Data_Model
tags:
  - EA
  - Data
  - Data_Integration
  - definition
  - Technology
---
# Structured Data / Data Model[![](https://upload.wikimedia.org/wikipedia/commons/thumb/2/2b/Data_modeling_context.svg/350px-Data_modeling_context.svg.png)](https://en.wikipedia.org/wiki/File:Data_modeling_context.svg)

Overview of a data-modeling context: Data model is based on Data, Data relationship, Data semantic and Data constraint. A data model provides the details of [information](https://en.wikipedia.org/wiki/Information "Information") to be stored, and is of primary use when the final product is the generation of computer [software code](https://en.wikipedia.org/wiki/Software_code "Software code") for an application or the preparation of a [functional specification](https://en.wikipedia.org/wiki/Functional_specification "Functional specification") to aid a [computer software](https://en.wikipedia.org/wiki/Computer_software "Computer software") make-or-buy decision. The figure is an example of the interaction between [process](https://en.wikipedia.org/wiki/Business_process_modeling "Business process modeling") and data models.<sup id="cite_ref-SS93_1-0"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-SS93-1">[1]</a></sup>

A **data model**<sup id="cite_ref-2"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-2">[2]</a></sup><sup id="cite_ref-w3cxpath_3-0"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-w3cxpath-3">[3]</a></sup><sup id="cite_ref-npmdatamodel_4-0"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-npmdatamodel-4">[4]</a></sup><sup id="cite_ref-5"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-5">[5]</a></sup><sup id="cite_ref-6"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-6">[6]</a></sup> is an [abstract model](https://en.wikipedia.org/wiki/Abstract_model "Abstract model") that organizes elements of [data](https://en.wikipedia.org/wiki/Data "Data") and [standardizes](https://en.wikipedia.org/wiki/Standardization "Standardization") how they relate to one another and to the properties of real-world [entities](https://en.wikipedia.org/wiki/Entity "Entity"). For instance, a data model may specify that the data element representing a car be composed of a number of other elements which, in turn, represent the color and size of the car and define its owner.

The corresponding professional activity is called generally _[data modeling](https://en.wikipedia.org/wiki/Data_modeling "Data modeling")_ or, more specifically, _[database design](https://en.wikipedia.org/wiki/Database_design "Database design")_. Data models are typically specified by a data expert, data specialist, data scientist, data librarian, or a data scholar. A data [modeling language](https://en.wikipedia.org/wiki/Modeling_language "Modeling language") and notation are often represented in graphical form as diagrams.<sup id="cite_ref-MRM99_7-0"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-MRM99-7">[7]</a></sup>

A data model can sometimes be referred to as a [data structure](https://en.wikipedia.org/wiki/Data_structure "Data structure"), especially in the context of [programming languages](https://en.wikipedia.org/wiki/Programming_language "Programming language"). Data models are often complemented by [function models](https://en.wikipedia.org/wiki/Function_model "Function model"), especially in the context of [enterprise models](https://en.wikipedia.org/wiki/Enterprise_model "Enterprise model").

A data model explicitly determines the _structure of data_; conversely, **structured data** is data organized according to an explicit data model or data structure. Structured data is in contrast to _[unstructured data](https://en.wikipedia.org/wiki/Unstructured_data "Unstructured data")_ and _[semi-structured data](https://en.wikipedia.org/wiki/Semi-structured_data "Semi-structured data")_.

## Overview\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=1 "Edit section: Overview")\]

The term _**data model**_ can refer to two distinct but closely related concepts. Sometimes it refers to an abstract formalization of the [objects](https://en.wikipedia.org/wiki/Object_(philosophy) "Object (philosophy)") and relationships found in a particular application domain: for example the customers, products, and orders found in a manufacturing organization. At other times it refers to the set of concepts used in defining such formalizations: for example concepts such as entities, attributes, relations, or tables. So the "data model" of a banking application may be defined using the entity–relationship "data model". This article uses the term in both senses.

Managing large quantities of structured and [unstructured data](https://en.wikipedia.org/wiki/Unstructured_data "Unstructured data") is a primary function of [information systems](https://en.wikipedia.org/wiki/Information_system "Information system"). Data models describe the structure, manipulation, and integrity aspects of the data stored in data management systems such as relational databases. They may also describe data with a looser structure, such as [word processing](https://en.wikipedia.org/wiki/Word_processor "Word processor") documents, [email messages](https://en.wikipedia.org/wiki/Email "Email"), pictures, digital audio, and video: [XDM](https://en.wikipedia.org/wiki/XQuery_and_XPath_Data_Model "XQuery and XPath Data Model"), for example, provides a data model for [XML](https://en.wikipedia.org/wiki/XML "XML") documents.

### The role of data models\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=2 "Edit section: The role of data models")\]

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/9/93/3-4_Data_model_roles.svg/320px-3-4_Data_model_roles.svg.png)](https://en.wikipedia.org/wiki/File:3-4_Data_model_roles.svg)

How data models deliver benefit<sup id="cite_ref-MW99_8-0"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-MW99-8">[8]</a></sup>

The main aim of data models is to support the development of [information systems](https://en.wikipedia.org/wiki/Information_system "Information system") by providing the definition and format of data. According to West and Fowler (1999) "if this is done consistently across systems then compatibility of data can be achieved. If the same data structures are used to store and access data then different applications can share data. The results of this are indicated above. However, systems and interfaces often cost more than they should, to build, operate, and maintain. They may also constrain the business rather than support it. A major cause is that the quality of the data models implemented in systems and interfaces is poor".<sup id="cite_ref-MW99_8-1"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-MW99-8">[8]</a></sup>

-   "Business rules, specific to how things are done in a particular place, are often fixed in the structure of a data model. This means that small changes in the way business is conducted lead to large changes in computer systems and interfaces".<sup id="cite_ref-MW99_8-2"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-MW99-8">[8]</a></sup>
-   "Entity types are often not identified, or incorrectly identified. This can lead to replication of data, data structure, and functionality, together with the attendant costs of that duplication in development and maintenance".<sup id="cite_ref-MW99_8-3"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-MW99-8">[8]</a></sup>
-   "Data models for different systems are arbitrarily different. The result of this is that complex interfaces are required between systems that share data. These interfaces can account for between 25-70% of the cost of current systems".<sup id="cite_ref-MW99_8-4"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-MW99-8">[8]</a></sup>
-   "Data cannot be shared electronically with customers and suppliers, because the structure and meaning of data has not been standardized. For example, engineering design data and drawings for process plant are still sometimes exchanged on paper".<sup id="cite_ref-MW99_8-5"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-MW99-8">[8]</a></sup>

The reason for these problems is a lack of standards that will ensure that data models will both meet business needs and be consistent.<sup id="cite_ref-MW99_8-6"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-MW99-8">[8]</a></sup>

A data model explicitly determines the structure of data. Typical applications of data models include database models, design of information systems, and enabling exchange of data. Usually, data models are specified in a data modeling language.\[3\]

### Three perspectives\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=3 "Edit section: Three perspectives")\]

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/8/84/4-2_ANSI-SPARC_three_level_architecture.svg/320px-4-2_ANSI-SPARC_three_level_architecture.svg.png)](https://en.wikipedia.org/wiki/File:4-2_ANSI-SPARC_three_level_architecture.svg)

The ANSI/SPARC [three level architecture](https://en.wikipedia.org/wiki/Three_schema_approach "Three schema approach"). This shows that a data model can be an external model (or view), a conceptual model, or a physical model. This is not the only way to look at data models, but it is a useful way, particularly when comparing models.<sup id="cite_ref-MW99_8-7"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-MW99-8">[8]</a></sup>

A data model _instance_ may be one of three kinds according to [ANSI](https://en.wikipedia.org/wiki/ANSI "ANSI") in 1975:<sup id="cite_ref-9"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-9">[9]</a></sup>

1.  [Conceptual data model](https://en.wikipedia.org/wiki/Conceptual_data_model "Conceptual data model"): describes the semantics of a domain, being the scope of the model. For example, it may be a model of the interest area of an organization or industry. This consists of entity classes, representing kinds of things of significance in the domain, and relationship assertions about associations between pairs of entity classes. A conceptual schema specifies the kinds of facts or propositions that can be expressed using the model. In that sense, it defines the allowed expressions in an artificial 'language' with a scope that is limited by the scope of the model.
2.  [Logical data model](https://en.wikipedia.org/wiki/Logical_data_model "Logical data model"): describes the semantics, as represented by a particular data manipulation technology. This consists of descriptions of tables and columns, object oriented classes, and XML tags, among other things.
3.  [Physical data model](https://en.wikipedia.org/wiki/Physical_data_model "Physical data model"): describes the physical means by which data are stored. This is concerned with partitions, CPUs, tablespaces, and the like.

The significance of this approach, according to ANSI, is that it allows the three perspectives to be relatively independent of each other. Storage technology can change without affecting either the logical or the conceptual model. The table/column structure can change without (necessarily) affecting the conceptual model. In each case, of course, the structures must remain consistent with the other model. The table/column structure may be different from a direct translation of the entity classes and attributes, but it must ultimately carry out the objectives of the conceptual entity class structure. Early phases of many software development projects emphasize the design of a [conceptual data model](https://en.wikipedia.org/wiki/Conceptual_schema "Conceptual schema"). Such a design can be detailed into a [logical data model](https://en.wikipedia.org/wiki/Logical_data_model "Logical data model"). In later stages, this model may be translated into [physical data model](https://en.wikipedia.org/wiki/Physical_data_model "Physical data model"). However, it is also possible to implement a conceptual model directly.

## History\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=4 "Edit section: History")\]

One of the earliest pioneering works in modeling information systems was done by Young and Kent (1958),<sup id="cite_ref-10"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-10">[10]</a></sup><sup id="cite_ref-JAB07_11-0"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-JAB07-11">[11]</a></sup> who argued for "a precise and abstract way of specifying the informational and time characteristics of a [data processing](https://en.wikipedia.org/wiki/Data_processing "Data processing") problem". They wanted to create "a notation that should enable the [analyst](https://en.wikipedia.org/wiki/Systems_analyst "Systems analyst") to organize the problem around any piece of [hardware](https://en.wikipedia.org/wiki/Computer_hardware "Computer hardware")". Their work was the first effort to create an abstract specification and invariant basis for designing different alternative implementations using different hardware components. The next step in IS modeling was taken by [CODASYL](https://en.wikipedia.org/wiki/CODASYL "CODASYL"), an IT industry consortium formed in 1959, who essentially aimed at the same thing as Young and Kent: the development of "a proper structure for machine-independent problem definition language, at the system level of data processing". This led to the development of a specific IS [information algebra](https://en.wikipedia.org/wiki/Information_algebra "Information algebra").<sup id="cite_ref-JAB07_11-1"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-JAB07-11">[11]</a></sup>

In the 1960s data modeling gained more significance with the initiation of the [management information system](https://en.wikipedia.org/wiki/Management_information_system "Management information system") (MIS) concept. According to Leondes (2002), "during that time, the information system provided the data and information for management purposes. The first generation [database system](https://en.wikipedia.org/wiki/Database_system "Database system"), called [Integrated Data Store](https://en.wikipedia.org/wiki/Integrated_Data_Store "Integrated Data Store") (IDS), was designed by [Charles Bachman](https://en.wikipedia.org/wiki/Charles_Bachman "Charles Bachman") at General Electric. Two famous database models, the [network data model](https://en.wikipedia.org/wiki/Network_data_model "Network data model") and the [hierarchical data model](https://en.wikipedia.org/wiki/Hierarchical_data_model "Hierarchical data model"), were proposed during this period of time".<sup id="cite_ref-12"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-12">[12]</a></sup> Towards the end of the 1960s, [Edgar F. Codd](https://en.wikipedia.org/wiki/Edgar_F._Codd "Edgar F. Codd") worked out his theories of data arrangement, and proposed the [relational model](https://en.wikipedia.org/wiki/Relational_model "Relational model") for database management based on [first-order predicate logic](https://en.wikipedia.org/wiki/First-order_logic "First-order logic").<sup id="cite_ref-13"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-13">[13]</a></sup>

In the 1970s [entity–relationship modeling](https://en.wikipedia.org/wiki/Entity%E2%80%93relationship_model "Entity–relationship model") emerged as a new type of conceptual data modeling, originally formalized in 1976 by [Peter Chen](https://en.wikipedia.org/wiki/Peter_Chen "Peter Chen"). Entity–relationship models were being used in the first stage of [information system](https://en.wikipedia.org/wiki/Information_system "Information system") design during the [requirements analysis](https://en.wikipedia.org/wiki/Requirements_analysis "Requirements analysis") to describe information needs or the type of [information](https://en.wikipedia.org/wiki/Information "Information") that is to be stored in a [database](https://en.wikipedia.org/wiki/Database "Database"). This technique can describe any [ontology](https://en.wikipedia.org/wiki/Ontology_(computer_science) "Ontology (computer science)"), i.e., an overview and classification of concepts and their relationships, for a certain [area of interest](https://en.wikipedia.org/wiki/Universe_of_discourse "Universe of discourse").

In the 1970s [G.M. Nijssen](https://en.wikipedia.org/wiki/G.M._Nijssen "G.M. Nijssen") developed "Natural Language Information Analysis Method" (NIAM) method, and developed this in the 1980s in cooperation with [Terry Halpin](https://en.wikipedia.org/wiki/Terry_Halpin "Terry Halpin") into [Object–Role Modeling](https://en.wikipedia.org/wiki/Object%E2%80%93Role_Modeling "Object–Role Modeling") (ORM). However, it was Terry Halpin's 1989 PhD thesis that created the formal foundation on which Object–Role Modeling is based.

Bill Kent, in his 1978 book _Data and Reality,_<sup id="cite_ref-14"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-14">[14]</a></sup> compared a data model to a map of a territory, emphasizing that in the real world, "highways are not painted red, rivers don't have county lines running down the middle, and you can't see contour lines on a mountain". In contrast to other researchers who tried to create models that were mathematically clean and elegant, Kent emphasized the essential messiness of the real world, and the task of the data modeler to create order out of chaos without excessively distorting the truth.

In the 1980s, according to Jan L. Harrington (2000), "the development of the [object-oriented](https://en.wikipedia.org/wiki/Object-oriented "Object-oriented") paradigm brought about a fundamental change in the way we look at data and the procedures that operate on data. Traditionally, data and procedures have been stored separately: the data and their relationship in a database, the procedures in an application program. Object orientation, however, combined an entity's procedure with its data."<sup id="cite_ref-JLH00_15-0"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-JLH00-15">[15]</a></sup>

During the early 1990s, three Dutch mathematicians Guido Bakema, Harm van der Lek, and JanPieter Zwart, continued the development on the work of [G.M. Nijssen](https://en.wikipedia.org/wiki/G.M._Nijssen "G.M. Nijssen"). They focused more on the communication part of the semantics. In 1997 they formalized the method Fully Communication Oriented Information Modeling [FCO-IM](https://en.wikipedia.org/wiki/FCO-IM "FCO-IM").

## Types\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=5 "Edit section: Types")\]

### Database model\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=6 "Edit section: Database model")\]

A database model is a specification describing how a database is structured and used.

Several such models have been suggested. Common models include:

[Flat model](https://en.wikipedia.org/wiki/Flat-file_database "Flat-file database")

This may not strictly qualify as a data model. The flat (or table) model consists of a single, two-dimensional array of data elements, where all members of a given column are assumed to be similar values, and all members of a row are assumed to be related to one another.

[Hierarchical model](https://en.wikipedia.org/wiki/Hierarchical_model "Hierarchical model")

The hierarchical model is similar to the network model except that links in the hierarchical model form a tree structure, while the network model allows arbitrary graph.

[Network model](https://en.wikipedia.org/wiki/Network_model "Network model")

This model organizes data using two fundamental constructs, called records and sets. Records contain fields, and sets define one-to-many relationships between records: one owner, many members. The network data model is an abstraction of the design concept used in the implementation of databases.

[Relational model](https://en.wikipedia.org/wiki/Relational_model "Relational model")

is a database model based on first-order predicate logic. Its core idea is to describe a database as a collection of predicates over a finite set of predicate variables, describing constraints on the possible values and combinations of values. The power of the relational data model lies in its mathematical foundations and a simple user-level paradigm.

[Object–relational model](https://en.wikipedia.org/wiki/Object%E2%80%93relational_model "Object–relational model")

Similar to a relational database model, but objects, classes, and inheritance are directly supported in [database schemas](https://en.wikipedia.org/wiki/Database_schema "Database schema") and in the query language.

[Object–role modeling](https://en.wikipedia.org/wiki/Object%E2%80%93role_modeling "Object–role modeling")

A method of data modeling that has been defined as "attribute free", and "fact-based". The result is a verifiably correct system, from which other common artifacts, such as ERD, UML, and semantic models may be derived. Associations between data objects are described during the database design procedure, such that normalization is an inevitable result of the process.

[Star schema](https://en.wikipedia.org/wiki/Star_schema "Star schema")

The simplest style of data warehouse schema. The star schema consists of a few "fact tables" (possibly only one, justifying the name) referencing any number of "dimension tables". The star schema is considered an important special case of the [snowflake schema](https://en.wikipedia.org/wiki/Snowflake_schema "Snowflake schema").

-   [![Flat model](https://upload.wikimedia.org/wikipedia/commons/thumb/3/31/FigFileConvert000a.svg/107px-FigFileConvert000a.svg.png)](https://en.wikipedia.org/wiki/File:FigFileConvert000a.svg "Flat model")
    
-   [![Hierarchical model](https://upload.wikimedia.org/wikipedia/commons/thumb/9/90/Hierarchisches_Datenbankmodell.svg/120px-Hierarchisches_Datenbankmodell.svg.png)](https://en.wikipedia.org/wiki/File:Hierarchisches_Datenbankmodell.svg "Hierarchical model")
    
-   [![Network model](https://upload.wikimedia.org/wikipedia/commons/thumb/4/41/Network_DB_model.svg/120px-Network_DB_model.svg.png)](https://en.wikipedia.org/wiki/File:Network_DB_model.svg "Network model")
    
-   [![Relational model](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8d/Relational_model_concepts.png/120px-Relational_model_concepts.png)](https://en.wikipedia.org/wiki/File:Relational_model_concepts.png "Relational model")
    
-   [![Concept-oriented model](https://upload.wikimedia.org/wikipedia/commons/thumb/6/62/Company_codm.png/120px-Company_codm.png)](https://en.wikipedia.org/wiki/File:Company_codm.png "Concept-oriented model")
    
    Concept-oriented model
    
-   [![Star schema](https://upload.wikimedia.org/wikipedia/commons/thumb/b/bb/Star-schema.png/120px-Star-schema.png)](https://en.wikipedia.org/wiki/File:Star-schema.png "Star schema")
    

### Data structure diagram\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=7 "Edit section: Data structure diagram")\]

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c4/Aggregate_Data_Structure_Diagram.jpg/240px-Aggregate_Data_Structure_Diagram.jpg)](https://en.wikipedia.org/wiki/File:Aggregate_Data_Structure_Diagram.jpg)

Example of a Data Structure Diagram

A data structure diagram (DSD) is a [diagram](https://en.wikipedia.org/wiki/Diagram "Diagram") and data model used to describe [conceptual data models](https://en.wikipedia.org/wiki/Conceptual_schema "Conceptual schema") by providing graphical notations which document [entities](https://en.wikipedia.org/wiki/Entity_class "Entity class") and their [relationships](https://en.wikipedia.org/wiki/Relational_model "Relational model"), and the [constraints](https://en.wikipedia.org/wiki/Integrity_constraints "Integrity constraints") that bind them. The basic graphic elements of DSDs are [boxes](https://en.wikipedia.org/wiki/Box "Box"), representing entities, and [arrows](https://en.wikipedia.org/wiki/Arrow "Arrow"), representing relationships. Data structure diagrams are most useful for documenting complex data entities.

Data structure diagrams are an extension of the [entity–relationship model](https://en.wikipedia.org/wiki/Entity%E2%80%93relationship_model "Entity–relationship model") (ER model). In DSDs, [attributes](https://en.wikipedia.org/wiki/Attribute_(computing) "Attribute (computing)") are specified inside the entity boxes rather than outside of them, while relationships are drawn as boxes composed of attributes which specify the constraints that bind entities together. DSDs differ from the ER model in that the ER model focuses on the relationships between different entities, whereas DSDs focus on the relationships of the elements within an entity and enable users to fully see the links and relationships between each entity.

There are several styles for representing data structure diagrams, with the notable difference in the manner of defining [cardinality](https://en.wikipedia.org/wiki/Cardinality_(data_modeling) "Cardinality (data modeling)"). The choices are between arrow heads, inverted arrow heads ([crow's feet](https://en.wikipedia.org/wiki/Entity%E2%80%93relationship_model "Entity–relationship model")), or numerical representation of the cardinality.

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/c/ca/B_5_1_IDEF1X_Diagram.jpg/240px-B_5_1_IDEF1X_Diagram.jpg)](https://en.wikipedia.org/wiki/File:B_5_1_IDEF1X_Diagram.jpg)

Example of an [IDEF1X](https://en.wikipedia.org/wiki/IDEF1X "IDEF1X") entity–relationship diagrams used to model IDEF1X itself<sup id="cite_ref-FIPS184_16-0"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-FIPS184-16">[16]</a></sup>

### Entity–relationship model\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=8 "Edit section: Entity–relationship model")\]

An entity–relationship model (ERM), sometimes referred to as an entity–relationship diagram (ERD), could be used to represent an abstract [conceptual data model](https://en.wikipedia.org/wiki/Conceptual_schema "Conceptual schema") (or [semantic data model](https://en.wikipedia.org/wiki/Semantic_data_model "Semantic data model") or physical data model) used in [software engineering](https://en.wikipedia.org/wiki/Software_engineering "Software engineering") to represent structured data. There are several notations used for ERMs. Like DSD's, [attributes](https://en.wikipedia.org/wiki/Attribute_(computing) "Attribute (computing)") are specified inside the entity boxes rather than outside of them, while relationships are drawn as lines, with the relationship constraints as descriptions on the line. The E-R model, while robust, can become visually cumbersome when representing entities with several attributes.

There are several styles for representing data structure diagrams, with a notable difference in the manner of defining cardinality. The choices are between arrow heads, inverted arrow heads (crow's feet), or numerical representation of the cardinality.

### Geographic data model\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=9 "Edit section: Geographic data model")\]

A data model in [Geographic information systems](https://en.wikipedia.org/wiki/Geographic_information_system "Geographic information system") is a mathematical construct for representing geographic objects or surfaces as data. For example,

-   the [vector](https://en.wikipedia.org/wiki/Vector_graphics "Vector graphics") data model represents geography as points, lines, and polygons
-   the raster data model represents geography as cell matrixes that store numeric values;
-   and the [Triangulated irregular network](https://en.wikipedia.org/wiki/Triangulated_irregular_network "Triangulated irregular network") (TIN) data model represents geography as sets of contiguous, nonoverlapping triangles.<sup id="cite_ref-17"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-17">[17]</a></sup>

-   [![Groups relate to process of making a map[18]](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d6/Groups_relate_to_the_process_of_making_a_map.jpg/120px-Groups_relate_to_the_process_of_making_a_map.jpg)](https://en.wikipedia.org/wiki/File:Groups_relate_to_the_process_of_making_a_map.jpg "Groups relate to process of making a map[18]")
    
    Groups relate to process of making a map<sup id="cite_ref-DRS03_18-0"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-DRS03-18">[18]</a></sup>
    
-   [![NGMDB data model applications[18]](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e1/NGMDB_data_model_application.jpg/120px-NGMDB_data_model_application.jpg)](https://en.wikipedia.org/wiki/File:NGMDB_data_model_application.jpg "NGMDB data model applications[18]")
    
    NGMDB data model applications<sup id="cite_ref-DRS03_18-1"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-DRS03-18">[18]</a></sup>
    
-   [![NGMDB databases linked together[18]](https://upload.wikimedia.org/wikipedia/commons/thumb/b/bc/NGMDB_databases_linked_together.jpg/120px-NGMDB_databases_linked_together.jpg)](https://en.wikipedia.org/wiki/File:NGMDB_databases_linked_together.jpg "NGMDB databases linked together[18]")
    
    NGMDB databases linked together<sup id="cite_ref-DRS03_18-2"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-DRS03-18">[18]</a></sup>
    
-   [![Representing 3D map information[18]](https://upload.wikimedia.org/wikipedia/commons/thumb/5/55/Representing_three-dimensional_map_information.jpg/90px-Representing_three-dimensional_map_information.jpg)](https://en.wikipedia.org/wiki/File:Representing_three-dimensional_map_information.jpg "Representing 3D map information[18]")
    
    Representing 3D map information<sup id="cite_ref-DRS03_18-3"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-DRS03-18">[18]</a></sup>
    

### Generic data model\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=10 "Edit section: Generic data model")\]

Generic data models are generalizations of conventional data models. They define standardized general relation types, together with the kinds of things that may be related by such a relation type. Generic data models are developed as an approach to solving some shortcomings of conventional data models. For example, different modelers usually produce different conventional data models of the same domain. This can lead to difficulty in bringing the models of different people together and is an obstacle for data exchange and data integration. Invariably, however, this difference is attributable to different levels of abstraction in the models and differences in the kinds of facts that can be instantiated (the semantic expression capabilities of the models). The modelers need to communicate and agree on certain elements that are to be rendered more concretely, in order to make the differences less significant.

### Semantic data model\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=11 "Edit section: Semantic data model")\]

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/5/58/A2_4_Semantic_Data_Models.svg/320px-A2_4_Semantic_Data_Models.svg.png)](https://en.wikipedia.org/wiki/File:A2_4_Semantic_Data_Models.svg)

Semantic data models<sup id="cite_ref-FIPS184_16-1"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-FIPS184-16">[16]</a></sup>

A semantic data model in software engineering is a technique to define the meaning of data within the context of its interrelationships with other data. A semantic data model is an abstraction that defines how the stored symbols relate to the real world.<sup id="cite_ref-FIPS184_16-2"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-FIPS184-16">[16]</a></sup> A semantic data model is sometimes called a [conceptual data model](https://en.wikipedia.org/wiki/Conceptual_data_model "Conceptual data model").

The logical data structure of a [database management system](https://en.wikipedia.org/wiki/Database_management_system "Database management system") (DBMS), whether [hierarchical](https://en.wikipedia.org/wiki/Hierarchical_model "Hierarchical model"), [network](https://en.wikipedia.org/wiki/Network_model "Network model"), or [relational](https://en.wikipedia.org/wiki/Relational_model "Relational model"), cannot totally satisfy the [requirements](https://en.wikipedia.org/wiki/Requirements_analysis "Requirements analysis") for a conceptual definition of data because it is limited in scope and biased toward the implementation strategy employed by the DBMS. Therefore, the need to define data from a [conceptual view](https://en.wikipedia.org/wiki/Three_schema_approach "Three schema approach") has led to the development of semantic data modeling techniques. That is, techniques to define the meaning of data within the context of its interrelationships with other data. As illustrated in the figure. The real world, in terms of resources, ideas, events, etc., are symbolically defined within physical data stores. A semantic data model is an abstraction that defines how the stored symbols relate to the real world. Thus, the model must be a true representation of the real world.<sup id="cite_ref-FIPS184_16-3"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-FIPS184-16">[16]</a></sup>

## Topics\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=12 "Edit section: Topics")\]

### Data architecture\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=13 "Edit section: Data architecture")\]

Data architecture is the design of data for use in defining the target state and the subsequent planning needed to hit the target state. It is usually one of several [architecture domains](https://en.wikipedia.org/wiki/Architecture_domain "Architecture domain") that form the pillars of an [enterprise architecture](https://en.wikipedia.org/wiki/Enterprise_architecture "Enterprise architecture") or [solution architecture](https://en.wikipedia.org/wiki/Solution_architecture "Solution architecture").

A data architecture describes the data structures used by a business and/or its applications. There are descriptions of data in storage and data in motion; descriptions of data stores, data groups, and data items; and mappings of those data artifacts to data qualities, applications, locations, etc.

Essential to realizing the target state, Data architecture describes how data is processed, stored, and utilized in a given system. It provides criteria for data processing operations that make it possible to design data flows and also control the flow of data in the system.

### Data modeling\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=14 "Edit section: Data modeling")\]

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5d/4-3_Data_Modelling_Today.svg/320px-4-3_Data_Modelling_Today.svg.png)](https://en.wikipedia.org/wiki/File:4-3_Data_Modelling_Today.svg)

The data modeling process

Data modeling in [software engineering](https://en.wikipedia.org/wiki/Software_engineering "Software engineering") is the process of creating a data model by applying formal data model descriptions using data modeling techniques. Data modeling is a technique for defining business [requirements](https://en.wikipedia.org/wiki/Requirement "Requirement") for a database. It is sometimes called _database modeling_ because a data model is eventually implemented in a database.<sup id="cite_ref-WBD04_19-0"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-WBD04-19">[19]</a></sup>

The figure illustrates the way data models are developed and used today. A [conceptual data model](https://en.wikipedia.org/wiki/Conceptual_data_model "Conceptual data model") is developed based on the data [requirements](https://en.wikipedia.org/wiki/Requirements "Requirements") for the application that is being developed, perhaps in the context of an [activity model](https://en.wikipedia.org/wiki/Activity_diagram "Activity diagram"). The data model will normally consist of entity types, attributes, relationships, integrity rules, and the definitions of those objects. This is then used as the start point for interface or [database design](https://en.wikipedia.org/wiki/Database_design "Database design").<sup id="cite_ref-MW99_8-8"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-MW99-8">[8]</a></sup>

### Data properties\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=15 "Edit section: Data properties")\]

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ef/3-2_Properties_of_data.svg/320px-3-2_Properties_of_data.svg.png)](https://en.wikipedia.org/wiki/File:3-2_Properties_of_data.svg)

Some important properties of data<sup id="cite_ref-MW99_8-9"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-MW99-8">[8]</a></sup>

Some important properties of data for which requirements need to be met are:

-   definition-related properties<sup id="cite_ref-MW99_8-10"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-MW99-8">[8]</a></sup>
    -   _relevance_: the usefulness of the data in the context of your business.
    -   _clarity_: the availability of a clear and shared definition for the data.
    -   _consistency_: the compatibility of the same type of data from different sources.
-   content-related properties
    -   _timeliness_: the availability of data at the time required and how up-to-date that data is.
    -   _accuracy_: how close to the truth the data is.
-   properties related to both definition and content
    -   _completeness_: how much of the required data is available.
    -   _accessibility_: where, how, and to whom the data is available or not available (e.g. security).
    -   _cost_: the cost incurred in obtaining the data, and making it available for use.

### Data organization\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=16 "Edit section: Data organization")\]

Another kind of data model describes how to organize data using a [database management system](https://en.wikipedia.org/wiki/Database_management_system "Database management system") or other data management technology. It describes, for example, relational tables and columns or object-oriented classes and attributes. Such a data model is sometimes referred to as the _[physical data model](https://en.wikipedia.org/wiki/Physical_data_model "Physical data model")_, but in the original ANSI three schema architecture, it is called "logical". In that architecture, the physical model describes the storage media (cylinders, tracks, and tablespaces). Ideally, this model is derived from the more conceptual data model described above. It may differ, however, to account for constraints like processing capacity and usage patterns.

While _data analysis_ is a common term for data modeling, the activity actually has more in common with the ideas and methods of _[synthesis](https://en.wiktionary.org/wiki/synthesis "wiktionary:synthesis")_ (inferring general concepts from particular instances) than it does with _[analysis](https://en.wiktionary.org/wiki/Analysis "wiktionary:Analysis")_ (identifying component concepts from more general ones). {_Presumably we call ourselves [systems analysts](https://en.wikipedia.org/wiki/Systems_analyst "Systems analyst") because no one can say [systems synthesists](https://en.wikipedia.org/wiki/Systems_analyst "Systems analyst")._} Data modeling strives to bring the data structures of interest together into a cohesive, inseparable, whole by eliminating unnecessary data redundancies and by relating data structures with [relationships](https://en.wikipedia.org/wiki/Relational_model "Relational model").

A different approach is to use [adaptive systems](https://en.wikipedia.org/wiki/Adaptive_system "Adaptive system") such as [artificial neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network "Artificial neural network") that can autonomously create implicit models of data.

### Data structure\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=17 "Edit section: Data structure")\]

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f7/Binary_tree.svg/240px-Binary_tree.svg.png)](https://en.wikipedia.org/wiki/File:Binary_tree.svg)

A [binary tree](https://en.wikipedia.org/wiki/Binary_tree "Binary tree"), a simple type of branching linked data structure

A data structure is a way of storing data in a computer so that it can be used efficiently. It is an organization of mathematical and logical concepts of data. Often a carefully chosen data structure will allow the most [efficient](https://en.wikipedia.org/wiki/Algorithmic_efficiency "Algorithmic efficiency") [algorithm](https://en.wikipedia.org/wiki/Algorithm "Algorithm") to be used. The choice of the data structure often begins from the choice of an [abstract data type](https://en.wikipedia.org/wiki/Abstract_data_type "Abstract data type").

A data model describes the structure of the data within a given domain and, by implication, the underlying structure of that domain itself. This means that a data model in fact specifies a dedicated _grammar_ for a dedicated artificial language for that domain. A data model represents classes of entities (kinds of things) about which a company wishes to hold information, the attributes of that information, and relationships among those entities and (often implicit) relationships among those attributes. The model describes the organization of the data to some extent irrespective of how data might be represented in a computer system.

The entities represented by a data model can be the tangible entities, but models that include such concrete entity classes tend to change over time. Robust data models often identify [abstractions](https://en.wikipedia.org/wiki/Abstraction "Abstraction") of such entities. For example, a data model might include an entity class called "Person", representing all the people who interact with an organization. Such an [abstract entity](https://en.wikipedia.org/wiki/Abstract_entity "Abstract entity") class is typically more appropriate than ones called "Vendor" or "Employee", which identify specific roles played by those people.

-   [![Array](https://upload.wikimedia.org/wikipedia/commons/thumb/0/01/Array_of_array_storage.svg/120px-Array_of_array_storage.svg.png)](https://en.wikipedia.org/wiki/File:Array_of_array_storage.svg "Array")
    
    Array
    
-   [![Hash table](https://upload.wikimedia.org/wikipedia/commons/thumb/8/85/HASHTB08_en.svg/120px-HASHTB08_en.svg.png)](https://en.wikipedia.org/wiki/File:HASHTB08_en.svg "Hash table")
    
-   [![Linked list](https://upload.wikimedia.org/wikipedia/commons/thumb/0/00/Singly_linked_list_insert_after.png/120px-Singly_linked_list_insert_after.png)](https://en.wikipedia.org/wiki/File:Singly_linked_list_insert_after.png "Linked list")
    
-   [![Stack (data structure)](https://upload.wikimedia.org/wikipedia/commons/thumb/2/29/Data_stack.svg/120px-Data_stack.svg.png)](https://en.wikipedia.org/wiki/File:Data_stack.svg "Stack (data structure)")
    

### Data model theory\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=18 "Edit section: Data model theory")\]

The term data model can have two meanings:<sup id="cite_ref-Beynon-Davies_P._2004_20-0"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-Beynon-Davies_P._2004-20">[20]</a></sup>

1.  A data model _theory_, i.e. a formal description of how data may be structured and accessed.
2.  A data model _instance_, i.e. applying a data model _theory_ to create a practical data model _instance_ for some particular application.

A data model theory has three main components:<sup id="cite_ref-Beynon-Davies_P._2004_20-1"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-Beynon-Davies_P._2004-20">[20]</a></sup>

-   The structural part: a collection of data structures which are used to create databases representing the entities or objects modeled by the database.
-   The integrity part: a collection of rules governing the constraints placed on these data structures to ensure structural integrity.
-   The manipulation part: a collection of operators which can be applied to the data structures, to update and query the data contained in the database.

For example, in the [relational model](https://en.wikipedia.org/wiki/Relational_model "Relational model"), the structural part is based on a modified concept of the [mathematical relation](https://en.wikipedia.org/wiki/Relation_(mathematics) "Relation (mathematics)"); the integrity part is expressed in [first-order logic](https://en.wikipedia.org/wiki/First-order_logic "First-order logic") and the manipulation part is expressed using the [relational algebra](https://en.wikipedia.org/wiki/Relational_algebra "Relational algebra"), [tuple calculus](https://en.wikipedia.org/wiki/Tuple_calculus "Tuple calculus") and [domain calculus](https://en.wikipedia.org/wiki/Domain_calculus "Domain calculus").

A data model instance is created by applying a data model theory. This is typically done to solve some business enterprise requirement. Business requirements are normally captured by a semantic [logical data model](https://en.wikipedia.org/wiki/Logical_data_model "Logical data model"). This is transformed into a physical data model instance from which is generated a physical database. For example, a data modeler may use a data modeling tool to create an [entity–relationship model](https://en.wikipedia.org/wiki/Entity%E2%80%93relationship_model "Entity–relationship model") of the corporate data repository of some business enterprise. This model is transformed into a [relational model](https://en.wikipedia.org/wiki/Relational_model "Relational model"), which in turn generates a [relational database](https://en.wikipedia.org/wiki/Relational_database "Relational database").

### Patterns\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=19 "Edit section: Patterns")\]

Patterns<sup id="cite_ref-LSPA08_21-0"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-LSPA08-21">[21]</a></sup> are common data modeling structures that occur in many data models.

## \[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=20 "Edit section: Related models")\]

### Data-flow diagram\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=21 "Edit section: Data-flow diagram")\]

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0f/Data_Flow_Diagram_Example.jpg/240px-Data_Flow_Diagram_Example.jpg)](https://en.wikipedia.org/wiki/File:Data_Flow_Diagram_Example.jpg)

Data-Flow Diagram example<sup id="cite_ref-22"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-22">[22]</a></sup>

A data-flow diagram (DFD) is a graphical representation of the "flow" of data through an [information system](https://en.wikipedia.org/wiki/Information_system "Information system"). It differs from the [flowchart](https://en.wikipedia.org/wiki/Flowchart "Flowchart") as it shows the _data_ flow instead of the _control_ flow of the program. A data-flow diagram can also be used for the [visualization](https://en.wikipedia.org/wiki/Data_visualization "Data visualization") of [data processing](https://en.wikipedia.org/wiki/Data_processing "Data processing") (structured design). Data-flow diagrams were invented by [Larry Constantine](https://en.wikipedia.org/wiki/Larry_Constantine "Larry Constantine"), the original developer of structured design,<sup id="cite_ref-23"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-23">[23]</a></sup> based on Martin and Estrin's "data-flow graph" model of computation.

It is common practice to draw a [context-level data-flow diagram](https://en.wikipedia.org/wiki/System_context_diagram "System context diagram") first which shows the interaction between the system and outside entities. The **DFD** is designed to show how a system is divided into smaller portions and to highlight the flow of data between those parts. This context-level data-flow diagram is then "exploded" to show more detail of the system being modeled

### Information model\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=22 "Edit section: Information model")\]

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/1/10/A_01_Audio_compact_disc_collection.svg/320px-A_01_Audio_compact_disc_collection.svg.png)](https://en.wikipedia.org/wiki/File:A_01_Audio_compact_disc_collection.svg)

Example of an [EXPRESS G](https://en.wikipedia.org/wiki/EXPRESS_(data_modeling_language) "EXPRESS (data modeling language)") [information model](https://en.wikipedia.org/wiki/Information_model "Information model")

An Information model is not a type of data model, but more or less an alternative model. Within the field of software engineering, both a data model and an information model can be abstract, formal representations of entity types that include their properties, relationships and the operations that can be performed on them. The entity types in the model may be kinds of real-world objects, such as devices in a network, or they may themselves be abstract, such as for the entities used in a billing system. Typically, they are used to model a constrained domain that can be described by a closed set of entity types, properties, relationships and operations.

According to Lee (1999)<sup id="cite_ref-Lee99_24-0"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-Lee99-24">[24]</a></sup> an information model is a representation of concepts, relationships, constraints, rules, and [operations](https://en.wikipedia.org/wiki/Operation_(mathematics) "Operation (mathematics)") to specify [data semantics](https://en.wikipedia.org/wiki/Semantic_data_model "Semantic data model") for a chosen domain of discourse. It can provide sharable, stable, and organized structure of information requirements for the domain context.<sup id="cite_ref-Lee99_24-1"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-Lee99-24">[24]</a></sup> More in general the term _information model_ is used for models of individual things, such as facilities, buildings, process plants, etc. In those cases the concept is specialised to [Facility Information Model](https://en.wikipedia.org/wiki/Facility_Information_Model "Facility Information Model"), [Building Information Model](https://en.wikipedia.org/wiki/Building_information_modeling "Building information modeling"), Plant Information Model, etc. Such an information model is an integration of a model of the facility with the data and documents about the facility.

An information model provides formalism to the description of a problem domain without constraining how that description is mapped to an actual implementation in software. There may be many mappings of the information model. Such mappings are called data models, irrespective of whether they are [object models](https://en.wikipedia.org/wiki/Object_model "Object model") (e.g. using [UML](https://en.wikipedia.org/wiki/Unified_Modeling_Language "Unified Modeling Language")), [entity–relationship models](https://en.wikipedia.org/wiki/Entity%E2%80%93relationship_model "Entity–relationship model") or [XML schemas](https://en.wikipedia.org/wiki/XML_schema "XML schema").

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e4/JKDOM.SVG/180px-JKDOM.SVG.png)](https://en.wikipedia.org/wiki/File:JKDOM.SVG)

[Document Object Model](https://en.wikipedia.org/wiki/Document_Object_Model "Document Object Model"), a standard [object model](https://en.wikipedia.org/wiki/Object_model "Object model") for representing [HTML](https://en.wikipedia.org/wiki/HTML "HTML") or [XML](https://en.wikipedia.org/wiki/XML "XML")

### Object model\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=23 "Edit section: Object model")\]

An object model in computer science is a collection of objects or classes through which a program can examine and manipulate some specific parts of its world. In other words, the object-oriented interface to some service or system. Such an interface is said to be the _object model of_ the represented service or system. For example, the [Document Object Model (DOM)](https://en.wikipedia.org/wiki/Document_Object_Model "Document Object Model") [\[1\]](http://www.w3.org/DOM/) is a collection of objects that represent a [page](https://en.wikipedia.org/wiki/Web_page "Web page") in a [web browser](https://en.wikipedia.org/wiki/Web_browser "Web browser"), used by [script](https://en.wikipedia.org/wiki/Scripting_language "Scripting language") programs to examine and dynamically change the page. There is a [Microsoft Excel](https://en.wikipedia.org/wiki/Microsoft_Excel "Microsoft Excel") object model<sup id="cite_ref-25"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-25">[25]</a></sup> for controlling Microsoft Excel from another program, and the [ASCOM](https://en.wikipedia.org/wiki/ASCOM_(standard) "ASCOM (standard)") Telescope Driver<sup id="cite_ref-26"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-26">[26]</a></sup> is an object model for controlling an astronomical telescope.

In [computing](https://en.wikipedia.org/wiki/Computing "Computing") the term _object model_ has a distinct second meaning of the general properties of [objects](https://en.wikipedia.org/wiki/Object_(computer_science) "Object (computer science)") in a specific computer [programming language](https://en.wikipedia.org/wiki/Programming_language "Programming language"), technology, notation or [methodology](https://en.wikipedia.org/wiki/Methodology "Methodology") that uses them. For example, the _[Java](https://en.wikipedia.org/wiki/Java_(programming_language) "Java (programming language)") object model_, the _[COM](https://en.wikipedia.org/wiki/Component_Object_Model "Component Object Model") object model_, or _the object model of [OMT](https://en.wikipedia.org/wiki/Object-modeling_technique "Object-modeling technique")_. Such object models are usually defined using concepts such as [class](https://en.wikipedia.org/wiki/Class_(computer_science) "Class (computer science)"), [message](https://en.wikipedia.org/wiki/Message_(computer_science) "Message (computer science)"), [inheritance](https://en.wikipedia.org/wiki/Inheritance_(object-oriented_programming) "Inheritance (object-oriented programming)"), [polymorphism](https://en.wikipedia.org/wiki/Polymorphism_in_object-oriented_programming "Polymorphism in object-oriented programming"), and [encapsulation](https://en.wikipedia.org/wiki/Information_hiding "Information hiding"). There is an extensive literature on formalized object models as a subset of the [formal semantics of programming languages](https://en.wikipedia.org/wiki/Formal_semantics_of_programming_languages "Formal semantics of programming languages").

### Object–role modeling\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=24 "Edit section: Object–role modeling")\]

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c4/Schema_for_Geologic_Surface.svg/320px-Schema_for_Geologic_Surface.svg.png)](https://en.wikipedia.org/wiki/File:Schema_for_Geologic_Surface.svg)

Example of the application of Object–Role Modeling in a "Schema for Geologic Surface", Stephen M. Richard (1999)<sup id="cite_ref-SMR99_27-0"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-SMR99-27">[27]</a></sup>

Object–Role Modeling (ORM) is a method for [conceptual modeling](https://en.wikipedia.org/wiki/Conceptual_modeling "Conceptual modeling"), and can be used as a tool for information and rules analysis.<sup id="cite_ref-28"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-28">[28]</a></sup>

Object–Role Modeling is a fact-oriented method for performing [systems analysis](https://en.wikipedia.org/wiki/Systems_analysis "Systems analysis") at the conceptual level. The quality of a database application depends critically on its design. To help ensure correctness, clarity, adaptability and productivity, information systems are best specified first at the conceptual level, using concepts and language that people can readily understand.

The conceptual design may include data, process and behavioral perspectives, and the actual DBMS used to implement the design might be based on one of many logical data models (relational, hierarchic, network, object-oriented, etc.).<sup id="cite_ref-msd_29-0"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-msd-29">[29]</a></sup>

### Unified Modeling Language models\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=25 "Edit section: Unified Modeling Language models")\]

The Unified Modeling Language (UML) is a standardized general-purpose [modeling language](https://en.wikipedia.org/wiki/Modeling_language "Modeling language") in the field of [software engineering](https://en.wikipedia.org/wiki/Software_engineering "Software engineering"). It is a [graphical language](https://en.wikipedia.org/wiki/Visual_language "Visual language") for visualizing, specifying, constructing, and documenting the [artifacts](https://en.wikipedia.org/wiki/Artifact_(software_development) "Artifact (software development)") of a software-intensive system. The Unified Modeling Language offers a standard way to write a system's blueprints, including:<sup id="cite_ref-OMG00_30-0"><a href="https://en.wikipedia.org/wiki/Data_model#cite_note-OMG00-30">[30]</a></sup>

-   Conceptual things such as [business processes](https://en.wikipedia.org/wiki/Business_process "Business process") and system functions
-   Concrete things such as [programming language](https://en.wikipedia.org/wiki/Programming_language "Programming language") statements, database schemas, and
-   Reusable [software components](https://en.wikipedia.org/wiki/Component-based_software_engineering "Component-based software engineering").

UML offers a mix of [functional models](https://en.wikipedia.org/wiki/Functional_model "Functional model"), data models, and [database models](https://en.wikipedia.org/wiki/Database_model "Database model").

## See also\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=26 "Edit section: See also")\]

-   [Business process model](https://en.wikipedia.org/wiki/Business_process_model "Business process model")
-   [Core architecture data model](https://en.wikipedia.org/wiki/Core_architecture_data_model "Core architecture data model")
-   [Common data model](https://en.wikipedia.org/wiki/Common_data_model "Common data model"), any standardised data model
-   [Data collection system](https://en.wikipedia.org/wiki/Data_collection_system "Data collection system")
-   [Data dictionary](https://en.wikipedia.org/wiki/Data_dictionary "Data dictionary")
-   [Data Format Description Language](https://en.wikipedia.org/wiki/Data_Format_Description_Language "Data Format Description Language") (DFDL)
-   [Distributional–relational database](https://en.wikipedia.org/wiki/Distributional%E2%80%93relational_database "Distributional–relational database")
-   [JC3IEDM](https://en.wikipedia.org/wiki/JC3IEDM "JC3IEDM")
-   [Process model](https://en.wikipedia.org/wiki/Process_model "Process model")

## References\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=27 "Edit section: References")\]

1.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-SS93_1-0 "Jump up")** Paul R. Smith & Richard Sarfaty Publications, LLC 2009
2.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-2 "Jump up")** ["UML Domain Modeling - Stack Overflow"](https://stackoverflow.com/a/3835214). _Stack Overflow_. Stack Exchange Inc. Retrieved 4 February 2017.
3.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-w3cxpath_3-0 "Jump up")** ["XQuery and XPath Data Model 3.1"](https://www.w3.org/TR/xpath-datamodel-3/). _World Wide Web Consortium (W3C)_. W3C. Retrieved 4 February 2017.
4.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-npmdatamodel_4-0 "Jump up")** ["DataModel"](https://www.npmjs.com/package/datamodel). _npm_. npm, Inc. Retrieved 4 February 2017.
5.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-5 "Jump up")** ["DataModel (Java EE 6)"](http://docs.oracle.com/javaee/6/api/javax/faces/model/DataModel.html). _Java Documentation_. Oracle. Retrieved 4 February 2017.
6.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-6 "Jump up")** Ostrovskiy, Stan. ["iOS: Three ways to pass data from Model to Controller"](https://medium.com/ios-os-x-development/ios-three-ways-to-pass-data-from-model-to-controller-b47cc72a4336#.ma7pr7no7). _Medium_. A Medium Corporation. Retrieved 4 February 2017.
7.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-MRM99_7-0 "Jump up")** Michael R. McCaleb (1999). ["A Conceptual Data Model of Datum Systems"](http://nvl.nist.gov/pub/nistpubs/jres/104/4/html/j44mac.htm#apa) [Archived](https://web.archive.org/web/20080921063005/http://nvl.nist.gov/pub/nistpubs/jres/104/4/html/j44mac.htm#apa) 2008-09-21 at the [Wayback Machine](https://en.wikipedia.org/wiki/Wayback_Machine "Wayback Machine"). National Institute of Standards and Technology. August 1999.
8.  ^ [Jump up to: <sup><i><b>a</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-MW99_8-0) [<sup><i><b>b</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-MW99_8-1) [<sup><i><b>c</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-MW99_8-2) [<sup><i><b>d</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-MW99_8-3) [<sup><i><b>e</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-MW99_8-4) [<sup><i><b>f</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-MW99_8-5) [<sup><i><b>g</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-MW99_8-6) [<sup><i><b>h</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-MW99_8-7) [<sup><i><b>i</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-MW99_8-8) [<sup><i><b>j</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-MW99_8-9) [<sup><i><b>k</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-MW99_8-10) Matthew West and Julian Fowler (1999). [Developing High Quality Data Models](https://sites.google.com/site/drmatthewwest/publications/princ03.pdf). The European Process Industries STEP Technical Liaison Executive (EPISTLE).
9.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-9 "Jump up")** American National Standards Institute. 1975. _ANSI/X3/SPARC Study Group on Data Base Management Systems; Interim Report_. FDT (Bulletin of ACM SIGMOD) 7:2.
10.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-10 "Jump up")** Young, J. W., and Kent, H. K. (1958). "Abstract Formulation of Data Processing Problems". In: _Journal of Industrial Engineering_. Nov-Dec 1958. 9(6), pp. 471-479
11.  ^ [Jump up to: <sup><i><b>a</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-JAB07_11-0) [<sup><i><b>b</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-JAB07_11-1) [Janis A. Bubenko jr](https://en.wikipedia.org/wiki/Janis_A._Bubenko_jr "Janis A. Bubenko jr") (2007) "From Information Algebra to Enterprise Modelling and Ontologies - a Historical Perspective on Modelling for Information Systems". In: _Conceptual Modelling in Information Systems Engineering_. [John Krogstie](https://en.wikipedia.org/wiki/John_Krogstie "John Krogstie") et al. eds. pp 1-18
12.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-12 "Jump up")** Cornelius T. Leondes (2002). _Database and Data Communication Network Systems: Techniques and Applications_. Page 7
13.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-13 "Jump up")** _"Derivability, Redundancy, and Consistency of Relations Stored in Large Data Banks"_, E.F. Codd, IBM Research Report, 1969
14.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-14 "Jump up")** [_Data and Reality_](http://www.bkent.net/Doc/darxrp.htm)
15.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-JLH00_15-0 "Jump up")** Jan L. Harrington (2000). _Object-oriented Database Design Clearly Explained_. p.4
16.  ^ [Jump up to: <sup><i><b>a</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-FIPS184_16-0) [<sup><i><b>b</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-FIPS184_16-1) [<sup><i><b>c</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-FIPS184_16-2) [<sup><i><b>d</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-FIPS184_16-3) [FIPS Publication 184](http://www.itl.nist.gov/fipspubs/idef1x.doc) [Archived](https://web.archive.org/web/20131203223034/http://www.itl.nist.gov/fipspubs/idef1x.doc) 2013-12-03 at the [Wayback Machine](https://en.wikipedia.org/wiki/Wayback_Machine "Wayback Machine") released of IDEF1X by the Computer Systems Laboratory of the National Institute of Standards and Technology (NIST). 21 December 1993 (withdrawn in 2008).
17.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-17 "Jump up")** Wade, T. and Sommer, S. eds. _[A to Z GIS](http://store.esri.com/esri/showdetl.cfm?SID=2&Product_ID=868&Category_ID=49)_
18.  ^ [Jump up to: <sup><i><b>a</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-DRS03_18-0) [<sup><i><b>b</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-DRS03_18-1) [<sup><i><b>c</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-DRS03_18-2) [<sup><i><b>d</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-DRS03_18-3) David R. Soller1 and Thomas M. Berg (2003). [The National Geologic Map Database Project: Overview and Progress](https://pubs.usgs.gov/of/2003/of03-471/soller1/index.html) U.S. Geological Survey Open-File Report 03–471.
19.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-WBD04_19-0 "Jump up")** [Whitten, Jeffrey L.](https://en.wikipedia.org/wiki/Whitten,_Jeffrey_L. "Whitten, Jeffrey L."); [Lonnie D. Bentley](https://en.wikipedia.org/wiki/Lonnie_D._Bentley "Lonnie D. Bentley"), [Kevin C. Dittman](https://en.wikipedia.org/wiki/Kevin_C._Dittman "Kevin C. Dittman"). (2004). _Systems Analysis and Design Methods_. 6th edition. [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [0-256-19906-X](https://en.wikipedia.org/wiki/Special:BookSources/0-256-19906-X "Special:BookSources/0-256-19906-X").
20.  ^ [Jump up to: <sup><i><b>a</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-Beynon-Davies_P._2004_20-0) [<sup><i><b>b</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-Beynon-Davies_P._2004_20-1) Beynon-Davies P. (2004). Database Systems 3rd Edition. Palgrave, Basingstoke, UK. [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [1-4039-1601-2](https://en.wikipedia.org/wiki/Special:BookSources/1-4039-1601-2 "Special:BookSources/1-4039-1601-2")
21.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-LSPA08_21-0 "Jump up")** "The Data Model Resource Book: Universal Patterns for Data Modeling" Len Silverstone & Paul Agnew (2008).
22.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-22 "Jump up")** John Azzolini (2000). [Introduction to Systems Engineering Practices](http://ses.gsfc.nasa.gov/ses_data_2000/000712_Azzolini.ppt). July 2000.
23.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-23 "Jump up")** W. Stevens, G. Myers, L. Constantine, "Structured Design", IBM Systems Journal, 13 (2), 115-139, 1974.
24.  ^ [Jump up to: <sup><i><b>a</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-Lee99_24-0) [<sup><i><b>b</b></i></sup>](https://en.wikipedia.org/wiki/Data_model#cite_ref-Lee99_24-1) Y. Tina Lee (1999). ["Information modeling from design to implementation"](http://www.mel.nist.gov/msidlibrary/doc/tina99im.pdf) National Institute of Standards and Technology.
25.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-25 "Jump up")** [Excel Object Model Overview](http://msdn2.microsoft.com/en-us/library/wss56bz7.aspx)
26.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-26 "Jump up")** ["ASCOM General Requirements"](http://ascom-standards.org/Standards/Requirements.htm). 2011-05-13. Retrieved 2014-09-25.
27.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-SMR99_27-0 "Jump up")** Stephen M. Richard (1999). [Geologic Concept Modeling](https://pubs.usgs.gov/of/1999/of99-386/richard.html). U.S. Geological Survey Open-File Report 99–386.
28.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-28 "Jump up")** Joachim Rossberg and Rickard Redler (2005). _Pro Scalable .NET 2.0 Application Designs._. Page 27.
29.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-msd_29-0 "Jump up")** [Object Role Modeling: An Overview (msdn.microsoft.com)](http://msdn2.microsoft.com/en-us/library/aa290383(VS.71).aspx). Retrieved 19 September 2008.
30.  **[^](https://en.wikipedia.org/wiki/Data_model#cite_ref-OMG00_30-0 "Jump up")** Grady Booch, Ivar Jacobson & Jim Rumbaugh (2005) [OMG Unified Modeling Language Specification](https://web.archive.org/web/20191029065137/https://pdfs.semanticscholar.org/f6b0/0ae65bc03ae3e2dc1edd8d9d1af3ea96f750.pdf).

## Further reading\[[edit](https://en.wikipedia.org/w/index.php?title=Data_model&action=edit&section=28 "Edit section: Further reading")\]

-   David C. Hay (1996). _[Data Model Patterns: Conventions of Thought](https://books.google.com/books?id=eUQbAAAAQBAJ&q=%22Data+Model+Patterns%3A+Conventions+of+Thought%22)_. New York:Dorset House Publishers, Inc.
-   Len Silverston (2001). _The Data Model Resource Book_ Volume 1/2. John Wiley & Sons.
-   Len Silverston & Paul Agnew (2008). _The Data Model Resource Book: Universal Patterns for data Modeling_ Volume 3. John Wiley & Sons.
-   Matthew West (2011) _Developing High Quality Data Models_ Morgan Kaufmann