---
title: Getting Hands On With Microsoft Fabric
source: https://mrpaulandrew.com/2023/10/29/getting-hands-on-with-microsoft-fabric/
author:
  - "[[Welcome to the Blog of Paul Andrew]]"
published: 2023-10-29
created: 2024-12-17
description: The Pain Of Creating Production Solutions With Preview Tools Over the last couple of months we've been involved in the design and build of a real-time analytics platform where Microsoft Fabric has been front and center for the delivery. After a lot of debate during the design phase, it was concluded that using Microsoft Azure…
tags:
  - EA
  - EA_Data
  - Data
  - Data_Fabric
  - Microsoft_Fabric
  - Lambda
  - Kappa
  - Data_Platform
---
## The Pain Of Creating Production Solutions With Preview Tools

Over the last couple of months we’ve been involved in the design and build of a real-time analytics platform where Microsoft Fabric has been front and center for the delivery. After a lot of debate during the design phase, it was concluded that using Microsoft Azure to handle the data ingestion from an evolving source API was needed, with Microsoft Fabric supporting all technical capabilities downstream was the best approach.

Logical architecture for context:

![](https://mrpaulandrew.com/wp-content/uploads/2023/10/image.png?w=1024)

---

Despite playing with different parts of the Fabric ecosystem for a long time. Nothing ever prepares you for the challenges and “quirks” faced when building a solution for real. In this post I’ll call out some of the pain points we’ve faced and features of the product still requiring improvement. Excluding some of the obvious gaps in the product like security, that we know to be coming.

---

- Artifacts not supported in Git or as part of the workspace Deployment Pipelines. Maybe obvious. But this means we have no automated way to publish Artifacts between workspaces. No API. Nothing. Deployment Pipelines only offer the ability to promote dashboard content between workspaces, nothing else. Manual change control for now!

![](https://mrpaulandrew.com/wp-content/uploads/2023/10/image-2.png?w=502)

---

- This one has two parts to it. **Firstly**, tables created via a Notebook that aren’t explicitly set to ‘USING DELTA’ will not appear in the SQL endpoint because the default table creation is actually to use TEXT, we could say this is a Spark vs Fabric feature incompatibility. It is documented. But like many you could be forgiven for assuming everything in Fabric is Delta, so it should be implicit in the table create. **Secondly**, attributes in tables created by other experiences (like Event Handler outputs) that auto infer complex data types for things like JSON, setting the data type to ‘Struct’, not supported in the SQL endpoint also just won’t appear and can’t be overwritten to strings. See MS Docs [here](https://learn.microsoft.com/en-us/fabric/data-warehouse/data-types) for supported types.

![](https://mrpaulandrew.com/wp-content/uploads/2023/10/image-3.png?w=817)

---

- SQL endpoints don’t have a local firewall to block external IP addresses. The hostnames are very long and random requiring AAD authentication. But we still need network integration to provide that extra layer of security. Currently feels a little exposed.

---

- Developing KQL code in a dedicated ‘Queryset’ artifact vs the KQL Database directly feels very disconnected. By comparison developing Python in a Notebook for a Lakehouse is a lot more connected/intuitive.

---

- Not having available compute capacity to preview data as part an Event Handler output. “*Unable to submit this request because all the available capacity is currently being used.*” This works fine for the KQL Database output. Just not to the Lake House.

![](https://mrpaulandrew.com/wp-content/uploads/2023/10/image-4.png?w=1024)

---

- Having more than 10 different artifacts or experience panels open at once. Resulting in UI errors.

![](https://mrpaulandrew.com/wp-content/uploads/2023/10/image-5.png?w=763)

---

- Generally navigating around the UI. Everything taking multiple clicks to change windows. The new lineage view is helpful. But compared to developing in a VSCode Workspace with a tidy folder structure for files etc, it leaves a lot to be desired.

---

- In the Event handler input where a custom input for an Event Hub is used. In a “normal” Azure Event Hub the namespace connection string and the Event Hub Name is required. In Fabric this can only be found by checking for the “Entity Path” on the end of the input connection string. Not very obvious. The Event Hub Name is not the name of the Event Handler artifact as you might expect.

![](https://mrpaulandrew.com/wp-content/uploads/2023/10/image-6.png?w=1024)

---

- Pipeline external activities loosing connection string information and requiring it to be re-selected for the pipeline to work correctly. I didn’t manage to screen shot this one. But experienced it intermintantly several times while building artifacts and clicking round. It may just be a UI cache issue between saving/committing.

---

- Having the left menu expanded when dealing with complex naming conventions because not all the text is visable. Meaning you have to guess as well as learn what all the icons are for open artifacts.

---

- Creating Event Handler outputs to KQL databases without being able to provide sample data. To correctly connect and configure the output, data must first be flowing into the input. Not an obvious dependency step when developing a real-time feed.

---

I have no doubt the product teams will address these issues as the things mature. But for now, as a Microsoft MVP I consider it part of my role to hold them accountantble for the software released and where it remains unfinished.

Today 31st October 2023, it is no surprise that Mircrosoft Fabric is not yet finished and not yet suitable for enterprise deliveries. That said, I stand by the design and love the potential the Event Handler artifact offers over comparable Azure Resources.
