---
aliases: [Oracle Regions, Availability Domains, Fault Domains]
---

#Technology #definition #Oracle #OIC 
# Synopsis
- Region(s) contains multiple availability domains
	- Canada only has two regions, each with one availability domain
- Availability Domain
	-  = 1 or more data centre within the region
	- Isolated from each other, fault tolerant
	- No shared infrastructure between availability domains
	- High speed network between availability domains
	- Can leverage for HA and DR
	- Each Availability Domain has 3 Fault Domains
- Fault Domain
	- Grouping of hardware and infrastructure within an Availability Domain to provide anti-affinity (logical data centre)
	- 3 per Availability Domain
	- Should deploy server and databases across Fault Domains
- Compartment
	- A collection of related resources
		- Tenancy / Root, plus up to 5 nested below
		- Has a load balancer as part of Compartment Network
	- Compartment Storage can include
		- Block
		- File
		- Object
	- Best practice is to create dedicated compartments when you need to isolate resources
	- **Not sure what to use this for**
# Oracle Regions and Availability Domains
Oracle Cloud Infrastructure is hosted in **regions** and **availability domains**. A region is a localized geographic area, and an availability domain is one or more data centers located within a region. A region is composed of one or more availability domains. Most Oracle Cloud Infrastructure resources are either region-specific, such as a virtual cloud network, or availability domain\-specific, such as a compute instance. Traffic between availability domains and between regions is encrypted. Availability domains are isolated from each other, fault tolerant, and very unlikely to fail simultaneously. Because availability domains do not share infrastructure such as power or cooling, or the internal availability domain network, a failure at one availability domain within a region is unlikely to impact the availability of the others within the same region.

The availability domains within the same region are connected to each other by a low latency, high bandwidth network, which makes it possible for you to provide high-availability connectivity to the internet and on-premises, and to build replicated systems in multiple availability domains for both high-availability and disaster recovery.

Oracle is adding multiple cloud regions around the world to provide local access to cloud resources for our customers. To accomplish this quickly, we’ve chosen to launch regions in new geographies with one availability domain.

As regions require expansion, we have the option to add capacity to existing availability domains, to add additional availability domains to an existing region, or to build a new region. The expansion approach in a particular scenario is based on customer requirements as well as considerations of regional demand patterns and resource availability.

For any region with one availability domain, a second availability domain or region in the same country or geo-political area will be made available within a year to enable further options for disaster recovery that support customer requirements for data residency where they exist.

Regions are independent of other regions and can be separated by vast distances—across countries or even continents. Generally, you would deploy an application in the region where it is most heavily used, because using nearby resources is faster than using distant resources. However, you can also deploy applications in different regions for these reasons:

-   To mitigate the risk of region-wide events such as large weather systems or earthquakes.
-   To meet varying requirements for legal jurisdictions, tax domains, and other business or social criteria.

Regions are grouped into **realms** . Your tenancy exists in a single realm and can access all regions that belong to that realm. You cannot access regions that are not in your realm. Currently, Oracle Cloud Infrastructure has multiple realms. There is one commercial realm. There are multiple realms for Government Cloud: US Government Cloud [FedRAMP authorized](https://docs.oracle.com/en-us/iaas/Content/General/Concepts/govfedramp.htm#Oracle_Cloud_Infrastructure_US_Government_Cloud_with_FedRAMP_Authorization) and [IL5 authorized](https://docs.oracle.com/en-us/iaas/Content/General/Concepts/govfeddod.htm#Oracle_Cloud_Infrastructure_US_Federal_Cloud_with_DISA_Impact_Level_5_Authorization), and [United Kingdom Government Cloud](https://docs.oracle.com/en-us/iaas/Content/General/Concepts/govuksouth.htm#Oracle_Cloud_Infrastructure_United_Kingdom_Government_Cloud).

The following table lists the regions in the Oracle Cloud Infrastructure commercial **realm** :

| Region Name | Region Identifier | Region Location | Region Key | Realm Key | Availability Domains |
| --- | --- | --- | --- | --- | --- |
| Australia East (Sydney) | ap-sydney-1 | Sydney, Australia | SYD | OC1 | 1 |
| Australia Southeast (Melbourne) | ap-melbourne-1 | Melbourne, Australia | MEL | OC1 | 1 |
| Brazil East (Sao Paulo) | sa-saopaulo-1 | Sao Paulo, Brazil | GRU | OC1 | 1 |
| Brazil Southeast (Vinhedo) | sa-vinhedo-1 | Vinhedo, Brazil | VCP | OC1 | 1 |
| Canada Southeast (Montreal) | ca-montreal-1 | Montreal, Canada | YUL | OC1 | 1 |
| Canada Southeast (Toronto) | ca-toronto-1 | Toronto, Canada | YYZ | OC1 | 1 |
| Chile (Santiago) | sa-santiago-1 | Santiago, Chile | SCL | OC1 | 1 |
| France South (Marseille) | eu-marseille-1 | Marseille, France | MRS | OC1 | 1 |
| Germany Central (Frankfurt) | eu-frankfurt-1 | Frankfurt, Germany | FRA | OC1 | 3 |
| India South (Hyderabad) | ap-hyderabad-1 | Hyderabad, India | HYD | OC1 | 1 |
| India West (Mumbai) | ap-mumbai-1 | Mumbai, India | BOM | OC1 | 1 |
| Israel Central (Jerusalem) | il-jerusalem-1 | Jerusalem, Israel | MTZ | OCI | 1 |
| Italy Northwest (Milan) | eu-milan-1 | Milan, Italy | LIN | OC1 | 1 |
| Japan Central (Osaka) | ap-osaka-1 | Osaka, Japan | KIX | OC1 | 1 |
| Japan East (Tokyo) | ap-tokyo-1 | Tokyo, Japan | NRT | OC1 | 1 |
| Netherlands Northwest (Amsterdam) | eu-amsterdam-1 | Amsterdam, Netherlands | AMS | OC1 | 1 |
| Saudi Arabia West (Jeddah) | me-jeddah-1 | Jeddah, Saudi Arabia | JED | OC1 | 1 |
| Singapore (Singapore) | ap-singapore-1 | Singapore,Singapore | SIN | OC1 | 1 |
| South Africa Central (Johannesburg) | af-johannesburg-1 | Johannesburg, South Africa | JNB | OC1 | 1 |
| South Korea Central (Seoul) | ap-seoul-1 | Seoul, South Korea | ICN | OC1 | 1 |
| South Korea North (Chuncheon) | ap-chuncheon-1 | Chuncheon, South Korea | YNY | OC1 | 1 |
| Sweden Central (Stockholm) | eu-stockholm-1 | Stockholm, Sweden | ARN | OC1 | 1 |
| Switzerland North (Zurich) | eu-zurich-1 | Zurich, Switzerland | ZRH | OC1 | 1 |
| UAE Central (Abu Dhabi) | me-abudhabi-1 | Abu Dhabi, UAE | AUH | OC1 | 1 |
| UAE East (Dubai) | me-dubai-1 | Dubai, UAE | DXB | OC1 | 1 |
| UK South (London) | uk-london-1 | London, United Kingdom | LHR | OC1 | 3 |
| UK West (Newport) | uk-cardiff-1 | Newport, United Kingdom | CWL | OC1 | 1 |
| US East (Ashburn) | us-ashburn-1 | Ashburn, VA | IAD | OC1 | 3 |
| US West (Phoenix) | us-phoenix-1 | Phoenix, AZ | PHX | OC1 | 3 |
| US West (San Jose) | us-sanjose-1 | San Jose, CA | SJC | OC1 | 1 |

To subscribe to a region, see [Managing Regions](https://docs.oracle.com/en-us/iaas/Content/Identity/Tasks/managingregions.htm#Managing_Regions).

For a list of regions in the the Oracle Government Cloud realms, see the following topics:

-   [Oracle Cloud Infrastructure US Government Cloud with FedRAMP Authorization](https://docs.oracle.com/en-us/iaas/Content/General/Concepts/govfedramp.htm#Oracle_Cloud_Infrastructure_US_Government_Cloud_with_FedRAMP_Authorization)
-   [Oracle Cloud Infrastructure US Federal Cloud with DISA Impact Level 5 Authorization](https://docs.oracle.com/en-us/iaas/Content/General/Concepts/govfeddod.htm#Oracle_Cloud_Infrastructure_US_Federal_Cloud_with_DISA_Impact_Level_5_Authorization)
-   [Oracle Cloud Infrastructure United Kingdom Government Cloud](https://docs.oracle.com/en-us/iaas/Content/General/Concepts/govuksouth.htm#Oracle_Cloud_Infrastructure_United_Kingdom_Government_Cloud)

**Note**

Your Tenancy's Availability Domain Names

Oracle Cloud Infrastructure randomizes the availability domains by **tenancy**  to help balance capacity in the data centers. For example, the availability domain labeled PHX\-AD-1 for tenancyA may be a different data center than the one labeled PHX\-AD-1 for tenancyB. To keep track of which availability domain corresponds to which data center for each tenancy, Oracle Cloud Infrastructure uses tenancy-specific prefixes for the availability domain names. For example: the availability domains for your tenancy are something like Uocm:PHX\-AD-1, Uocm:PHX\-AD-2, and so on.

To get the specific names of your tenancy's availability domains, use the [ListAvailabilityDomains](https://docs.oracle.com/iaas/api/#/en/identity/latest/AvailabilityDomain/ListAvailabilityDomains) operation, which is available in the IAM API. You can also see the names when you use the Console to [launch an instance](https://docs.oracle.com/en-us/iaas/Content/Compute/Tasks/launchinginstance.htm#Creating_an_Instance) and choose which availability domain to launch the instance in.