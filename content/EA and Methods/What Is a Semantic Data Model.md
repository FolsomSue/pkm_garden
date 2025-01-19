---
aliases:
  - Semantic
  - SDM
tags:
  - EA
  - Methods
  - Modelling
  - Data
  - Data_Architecture
  - Semantic
---
In simple terms, data is facts or numbers in an electronic format. It needs to be collected, stored, transformed, and processed to extract valuable information — an integral step of business decision-making. Different use cases require or carry various datasets, and understanding the relationships between these interconnected sets can help us utilize our data more efficiently.

Semantic data models (SDM) serve this very purpose. They describe objects and structures of datasets, allowing us to easily grasp the complex mechanics of our data.

## Semantic Data Model 101

Before we dive into further details about SDMs, let's answer two basic questions:

1.  What is a data model?
2.  What does “semantics” mean?

A data model is an abstract model that describes data elements and the relationships between them. To learn more about data models and their use cases, read our blog post on [what is a data model](https://www.gooddata.com/blog/what-a-data-model/).

Semantics relates to the study of references, specifically describing the real meaning between symbols or words. In computer science, semantics relates to the meaning of language constructs rather than their form.

What’s more, semantic data is data that has been prepared to assign meaning to the data. This is done by building data relationships between entities to provide data with the essential truth and importance for consumption. The usage of semantic data helps to maintain data consistency.

Semantic data consists of three components: two real objects, and one relationship between them.

So, what exactly is an SDM? An SDM, also known as a semantic database model, can be understood as a conceptual model. It is a data model defined on a higher level that captures the databases’ semantic description, structure, and form. The database is a data repository designed for easy access and management of data that is collected and used daily. The backbone of this database is a suitably designed data model.

The SDM describes and expands the meaning of the specific application environment in which this database is designed. The model includes descriptions of the entities, their classification, and the interconnection structure (i.e., their relationships). Essentially, it makes your data easier to understand.

The main difference between data models and SDMs is that SDMs explain the essence and graphical representation of different types of data models to increase their added value. While SDMs present a business-user-friendly perspective of the data, data models deal with various problems and convert them into different types of data models.

![A cloud representing Semantic Models. Beneath it is a landscape representing the Real World, and shapes representing Physical Data Stores.](https://www.gooddata.com/img/blog/_2000xauto/semantic-data-model.png "An SDM is a data model defined on a higher level.")

An SDM is a data model defined on a higher level.

_Image credit: [Wikipedia](https://en.wikipedia.org/wiki/Semantic_data_model#/media/File:A2_4_Semantic_Data_Models.svg)_

## How Do Semantic Data Models Work?

SDMs combine semantic and graphic visualization while adding value to different types of data models.

The analysis of input data requires an abstraction process that involves selecting specific qualities and parts of reality while rejecting others that are irrelevant to the specific solution (project, model, schema, etc.).

An SDM employs the following three different types of abstraction.

-   **Classification**: This classifies different objects in objective reality by using “instance of” relations, such as creating groups of objects by similar characteristics — a group of employees, for example.
-   **Aggregation**: Aggregation defines a new object from a set of objects that become its components using “has a” relations. For this example, we can mention an employer with characteristics such as name, age, or contact.
-   **Generalization**: Generalization defines the relationship of a subset between occurrences of two or more objects by using “is a” relations. For example, an employer is a generalization of managers.

Why not try our 30-day free trial?

Fully managed, API-first analytics platform. Get instant access — no installation or credit card required.

[Get started](https://registration.cloud.gooddata.com/register)

## Examples of Semantic Data Models

Here are a few examples of SDMs that show different objects and relationships between them. These objects are created by aggregating them into small groups according to their properties.

Each object is somehow related to another one. Let's take a look at the object Person and its relationships. Employee, Applicant, and Customer are generalized into one object called Person. The object Person is related to the object's Project and Task. A Person owns various projects and a specific task relates to different projects.

This example can easily assign relations between two objects as semantic data. Relationships belong to semantic data only when they are named. In our case, the relationships include Executes, Owns, Isa, and WorksAt.

![Points represent objects such as Person, Project, and Task. Lines connect the points, representing relationships, with labels such as Owns or Executes.](https://www.gooddata.com/img/blog/_2000xauto/semantic-data-model-example.png "SDMs define relationships between objects.")

SDMs define relationships between objects.

_Image credit: [Wikiversity](https://en.wikiversity.org/wiki/File:Semantic_model_example_1.png)_

This second example visualizes the relationship between real-world objects in the music industry. Between each object are defined relationships and the direction of object dependence.

![Blocks representing objects such as Artist, Album, and Genre. Lines connect the blocks, representing relationships, with labels such as Records On or Has A.](https://www.gooddata.com/img/blog/_2000xauto/study-image.png "SDMs can illustrate directions of object dependence.")

SDMs can illustrate directions of object dependence.

_Image credit: [Study](https://study.com/academy/lesson/semantic-data-model-definition-example.html)_

There are many possibilities for how SDMs can be created. Mainly, they depend on company requirements and employees' experience.

## Reasons to Use Semantic Data Models

The semantic model helps data management manage and oversee the company's overall data, thus increasing decision-making capabilities. There are four primary goals of SDMs:

-   **Data resource planning:** The SDM can be used in the initial stages of project planning to provide the necessary data resources.
-   **Shareable database creation:** The SDM can be utilized as a data view independent of the application and then transformed into a physical database.
-   **Vendor software evaluation:** The SDM helps detect and identify inconsistencies between a vendor system and its infrastructure and business operations.
-   **Extant database integration:** The SDM supports the creation and generation of conceptual schema (model) to help regulate transaction processing in a distributed database system with the right technology.

## Advantages of SDMs

-   Reveals relationships between instances and makes them easier to understand
-   Supports [data visualization](https://www.gooddata.com/blog/what-is-data-visualization/) to make data reporting clearer
-   Supports application development
-   Does not require technical knowledge about data models
-   Finds elements in objective reality, which are essential
-   Reveals the main characteristics of each component
-   Helps describe the reality of specific processes before setting them up in the organizational structure

## Disadvantages of SDMs

-   Uses graph data modeling technique, which is not widely spread among users
-   Requires more practice and experience to create them

## Semantic Data Models in GoodData

GoodData offers SDMs to end users through the advantages of visualization. This tool provides reusable abstractions which are easier to use than complex SQL queries. With GoodData, you can design your dashboard by using metrics and insights. Every change in the data model is automatically mirrored in the semantic model in GoodData, and your users' searches are unaffected.

Using GoodData, you can create a single metric, which would later be sliceable and usable in all areas and visualizations defined in your SDM. With shared definitions of metrics and relationships, you can easily maintain consistency in your SDM. GoodData’s Analytical Designer tool creates basic SQL queries for you by the drag and drop method related to how your conceptual data view is designed.

![Screenshot of GoodData’s Analytical Designer tool. Sales chart depicting order amounts of various product categories by region.](https://www.gooddata.com/img/blog/_2000xauto/semantic-model-screenshot-as-an-examples-in-the-last-part-.png "Single metrics in GoodData are sliceable and usable in all visualizations defined in your SDM.")

Single metrics in GoodData are sliceable and usable in all visualizations defined in your SDM.

Learn more about semantic models in GoodData in our blog post on how to [deliver efficient data consumption with a semantic model](https://www.gooddata.com/blog/deliver-efficient-data-consumption-semantic-model/).

## Analyze Your Data With GoodData

If you are interested in GoodData.CN, please [contact us](https://www.gooddata.com/contact/). Alternatively, sign up for a trial version of GoodData Cloud: [https://www.gooddata.com/trial/](https://www.gooddata.com/trial/)

Why not try our 30-day free trial?

Fully managed, API-first analytics platform. Get instant access — no installation or credit card required.

[Get started](https://registration.cloud.gooddata.com/register)