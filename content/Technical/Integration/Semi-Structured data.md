---
tags:
  - EA
  - Data
  - Technology
  - definition
  - Data_Integration
---

# Semi-Structured Data
**Semi-structured data**<sup id="cite_ref-1"><a href="https://en.wikipedia.org/wiki/Semi-structured_data#cite_note-1">[1]</a></sup> is a form of [structured data](https://en.wikipedia.org/wiki/Structured_data "Structured data") that does not obey the tabular structure of data models associated with [relational databases](https://en.wikipedia.org/wiki/Relational_database "Relational database") or other forms of [data tables](https://en.wikipedia.org/wiki/Table_(database) "Table (database)"), but nonetheless contains [tags](https://en.wikipedia.org/wiki/Tag_(metadata) "Tag (metadata)") or other markers to separate semantic elements and enforce hierarchies of records and fields within the data. Therefore, it is also known as [self-describing](https://en.wikipedia.org/wiki/Self-describing "Self-describing") structure.

In semi-structured data, the entities belonging to the same class may have different [attributes](https://en.wikipedia.org/wiki/Attribute_(research) "Attribute (research)") even though they are grouped together, and the attributes' order is not important.

Semi-structured data are increasingly occurring since the advent of the [Internet](https://en.wikipedia.org/wiki/Internet "Internet") where [full-text](https://en.wikipedia.org/wiki/Full-text "Full-text") [documents](https://en.wikipedia.org/wiki/Documents "Documents") and [databases](https://en.wikipedia.org/wiki/Databases "Databases") are not the only forms of data anymore, and different applications need a medium for [exchanging information](https://en.wikipedia.org/wiki/Information_exchange "Information exchange"). In [object-oriented databases](https://en.wikipedia.org/wiki/Object_database "Object database"), one often finds semi-structured data.

## Types\[[edit](https://en.wikipedia.org/w/index.php?title=Semi-structured_data&action=edit&section=1 "Edit section: Types")\]

### XML\[[edit](https://en.wikipedia.org/w/index.php?title=Semi-structured_data&action=edit&section=2 "Edit section: XML")\]

[XML](https://en.wikipedia.org/wiki/XML "XML"),<sup id="cite_ref-2"><a href="https://en.wikipedia.org/wiki/Semi-structured_data#cite_note-2">[2]</a></sup> other markup languages, [email](https://en.wikipedia.org/wiki/Email "Email"), and [EDI](https://en.wikipedia.org/wiki/Electronic_Data_Interchange "Electronic Data Interchange") are all forms of semi-structured data. [OEM](https://en.wikipedia.org/wiki/Object_Exchange_Model "Object Exchange Model") (Object Exchange Model)<sup id="cite_ref-3"><a href="https://en.wikipedia.org/wiki/Semi-structured_data#cite_note-3">[3]</a></sup> was created prior to XML as a means of self-describing a data structure. XML has been popularized by web services that are developed utilizing [SOAP](https://en.wikipedia.org/wiki/SOAP "SOAP") principles.

Some types of data described here as "semi-structured", especially XML, suffer from the impression that they are incapable of structural rigor at the same functional level as Relational Tables and Rows. Indeed, the view of XML as inherently semi-structured (previously, it was referred to as "unstructured") has handicapped its use for a widening range of data-centric applications. Even documents, normally thought of as the epitome of semi-structure, can be designed with virtually the same rigor as [database schema](https://en.wikipedia.org/wiki/Database_schema "Database schema"), enforced by the [XML schema](https://en.wikipedia.org/wiki/XML_schema "XML schema") and processed by both commercial and custom software programs without reducing their usability by human readers.

In view of this fact, XML might be referred to as having "flexible structure" capable of human-centric flow and hierarchy as well as highly rigorous element structure and data typing.

The concept of XML as "human-readable", however, can only be taken so far. Some implementations/dialects of XML, such as the XML representation of the contents of a Microsoft Word document, as implemented in Office 2007 and later versions, utilize dozens or even hundreds of different kinds of tags that reflect a particular problem domain - in Word's case, formatting at the character and paragraph and document level, definitions of styles, inclusion of citations, etc. - which are nested within each other in complex ways. Understanding even a portion of such an XML document by reading it, let alone catching errors in its structure, is impossible without a very deep prior understanding of the specific XML implementation, along with assistance by software that understands the XML schema that has been employed. Such text is not "human-understandable" any more than a book written in Swahili (which uses the Latin alphabet) would be to an American or Western European who does not know a word of that language: the tags are symbols that are meaningless to a person unfamiliar with the domain.

### JSON\[[edit](https://en.wikipedia.org/w/index.php?title=Semi-structured_data&action=edit&section=3 "Edit section: JSON")\]

[JSON](https://en.wikipedia.org/wiki/JSON "JSON") or JavaScript Object Notation, is an open standard format that uses human-readable text to transmit data objects. JSON has been popularized by web services developed utilizing [REST](https://en.wikipedia.org/wiki/REST "REST") principles.

There is a new breed of databases such as [MongoDB](https://en.wikipedia.org/wiki/MongoDB "MongoDB") and [Couchbase](https://en.wikipedia.org/wiki/Couchbase "Couchbase") that store data natively in JSON format, leveraging the pros of semi-structured data architecture.

## Pros and cons\[[edit](https://en.wikipedia.org/w/index.php?title=Semi-structured_data&action=edit&section=4 "Edit section: Pros and cons")\]

### Advantages\[[edit](https://en.wikipedia.org/w/index.php?title=Semi-structured_data&action=edit&section=5 "Edit section: Advantages")\]

-   Programmers persisting objects from their application to a database do not need to worry about [object-relational impedance mismatch](https://en.wikipedia.org/wiki/Object-relational_impedance_mismatch "Object-relational impedance mismatch"), but can often serialize objects via a light-weight library.
-   Support for nested or hierarchical data often simplifies data models representing complex relationships between entities.
-   Support for lists of objects simplifies data models by avoiding messy translations of lists into a relational data model.

### Disadvantages\[[edit](https://en.wikipedia.org/w/index.php?title=Semi-structured_data&action=edit&section=6 "Edit section: Disadvantages")\]

-   The traditional relational data model has a popular and ready-made query language, [SQL](https://en.wikipedia.org/wiki/SQL "SQL").
-   Prone to "garbage in, garbage out"; by removing restraints from the data model, there is less forethought that is necessary to operate a data application.

## See also\[[edit](https://en.wikipedia.org/w/index.php?title=Semi-structured_data&action=edit&section=7 "Edit section: See also")\]

-   [Semi-structured model](https://en.wikipedia.org/wiki/Semi-structured_model "Semi-structured model")
-   [NoSQL](https://en.wikipedia.org/wiki/NoSQL "NoSQL")
-   [Unstructured data](https://en.wikipedia.org/wiki/Unstructured_data "Unstructured data")
-   [Structured data](https://en.wikipedia.org/wiki/Structured_data "Structured data")

## References\[[edit](https://en.wikipedia.org/w/index.php?title=Semi-structured_data&action=edit&section=8 "Edit section: References")\]

1.  **[^](https://en.wikipedia.org/wiki/Semi-structured_data#cite_ref-1 "Jump up")** Peter Buneman (1997). ["Semistructured data"](https://homepages.inf.ed.ac.uk/opb/papers/PODS1997a.pdf) (PDF). _Symposium on Principles of Database Systems_.
2.  **[^](https://en.wikipedia.org/wiki/Semi-structured_data#cite_ref-2 "Jump up")** [The Penn database group has semi-structured and XML data project](http://db.cis.upenn.edu/research/SS_XML.html)
3.  **[^](https://en.wikipedia.org/wiki/Semi-structured_data#cite_ref-3 "Jump up")** [Stanford Universities Lore DBMS](http://infolab.stanford.edu/lore/home/index.html)

## External links\[[edit](https://en.wikipedia.org/w/index.php?title=Semi-structured_data&action=edit&section=9 "Edit section: External links")\]

-   [UPenn Database Group](http://db.cis.upenn.edu/research/SS_XML.html) – semi-structured data and XML
-   [Semi-Structured data analytics: Relational or Hadoop platform?](http://www.ibmbigdatahub.com/blog/semi-structured-data-analytics-relational-or-hadoop-platform-part-1) by IBM