 #Oracle #OIC #OCI #Integration 
# Oracle Integration Issues
## MFT
- Billed as the alternative to OIC File Transfer when files are > 1GB (as OIC has limited support over 1MB, and none over 1GB)
- Gen1 vs Gen2 limitations (see below)
## OIC File Transfer
- Limitations based on size requires different integration logic / implementations
	- Files up to 1MB: fully-functional
	- Between 1-10MB: only XML or CSV, files must  be read in segments / stages
	- > 10MB: option to download to storage instead (up to 1GB)
	- > 1GB: unsupported
## Gen1 vs Gen2
- Integrations Gen1 did not meet requirements for Object Storage
- Integrations Gen2 *does* meet Object Storage requirements
- There is no in-place upgrade capability to go from Gen1 to Gen2
	- Instead a separate Gen2 instance was commissioned to handle the requirements of CIS/WAM
- Opinion is that it is non-trivial to commission / migrate from Gen1 to Gen2
- Result is that we have multiple generations in use, sometimes within the same applications / systems
## Maximo via OCI
- Maximo sends data back out of order
	- Unclear if this is a weirdness of Maximo or the connector adapter
- Workaround was to not use OIC but instead rely on OCI streaming to get the proper order + persistence
## HA / DR
- HA achievable via appropriate OIC (and OCI) allocation to fault domains
	- Unclear if this was deployed correctly in the past hence HA not always consistent across service components
- Inadequate monitoring in place (including notifications) to manager / verify availability (Kyndryl problem?)
- DR for OIC
	- Oracle has indicated that this is the customer's responsibility
	- Seems to involve provisioning of underlying components (WebLogic, database, replication) along with load balancers (?), schedulers (?)
		- This should not be an end-customer item to architect -- it should be something requested of / provisioned by Oracle as a core capability
	- Some of the "Integrations" services are not part of OIC but instead provided by OIC (like MFT, Streaming)
		- Unclear re their respective resiliency / HA DR capabilities
- Is a third-party Event Broker necessary / useful to guarantee no less of message requests in the case of failover?
## Overall Issue
- Due to re-branding, re-packaging, acquisitions, etc. it is very unclear what the various Integrations components are from Oracle
	- Documentation online is inconsistent, making it unclear if additional components are being discussed, or merely ones that have been renamed or deprecated
	- **Need a landscape view of the Oracle Integrations components, whether they are part of OCI, OIC, or whatever**
	- 