#iPaaS #Technology 
In the modern business world, it’s all about automation. It starts with such simple tasks as how to [send out automated emails](https://www.rightinbox.com/blog/automated-email-responses-examples) and goes way beyond automatic exchange of data between enterprise systems of record or systems of engagements. When it comes to complex automated data exchange scenarios, there are various tools that IT typically uses to enable this: ESBs, API management systems and B2B gateways, to name just a few. There is, however, a tool that promises to combine the advantages offered by all these – Integration platform as a Service, or simply put, iPaaS.

Gartner introduced the term iPaaS in 2011, [referring to](http://www.gartner.com/it-glossary/information-platform-as-a-service-ipaas) _“a suite of cloud services enabling development, execution and governance of integration flows connecting any combination of on premises and cloud-based processes, services, applications and data within individual or across multiple organizations”_. Since then iPaaS has been diligently serving its main purpose, which has been exactly connecting cloud-to-cloud and cloud-to-on-premise applications. One can call these the most common use cases for an integration platform as a service.

There are, however, several other ways of implementing an iPaaS that are currently far less common, yet are promising and worth exploring. They have something to do with relatively new phenomena in the world of cloud and technology such as software industrialisation, microservices and IoT.

Here’s a quick overview that might help you make a faster decision how to tackle these phenomena next time you deal with them.

## 1\. Embedding iPaaS functionality into an application

New SaaS applications are built practically every day. There might be some unique solutions among them, but most times, they are about the same: create analytics for social media activity, send out automated emails and newsletters, manage customers contacts, etc. This is especially true for horizontal markets, but very soon will be so for vertical markets as well since these are, too, [actively explored by SaaS providers](http://www.nvp.com/blog/the-rise-of-vertical-specific-saas-vendors/).

So, with functionality and innovation set aside for a moment (as these can be relatively easily replicated), the real differentiation factor for SaaS applications is how easily they can provide connection to other systems on the market. By this I mean not just their overall ability to integrate with other applications, which by now should be a default feature, but whether they can deliver these integrations right in their own user interface offering a nearly perfect user experience.

The main challenge for SaaS ISVs, though, lies in the proper infrastructure for integrations. An application typically works on the request-response basis, which is a synchronous process. Most of the integration processes are, however, asynchronious, and this requires a different type of infrastructure. Debugging and supporting integration processes can also pose a serious issue.

This is where an iPaaS can come into play. Provided it has an integration management API, SaaS ISVs can embed an integration platform as a service right into their own application. The only thing their users would have to do is to click a button to activate the integration they need — and that is without leaving the application’s dashboard. At the same time, a developer and integration administrator backend delivered with an iPaaS will allow ISVs to easily design, run and monitor integration processes.

![Embed iPaaS functionality into an app](https://15f76u3xxy662wdat72j3l53-wpengine.netdna-ssl.com/wp-content/uploads/2016/02/Embed-iPaaS-functionality-into-an-app-300x175.jpg)

A rough example of how integrations embedded into an application can look like

## 2\. Building integration portals for repetitive integration scenarios

This way of implementing an iPaaS can be of a special value particularly for IT departments and system integrators. One of the most persistent challenges that both share is the inability to effectively offload the workload related to integration projects when it comes to repetitive integration scenarios. Both have to address even the smallest and most common integration project each time separately and as if it were a new one, which is not least of all due to the inconsistent infrastructures.

Implementing an integration platform as a service will ensure that IT departments and system integrators have a uniform infrastructure for all integrations. This way they have to build integration components only once. Further step would be to offer these components in the form of self-service integration portals to their end users. Surely, this involves investing some time and efforts into creating components and building an easy-to-use and intuitive user interface. However, in the long run, this is a one-time investment that would ensure a considerable decrease of efforts spent on repetitive integration scenarios in the future.

![Self-service integration portals](https://15f76u3xxy662wdat72j3l53-wpengine.netdna-ssl.com/wp-content/uploads/2016/02/Self-service-integration-portals_1.jpg)

An example for an ACME Corporation self-service integration portal

By creating self-service integration portals, both enterprise IT departments and system integrators will also, practically as a bonus, be able to solve a few other challenges. The former can introduce the so called citizen integration within their organisations (more on citizen integrators in this [Massimo Pezzini’s article on LinkedIn](https://www.linkedin.com/pulse/market-guide-citizen-integrator-tools-massimo-pezzini)), while the latter can address new markets and thus, expand their revenue streams (more on this in my previous article [What Implementation Partners and System Integrators Can Learn from Slack and Hipchat](https://medium.com/@O_Annenko/what-implementation-partners-and-system-integrators-can-learn-from-slack-and-hipchat-27c09712ca50#.2s65t4pm0)).

For the sake of a better user experience it is advisable to implement an iPaaS that has a white-labelling option. This way both corporate IT and system integrators can deliver the self-service integration portals under their own corporate brand.

[Check out elastic.io iPaaS now](https://eio.guru/udnle)

## 3\. Enabling communication between microservices

Microservices is one of the modern buzzwords in the tech world, and they certainly have earned the hype around them. After all, they allow to avoid building monolithic applications, but instead create them as a suite of small services. This is considerably more lightweight and much more manageable in case some part of an application malfunctions. It is crucial, though, among other things to ensure a really stable communication between the microservices.

There are different ways how microservices can “talk” to each other: These can be synchronous communication mechanisms such as HTTP-based REST or asynchronous communication mechanisms such as AMQP using e.g. RabbitMQ.

Yet another way can be achieved by connecting microservices via an iPaaS straight away, no matter whether you are building an application with microservices from scratch or want to split your existing monolithic application into them. An integration platform will be able to handle a lot of communication infrastructure, for example via Webhooks, and provide developers with a solid fault reporting system. Such approach is especially beneficial to businesses that don’t have time and/or resources to build an extra infrastructure which would hold microservices together.

Those who seek for a practical example of this approach can check out the article [“How This Startup Connected Microservices in 15 Minutes”](https://www.elastic.io/how-this-startup-connected-microservices-in-15-minutes-via-elastic-io/).

As microservices as a phenomenon are very young, I believe that very soon, connecting them via an iPaaS will become rather a standard approach to handling microservices architecture.

## 4\. Managing APIs for the Internet of Things (IoT)

IoT — another modern buzzword, and where would we be without mentioning it within this article. While the term “IoT” [was allegedly coined in 1999](http://www.pocket-lint.com/news/126559-internet-of-things-explained-what-is-it-and-can-it-really-change-the-world), it is only recently when it was brought up in connection with the term iPaaS.

The main reason behind this is that there is an increasing need to connect IoT services to each other and to applications for a variety of reasons: in commercial use cases, in industrial use cases, for better user experience, and so on. The data collected by IoT services and devices needs to be evaluated and analyzed for further usage, subsequently aggregated and recycled.

It is a standard practice that IoT services can be accessed via their APIs, and in this respect, a solid API management [is absolutely crucial](http://www.wired.com/insights/2013/07/without-api-management-the-internet-of-things-is-just-a-big-thing/) to ensure proper maintenance and high levels of functionality and security. Although an iPaaS is not defined by its ability to connect and manage APIs (see the Gartner’s definition above), this is practically its default feature: Most cloud applications are accessed through their REST or SOAP APIs, so in order to connect them, an iPaaS simply must handle APIs.

In this light, an iPaaS offers an ideal basis for ensuring the connectivity for the Internet of Things. Besides, apart from offering a uniform infrastructure and ready-to-use tools that are necessary for a solid integration via APIs, it should be also expected to deliver a proper credential management and granular monitoring & logging systems. This ensures a well-organized and controlled maintenance of the communication between IoT services and devices, and other applications.

As it is with microservices, I think we will be seeing an increased implementation of an integration platform as a service in the context of IoT. Many iPaaS providers already advertise with this buzzword, so the demand has obviously finally “arrived”.

### Wonder whether the elastic.io iPaaS is a match for your use case?

___

[Check out elastic.io iPaaS now](https://eio.guru/udnle)