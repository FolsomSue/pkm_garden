#EA #Integration #Patterns #Principles #Framework

# Approach
- Principles #strategy 
- [ ] Need to monitor upcoming initiatives to drive priorities for these  (Electric) #Tactical #2022-5-18
- [ ] Remaining BUs #2022-06-15
	- [ ] Develop key questions / questionnaire for use by all EAs / BRMs to drive discovery of upcoming #2-22-05-11
- Integration Scenarios #strategy 
	- Leads to pattern(s) to apply
	- Leads to standard(s) to apply
		- Which leverages technologies / services in place
- Patterns #strategy 
	- Roughly a half-dozen standard ones
	- **Re-use the ones defined via OIC**
- Implementation
	- Consider an Integration Bus to be conceptual
		- Will be realized by pre-existing / replacement [[iPaaS]] aspects
		- ... not looking to build an explicit Integration Bus
# Restrictions
- SOX-related apps may require approved partner connectors rather than  implementing regular integration connections
- Cloud-to-Prem / Prem-to-Cloud file integrations
	- Use IBM Sterling -> going away when on-prem goes
	- Use Oracle MFT
# Integration Patterns
## Considerations
- On-prem
- Cloud-based
- Multi-cloud
- Authentication
	- Leveraging corporate IdAM?
- DR / HA / Data Timeliness
- Align with Oracle's [[OIC Patterns|OIC Patterns]]
## Application Integration
### Patterns
- Bulk
	- File-transfer -based
- Asynchronous
	- Message-based
		- Message Channels
			- Point-to-Point
			- Pub-Sub
		- Message Routers
			- Used by EAI
- Repository
	- Databases, lakes, hubs
- Functional / Remote Procedural
	- RESTful, SOAP, RPC...
	- Webhook + API...
- Event-Driven: [[Event Broker]]+ iPaaS
	- OIC has Advanced Queuing (AQ) for Business Event System
- Streamed 
	- Apache Spark and / or related technologies?
- **Note** OIC integrations are typically activated and running in the background, waiting for messages / triggers
	- Once set up they are not programmatically invoked, but rather use a trigger from an app's activity to actually execute
### [[Integration Principles]]
- Design as if always crossing a network boundary
	- Covers on-prem vs. cloud
	- Covers Corporate vs. OT 
		- trust zones high to low
- << Conventional Principles: >>
	- Buy vs. Build
	- Leverage Data Mapping, transformations, etc. from the iPaaS
- Session
	- Stateful vs. Stateless
- Leverage iPaaS to Implement all patterns
- Authentication
	- Centralized IdAM? -> we leverage Okta for all platform / cross-platform authentication
	- OAuth 2.0, SAML-based API-key authentication
	- Separation of System authentication from User authorization (access)
- Security baked-in
	- Secure protocols
- Leverage Open Standards
- Loosely-coupled
- Leverage iPaaS wherever possible
## Data Integration
### Patterns
### Principles
- Leverages Application Integration Patterns and Principles
- Loosely-coupled
- Leverage Open Standards
- Data Access Mechanism
	- Data Virtualization
	- aka Data Marketplace
- Subject to Data Governance
	- Datasource must be subject to Data Classification
	- Authorization by either Data Classification or Role or both
- Authentication and Authorization
- Data Classification
- Leverage Mapping & Transformation Capabilities
- Data Format
- Data Timeliness
