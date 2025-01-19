---
aliases: (Oracle Integration Cloud)
---
#Technology #definition 
# Oracle Integration Cloud (OIC)
## Connectivity Agent
- [[OIC Connectivity Agents]]
## What to Use
- Connectors (app-based, protocol-based)
- [[ Integration Patterns]] (aka Integration Styles)
	- [[App Driven Orchestration]]
	- [[Scheduled Orchestration]]
	- [[File Transfer]]
	- [[Basic Routing]]
	- [[Publish to OIC]]
	- [[Subscribe to OIC]]
- Data Mapping
## What not to Use (Now)
- Process Automation
- Web Forms
- Visual Builder to build Web Apps
## Uncertain Use
* FTP Connectors
	* Unsure if MFT is the same / can be substituted
		* *FTP Connectors do not leverage MFT*
		* Still need to resolve the SOA MFT vs. FTP Connectors issue
- [[AQ]]
- Business Events System
- HA DR aspects
	- Based on WLS and Oracle DB which have HA options
	- Still need to architect correctly to leverage HA DR
	- Not sure about OIC configs re connectors
		- How portable are they?
		- Can they be moved to another cloud instance? Do the configs need to be changed / tracked / converted?
	- Should we use a Load Balancer?
	- Should we use an Event Broker?
	- How are we monitoring components for availability etc.?
	- What is a DBFS mount, in the context of WLS and Oracle DB?
	- cf. OCIDI Data Integration; Golden Gate
## What's Missing
- Data Streaming
## Relies Upon
- WSDL
- JSON
- XSD

# Export / Transfer Settings
- [Import and Export Integrations (oracle.com)](https://docs.oracle.com/en/cloud/paas/integration-cloud/integrations-user/import-and-export-integrations.html#GUID-A2E33343-291E-4F82-92F2-B1309886FDC1)
- [How to use the new Import/Export feature in Oracle Integration](https://blogs.oracle.com/integration/post/how-to-use-the-new-importexport-feature-in-oracle-integration)
- [[OIC Import Export Feature]]

# Recipes
- [Oracle Integration Generation 2 - Recipes](https://docs.oracle.com/en/cloud/paas/integration-cloud/find-recipes.html)
# Error Handling
- Global Fault Handler
	- [oicbasics: Basic Error Handling in OIC | Oracle Integration Cloud](https://www.oicbasics.com/2020/05/basic-error-handling-in-oic.html)
# Exception Handling
- A Summary Article
	- [OIC – Exception Handling and Notifications – A Summary – Note to self](https://notetoself.dev/2021/07/15/oic-exception-handling-and-notifications-a-summary/)
	- 