---
tags:
  - Integration
  - definition
  - API
  - REST
  - SOAP
  - GraphQL
---
Understanding API types is second nature to a developer who is often implementing [API connectors](https://cyclr.com/api-connectors) left, right and centre. But what if you are the person who is interpreting or the user of the data from those APIs? It is useful to have an understanding of the API types that are requesting and responding to the data you are using. 

To kick off an API (application programming interface) is a software intermediary that allows applications to understand and communicate with each other. Whether you work with them on a day-to-day basis or just learn the ropes they are a vital part of automation and integration. 

So with that said it is important to know your API types, REST, SOAP and GraphQL. 

## **Different Types of APIs**

### **REST API**

A REST or REpresentation State Transfer is a software architectural style that developers apply to web APIs. It can be used to communicate over the internet to make integrations simple and scalable. RESTs architectural style permits a requesting system to get robust access and redefine representations of web-based resources. It does so by deploying a predefined set of stateless protocols and standard operations.

There are some key terms that will pop up when interacting with a REST API.

-   The client is the person using the API and making requests in order to retrieve data or change an element within an application. 
-   The resource is any piece of information or data that the API provides to the client. 
-   The server is used by the app which receives the client request and contains the resource. 

When a client makes a request usually an HTTP request there are four basic types:

-   Get: retrieve a resource
-   Post: Create a new resource
-   Put: Update an existing resource
-   Delete: remove a resource 

For example, a REST API works in a similar way as you requesting or searching for something on Google. In response, you get a list of results back from the service you’re requesting from. APIs are the backbone of the web and mobile applications.

Other examples of REST APIs include when information needs to be read and written such as a social media profile, submitting data online, ordering information, and reading information from a server/database.

A REST API is ideal for use with importing or exporting content, like on a blog or social media profile.

They are commonly used when creating and managing credentials, adding a new customer or updating an employee to a CRM for instance. 

![REST API diagram](https://cyclr.com/wp-content/uploads/2021/07/REST-API-1024x1024.png.webp)

### **SOAP API**

SOAP or Simple Object Access Protocol is a message specification for exchanging information between systems and applications. It permits processes using different operating systems via HTTP, SOAP APIs are designed to create, recover, update and delete records.

[SoapUI](https://www.soapui.org/learn/api/soap-vs-rest-api/) states the difference between SOAP and REST API pretty well. “SOAP is like an envelope while REST is just a postcard.” A postcard is faster and cheaper, whereas it takes a few extra steps to access an envelope. Using SOAP when designing APIs focuses on the message, whereas using REST when designing APIs focuses on defining them as resources.

Many have referred to SOAP as being like the national postal service. It provides a reliable and trusted way to send and receive messages between systems. Other examples of when a SOAP API would be used include; financial services, e-commerce payments and telecommunications. These tend to be within an enterprise environment.

A SOAP [API is ideal for use with formal contracts](https://cyclr.com/blog/api-security-best-practices "API Security Best Practices") which are mostly on a large scale and affect a large proportion of customers.

Billing, for instance, many enterprise businesses connect systems to identify customer consumption to generate billing information. 

![SOAP API Diagram](https://cyclr.com/wp-content/uploads/2021/07/SOAP-API-1024x1024.png.webp)

### **GraphQL** 

GraphQL is a query language that lets developers construct requests that pull data from multiple data sources in a single API call. It prioritises giving clients exactly what they request from a GraphQL server and no more.

A GraphQL has three primary functions:

-   Query to read data
-   Mutation to write data
-   Subscription to observe events and automatically send data

GraphQL also contains a schema enabling the client to extract the exact data they need. 

[Po](https://www.postman.com/graphql/)[s](https://www.postman.com/graphql/)[tman](https://www.postman.com/graphql/) gives a great example of what GraphQL is capable of doing in comparison to REST APIs. So for instance, “if you wanted to use the Spotify REST API to get a list of all of the titles of all of the tracks of all of the albums by a particular artist, you would need to make three queries. You would need one query to find the artist ID, another to find all of the albums, and another to find all of the tracks on each album. If you were using the Spotify GraphQL API, you could access all of that data with a single query.”

There are several leading organisations that use GraphQL such as Facebook, Pinterest, GitHub and PayPal.

A GraphQL is ideal for use with apps for devices such as mobile phones or IoT devices, where speed and bandwidth are essential.

GraphQL is used where data is nested and needs to be fetched in a single call, like our diagram example above, a social networking platform would use this methodology where posts are required to be fetched, as well as comments, likes, and shares. 

![GraphQL API diagram](https://cyclr.com/wp-content/uploads/2021/07/GraphQL-1024x1024.png.webp)

#### **For more information about building integration first APIs download our report.**

Find out more information on the report’s dedicated page.

## **Which is better, GraphQL, SOAP or REST API?**

### **Pros and Cons of REST APIs**

#### **REST Advantages**

1.  Easy to integrate with due to small learning curve
2.  Use of HTTP so there are no expensive tools required to interact with the web service
3.  Scalable, efficient and fast due to smaller message formats and no extensive processing

#### **REST Disadvantages** 

1.  Lack of security
2.  Inability to maintain state, maintaining state lies on the client which can make the application heavy

### **Pros and Cons of SOAP APIs**

#### **SOAP Advantages**

1.  A dependable way to define and operate APIs across an enterprise at scale, and is the backbone applications and integrations that said enterprise depends upon
2.  Standardised
3.  Pre-built extensibility
4.  Built-in error handling

#### **SOAP Disadvantages** 

1.  SOAP can make it slower to evolve and iterate on APIs
2.  Longer to onboard new developers who aren’t familiar with SOAP’s older methods
3.  SOAP uses XML for all messages

### **Pros and Cons of GraphQL APIs**

#### **GraphQL Advantages**

1.  It is efficient so there is no under or over-fetching
2.  GraphQL has the ability to retrieve many resources in a single request saving time and bandwidth
3.  Allows for precise querying when working with large APIs that return lots of data
4.  Good for complex systems
5.  Fast process

#### **GraphQL Disadvantages**

1.  Lack of built-in caching support
2.  Performance issues depending on the complexity of the query
3.  Due to its complexity, it can take a long time to fully understand

___

> “The choice between REST and GraphQL depends on the specific requirements of a project. 
> 
> In my personal experience, REST is well-suited for applications and scenarios where predefined endpoints make sense. 
> 
> Whereas I feel GraphQL shines in situations where flexibility, efficient data fetching, and reduced over-fetching are crucial, especially in complex and dynamic applications.”
> 
> [Ian Rimmer](https://www.linkedin.com/in/ian-rimmer-89bb052/), Connector Team Lead

[![Ian Rimmer - Connector Team Lead](https://cyclr.com/wp-content/uploads/2019/07/Ian-Rimmer-1024x1024.jpg.webp)](https://www.linkedin.com/in/ian-rimmer-89bb052/)

___

### **What is an API request and response?**

We briefly touched on what requests and responses are for the different API types above, but for further explanation an API request allows you to retrieve data from a data source.

For instance, all of the previously mentioned API types have a client requesting data or information from a server. Data is delivered as a resource or response in the appropriate format depending on the API type that has been used.

![API data request and response flow](https://cyclr.com/wp-content/uploads/2021/07/Request-and-Response.png.webp)

### **The advantages of knowing API Types** 

Again if you are a developer this knowledge of the different API types might be second nature. However, if you aren’t a developer but are receiving data from APIs it can be beneficial to know the different API types. Knowing which type to use, and where, will influence how you interpret the data, know exactly what it is to be used for, how it flows in your integration workflow, and how it informs other data in the workflow. 

For further understanding of the differences between API types, and how they can help you to orchestrate your data. We explain some key [API orchestration](https://cyclr.com/orchestration-layer) components of Cyclr here in [What API Orchestration Tools are Available to Tame your Data?](https://cyclr.com/blog/api-orchestration-tools-to-tame-your-data)

#### **We are hosting a range of webinars discussing embedded iPaaS, integration building and more.**

Check out the full list on our dedicated page.