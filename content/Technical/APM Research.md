#Technology #definition #APM 
# Definitions
## Gartner's Definition
- Application Performance Monitoring (APM) is **a suite of monitoring software comprising digital experience monitoring (DEM), application discovery, tracing and diagnostics, and purpose-built artificial intelligence for IT operations**. APM strives to detect and diagnose complex application performance problems to maintain an expected level of service by tracking key software application performance metrics using monitoring software and telemetry data.
## Gartner's Overview
- APM and observability tools provide visibility into the digital experience that optimizes user engagement. Use cases now include security, and OpenTelemetry portends a new type of standardization. With many tools available, I&O leaders must identify their critical capabilities.
# Short List (Gartner)
- Based on Leaders' Quadrant from MQ (2021)
	- Dynatrace
	- Datadog
	- New Relic
	- Honeycomb
	- IBM (Instana)
	- ![[APM MQ.png]]
# Capabilities (Gartner)
## Primary
- Observation of an application's complete transactional behaviour
- Automated discovery and mapping of an application and its infrastructure components (including cloud services)
- Monitoring of applications running on mobile (native and browser) and desktop browsers
- Identification and analysis of application performance problems and their impact on business outcomes
- Native integration capabilities with automation and service management tools, as well as native integration with public cloud providers - e.g. AWS, Cloudwatch, Azure Monitoring and Google Cloud Operations
- Analysis of business key performance indicators (KPIs) and user journeys - for example, login to check-out
- The ability to perform interactive interrogation of multiple telemetry types (such as traces, metrics, and logs) to detect "unknown unknowns" -- that is, the ability to identify underlying issues to unexpected events and gaps in telemetry coverage
- Application security functionality delivered via a common agent or framework for APM
## Optional Functionality
- Endpoint monitoring to understand the user experience and its impact on business outcomes
- Support for virtual desktop infrastructure (VDI) monitoring
- Performance testing and integration with load testing tools
## Differentiating Critical Capabilities
- Application debugging and distributed profiling (ADDP)
- Behaviour analysis
- Business analysis
- IT service and infrastructure monitoring
- Root Cause Analysis
- Runtime Application Self-Protection (RASP)
## Use Cases
- Application owner / line of business (LOB)
- DevOps / AppDev
- Digital Experience Monitoring (DEM)
- IT operations
- Security operations
- Site Reliability Engineering (SRE) / platform operations
## Functional Areas
- The Core Layer comprises the basic requirements of functional areas, such as profiling and DEM, that must be available in some form for the solution to be viable and complete
- The Specialized Layer has functional areas that deliver specific value-added features, such as RASP or SLO-support, that are increasingly required by some organizations, and may serve to identify distinctive traits during product selection
- The Differentiator Layer is aligned to the needs of organizations that manage complex and distributed environments and have embedded APM and observability solutions into the fabric of their development, deployment, and operations processes.
- ![[APM Functional Areas.png]]

## IBM Instana
- Gartner-mentioned limitations
	- No ServiceNow integration
	- Limited Cloud Visiblity
- Current deployment
	- Primarily alerts on system / service outages
		Some apps have other thresholds mentioned
			Contention Rate High
			GC Time Percentage High
		- No mention of "business transaction" performance
			- No mention of transactions at all
	- Seems to be tied to app's .exe -- how can this work for SaaS / PaaS?
	- Has Sterling -- but not OMFT!
	- Has "ESB" but not OIC...
- Cloud Platforms Supported
	- Google, AWS, Azure, IBM
	- ... **but not Oracle**
- Oracle aspects
	- Supports Oracle for Cloud Monitoring
	- No support for Oracle for Observability
		- **But they do support Google, AWS, Azure, IBM for this**
	- OIC ?
	- OCI ?
- Third party SaaS
- SalesForce apps
- Instrumentation options?
	- Maximo is Java-based: is it eligible?
## Runscope
- Seems to cover OIC, cloud
- Covers API monitoring
- Has integrations with APMs
	- But not apparently Instana
## Kyndryl Meeting Findings
- Operational Readiness - APM
	- c. April-July 2021 for tool deployments
	- Can only monitor COTS at a threshold level
	- Need custom APIs for use with Oracle
		- Which Oracle products / services?
		- CCS at least would need a custom API
			- To be developed by Vinay's AMS team
				- Need an RFS for this
	- No use of correlation engine yet
	- No plan yet for turning / configuring APM for suitable thresholds, etc.
		- Need an RFS for this!