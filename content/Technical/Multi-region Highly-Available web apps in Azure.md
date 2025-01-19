#Azure #Technology #HA_DR 

## **Background**

Performance, Security, Availability & Recoverability, Efficiency & Operations are the primary concerns of a good software architecture. As you already know, if Azure is your choice, performance is not an issue and Azure will serve you at any scale. My primary concern of this post is Availability & Recoverability. And also, I will cover some basics of security as well.  
If you are a solution architect, your customers might have asked these questions from you. How do you recover your application after a disaster? What is the SLA of your application? How much time does it take to bring the application online after a disaster? How much data will lose?. A good disaster recovery plan will answer all those questions.

Why high availability is so important for your application? Just imagine that you are running a big e-commerce site which accessing by thousands of users per day and your application goes down for a few hours. As a result, it will cost you a lot of money. Not only that you will lose thousands of customers while making a bad reputation to your business. Therefore, you should able to bring your application online ASAP. In another word, you should keep the RTO (**Recovery Time Objective**) of your application as minimum as possible. On the other hand, after the disaster, you bring your application online quickly. However, you notice that you have lost data for the last ten minutes. For some business scenarios, that is ok and your customer will accept that. But some customers are not accepting any data losses. Think about a banking system and losing all the transactions of the last ten minutes. That will cost your customer a lot of money, sometimes millions. Therefore, it is very important to recover your system to the exact point where it was before when the disaster happens. In another word, you should maintain the RPO (**Recovery Point Objective**) to a minimum value. You must plan both RPO and RTO in your business continuity plan and you should have an agreement with your client.

That is a brief explanation of the importance of availability and recoverability. Let's get into the business. In this post, I mainly focus on the resiliency of your web applications from an Azure region failure. Even though you chose Azure as your cloud service provider, you cannot rely 100% upon Azure infrastructure. You should plan your business continuity and disaster recovery.

### **The Problem**

I am taking a very simple web application deployed into Azure App services and a small SQL database deployed into Azure SQL database.

![](https://miro.medium.com/max/1266/1*tcSMEqG8so45Jptm_Jk3Wg.jpeg)

Single region app deployment

In the Above architecture, you can get 99.95% high availability for app service, if your app service plan running under standard or premium tier. SLA for the SQL server depends on the version or tier. You can read more about SLAs for app service and SQL database on following links.

[**Azure App Service SLA**](https://azure.microsoft.com/en-us/support/legal/sla/app-service/v1_4/)**.** [**Azure SQL database SLA**](https://azure.microsoft.com/en-us/support/legal/sla/sql-database/v1_4/)

May be 99.95 SLA is fair enough for your business. However, what would happen if the whole Azure region goes down for a few hours or days. What would happen if all of your storage files including your database backups are corrupted after a catastrophic disaster and Azure team cannot restore your database or app? Your application will become out of service and sometimes you will not able to recover it to the previous status where it was before the disaster happens. To overcome these problems you can take following actions

### **The Solution**

1.  Setting up geo-replication for your Azure SQL database. This will replicate your databases to databases located in different regions (one or more). Note that the replication process happens asynchronously in the background. Therefore this will not affect to the performance of your application. However, it does take a few seconds to update your database changes to the secondary databases after you commit your transaction to the primary database.
2.  Deploy your application into one or more secondary regions and load-balance your HTTP traffics to those regions based on availability. If your application up and running in the primary region, traffic goes to the primary region. If your primary region not available, traffic goes to the secondary regions. You can use the priority routing method for this. There are few azure load balancers which provide priority load balancing options. [**Azure Traffic Manager**](https://docs.microsoft.com/en-us/azure/traffic-manager/)**,** [**Azure Application Gateway**](https://docs.microsoft.com/en-us/azure/application-gateway/), and [A**zure Front Door**](https://docs.microsoft.com/en-us/azure/frontdoor/). In addition to the priority routing, these load balancers provide different routing methods such as path-based routing, weighted routing, Performance-based routing…etc. You can use these methods to improve the performance of your application.
3.  Use geo-replication for your Azure storage. You can set up the Read Access Geo Redundant Storage (RA-GRS) option for your storage account. This will keep 3 extra copies of your data in another region

Let’s see how to improve the above architecture to increase the high availability and business continuity of your services in order to serve your customers even in an event of Azure region outage.

![](https://miro.medium.com/max/1400/1*g_jlUoiIvdSewEgpBEvajg.jpeg)

Multi-Region app deployment

## **Azure SQL Failover Groups**

In this architecture, I have chosen Southeast Asia Azure region as the primary region since that is the Azure region which gives me the lowest latency. But based on your geolocation your one may be different. You can test latency and many other important statistics of Azure from this [**link.**](https://www.azurespeed.com/Azure/Latency) I have chosen the East Asia Azure region as the secondary region since that is the paired region for Southeast Asia. You can read more about Azure Paired region and the importance of it from this [**link**](https://docs.microsoft.com/en-us/azure/best-practices-availability-paired-regions).

To improve the high availability, A SQL Server failover group has created for the two SQL servers running on those two regions. Azure SQL failover group makes sure that your database up and running all the time even though the primary database becomes unavailable due to an outage of the primary region. When your database of the primary region running without an issue, the primary region’s database works in read-write mode and your secondary region’s database works in read-only mode. All the database updates that you make to the primary database will replicate to the secondary region’s database asynchronously. However, If your primary region’s(Southeast Asia) database becomes unavailable, failover will trigger and the database of the secondary region(East Asia) will become the primary database and will work in read-write mode. When the failed region is restored and back online, the database in East Asia is immediately synchronized with the database in Southeast Asia region, and the read-only listener is switched back to the secondary database in East Asia. During synchronization performance of the primary could be slightly impacted depending on the amount of data that needs to be synchronized. To achieve this, no changes are required in your application source code.

## **Azure Front Door**

That is the database side. The next question is how do we guarantee the high availability of the application? The answer is, we have to deploy a copy of our application into the secondary region and load balance incoming HTTP traffic among those two regions based on the availability. We can choose any load balancer which provides priority routing option. We can use Azure Front Door as a layer 7 load balancer which provides many routing options including priority routing. In addition to priority routing, Azure Front Door provides a rich set of features including, Web Application Firewall, SSL offloading, caching, custom domains….etc. You can read more about AFD and its feature from the [**official documentation**](https://docs.microsoft.com/en-us/azure/frontdoor/). Azure Front Door comes with Azure Application Gateway Web Application Firewall. Therefore, you can protect your application from common web application vulnerabilities defined in [**OWASP**](https://owasp.org/). In this architecture, all the web traffic goes to the application hosted in the highest priority region(Southeast Asia). If the primary region becomes unavailable, traffic moves to the application with the second-highest priority. In general, this type of high availability setup is called **Active-Passive hot standby.** You can read more about this architecture from this [**link**](https://docs.microsoft.com/en-us/azure/architecture/reference-architectures/app-service-web-app/multi-region)**.**

## **Implementation**

Let's implement the above scenario in Azre. I have created a very simple .Net Core Web API sample. You can find the sample source code in this github [**repository**](https://github.com/ajithramawickrama/simplecruddotnetcore.git)

### **Creating Resource Groups**

In this scenario, we are creating azure resources in two different Azure regions. Therefore, it is better to create two resource groups as a best practice.

1.  Log in to the Azure portal
2.  Create a Resource Group for the primary region resources by giving a convenient name for you. I provide “primary-site” as the name. And I select Southeast Asia as the primary region since that is the azure region giving me the lowest latency

![](https://miro.medium.com/max/1400/1*T4RKT7YZ7KxnoRsgtZy6Tg.jpeg)

Creating the Primary Region Resource Group

3\. Create another Resource Group for the secondary region. I provide “Secondary-Region” as the name and select East Asia as the region due to East Asia is the paired region for Southeast Asia

![](https://miro.medium.com/max/1400/1*YylRevIzhCoEp2RY0A4ZQQ.jpeg)

Creating the secondary Region Resource Group

### **Creating the Primary Database**

If you do not have an existing Azure SQL database, create a one with following steps

1.  In Azure portal’s left menu, click on create a resource button. Select Database and then SQL database.
2.  Select your subscription and the resource group. In this case, my resource group is “primary-region”
3.  Provide a name for the database. I choose “primary-database” as the name
4.  Select a SQL Server if you have a one. Otherwise, create a new one
5.  If you create a new server, give a globally unique name as the name of the server
6.  Provide an admin user name and a password
7.  Provide the primary region as the region selection. In this case, my primary region in Southeast Asia
8.  Change the size in order to reduce the cost. I select 10 DTU from the standard tier
9.  Leave other settings to default values and create the database

![](https://miro.medium.com/max/624/1*3ygvskk0AFJsgDTWOskL_g.jpeg)

![](https://miro.medium.com/max/1400/1*hqytRlPdVaDcZWTDlPiuFQ.jpeg)

This will create an empty database in your primary region. We will create some sample data on this database later in this post.

10\. After creating the database add your IP address to the firewall settings of your SQL Server. Otherwise, It will not allow accessing this database from your local network. To do so, go to the SQL server and select the firewall and virtual network section and click on “Add client IP” button. Save your changes.

![](https://miro.medium.com/max/1400/1*2Z_gWXRjuLo2zX0L-_8crQ.jpeg)

### **Clone the sample source code**

1.  Clone the sample Web API source code from this [repo](https://github.com/ajithramawickrama/simplecruddotnetcore.git). If you have your own solution you can use that.
2.  Open the solution in Visual studio.
3.  Open the appsettings.json and change the connection string to your primary database which you have already created. You can copy your connection string from the database’s overview section of the Azure portal.
4.  Restore all the nuget packages.
5.  Open Visual Studio package manager console and enter the following commands.

add-migration {name\_of\_the\_migration}

update-database

This will generate tables and sample records in the SQL database of your primary region.

## **Setting up Azure SQL Failover Group**

We just created the primary database server, database, and some sample data. Now it is time to setup the failover group for our primary server.

1.  In Azure portal, navigate to the SQL server created in your primary region.
2.  Select the Failover Groups and click on Add group button.

![](https://miro.medium.com/max/1400/1*TnjATaGAJANUCHP1d11otw.jpeg)

3\. Provide a globally unique name for the failover group name.

4\. Create a secondary server in your secondary region by clicking on the Secondary Region

5\. Set Automatic for Read/Write failover policy. Giving this option, Azure will automatically start the failover

6\. Select 1 Hour for Read/Write grace period. Using this you can control how long the system waits before initiating the failover that is likely to result data loss.

7\. Select the databases that you need to add to the failover group

8\. Click on the Create button to create the failover group

![](https://miro.medium.com/max/1400/1*LVsrAZ7mPbVp8DhuSFMtYQ.jpeg)

This will synchronize all the data to the secondary region database. The time takes to create the failover group depends on the sizes of the database in the primary region.

9\. Go the failover group after creating it

![](https://miro.medium.com/max/1400/1*Y7SSjFUQ2ziUHb-cDsjzcQ.jpeg)

You can see there are two endpoints:

**Read/Write listener endpoint**\- This endpoint always connects your application to the primary database.

**Read only listener endpoint-**This will connect your application to the secondary database which is read-only. Using this option you can forward your read-only workload to the secondary database and can improve the performance of your application. However, it is recommended to use **ApplicationIntent=ReadOnly**; option in your read-only connection string.

Make sure that you have a common login for both database servers in order to access the failover group via your application.

1.  Create a server login by executing following command in maser database

CREATE LOGIN \[your\_username\] WITH PASSWORD = \[your\_password\]

2\. Create database user by executing following commands in your database

CREATE USER \[your\_username\] FROM LOGIN \[login\_name\] WITH DEFAULT\_SCHEMA=dbo;

Change the connection string of your application as follows

“Server={failover\_group\_name}.database.windows.net;Initial Catalog={database\_name};Persist Security Info=False;User ID={user\_id};Password={password};MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;”

Now we are almost done in the database side except one thing. To make the database accessible from our application, we have to add outbound IPs of our app services as trusted IPs into the firewall settings of both of our SQL servers. To make this easy you can change “Allow Azure services and resources to access this server” to yes in your database firewall settings. However, keep in mind that this is not recommended at all for a production environment.

![](https://miro.medium.com/max/1400/1*SjTSrvJHhMtecSe_IOSyXg.png)

## **Creating web apps in Azure App Services**

Firstly, will create and deploy the app to the primary region

1.  In Azure portal’s left menu, click on create a resource button. Select web App from the Web section.
2.  Select your Azure subscription and the resource group. In this case, my resource group is “primary-region”.
3.  Provide a globally unique name as the name of the application.
4.  Select the .Net Core 3.1 as the runtime stack. If you have your own application, select the runtime stack according to your application. May be Java, NodeJS, Python, PHP …..etc. Azure app services support all these languages.
5.  Since my sample developed with .Net Core 3.1, the application runs in Linux as well. Therefore, I select Linux as the operating system. Linux app services are cheaper than Windows app services. But, some features are limited in Linux app services. You can also use a Windows app service plan.
6.  Select your primary region in the Region selection. In this case, my primary region is Southeast Asia
7.  In the app service plan section, create an app service plan, if you do not have an existing one. If you are creating a new one, B1 SKU would be sufficient enough for this demo
8.  Click on Review + Create and click on Create button again

![](https://miro.medium.com/max/1400/1*sWl3f-L1P0U9sAszV-Nckg.jpeg)

Creating a web app in the primary region

![](https://miro.medium.com/max/1400/1*sPdYRySoAWedAtKzRA1vtA.jpeg)

9\. Using the same way, create a web app in the secondary region as well.

![](https://miro.medium.com/max/1400/1*1L0KqrU_F0K7AnOkz4Kwhg.jpeg)

Creating a web app in the secondary region

## **Deploying web apps to Azure App Service**

In this demo, I deploy the web app to Azure App service directly from the Visual Studio

1\. Open the sample solution in visual studio.

2\. Before you publish the solution, change the AppRegion value of the appsettings.json, located in the root folder of the solution. This will help you to identify the web application that responds to your request.

![](https://miro.medium.com/max/1400/1*dhJoMUJrjPp9gS3Ay-hFVQ.png)

3\. Right-click on the SimpleCrud Web API project and select the publish option. This will open the web application deployment window.

4\. Select Create New Profile or Start Option.

5\. Select App Service Linux Option and click on select existing

![](https://miro.medium.com/max/1400/1*xAf0dyamXdq3gmACafuO1w.png)

6\. Select your Azure subscription and the resource group. Then your app service under the resource group.

![](https://miro.medium.com/max/1400/1*VNinBrJFRthSAtjf2qTAUA.png)

7\. Click the OK button.

![](https://miro.medium.com/max/1374/1*ciA9AkmE7c1wZnestDD1-A.png)

8\. Click on the publish button. This will deploy the application to your Azure app service located in the primary region.

9\. Do the same thing for the secondary region app service as well. Before you publish the application into the secondary region, make sure that you have changed the AppRegion property of the appsettings.json to “Secondary”.

### **Check your Work**

Now we have two web API apps deployed into two azure regions(Southeast Asia and East Asia).

ha-test-primary-1990.azurewebsites.net — Primary Site in Southeast Asia

ha-test-secondary-1990.azurewebsites.net — Secondary Site in East Asia

If you are using the same sample API provided by me, Check whether both of your APIs are up and running and connected to the database.

[https://{your-web-app-url}/api/employee](https://%7Byour-web-app-url%7D/api/employee). If you get a list of employees from both of your sites, Congratulations! you have successfully deployed and configured your resources.

Now we have created and published our sample application into two Azure regions. And also, our database running in two Azure regions to make sure the high availability in the case of Azure region outage.

That is the end of part one of this post. I will meet you in part 2 to demonstrate how to configure Azure Front Door and Azure Web Application Firewall in order to provide high availability and security for our application.

## **References**

[https://docs.microsoft.com/en-us/azure/azure-sql/database/designing-cloud-solutions-for-disaster-recovery](https://docs.microsoft.com/en-us/azure/azure-sql/database/designing-cloud-solutions-for-disaster-recovery)

[https://docs.microsoft.com/en-us/azure/azure-sql/database/business-continuity-high-availability-disaster-recover-hadr-overview](https://docs.microsoft.com/en-us/azure/azure-sql/database/business-continuity-high-availability-disaster-recover-hadr-overview)

[https://docs.microsoft.com/en-us/azure/architecture/resiliency/recovery-loss-azure-region#database](https://docs.microsoft.com/en-us/azure/architecture/resiliency/recovery-loss-azure-region#database)