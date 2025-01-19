#Integration #strategy 
# Legacy
# Proposed
## Tech
- OIC-to-OIC:
	- Oracle Integration Cloud
	- Oracle MFT
- On-Prem (Legacy)
	- TivTalk
	- IBM Integration Bus
	- IBM Sterling MFT
## Patterns
- OIC patterns: [[OIC Patterns]]
- Conventional patterns: [[Integration Patterns]]
- 
## Principles (brief)
## Constraints
- Latency / Network Overhead
	- Typical when integrating between cloud and on-prem
	- Legacy systems remaining on-prem may still need to leverage on-prem tech
## Legacy Tech
- IBM Integrated Bus (IIB)
	- Based on WebSphere and MQ
- Tivoli System Manager (TSM)
### CIS / WAM
- TivTalk is Tivoli System Manager (TSM).  It is used to move files between ERP and BMO.  We replaced TivTalk for the Gas business, but not yet for Electric. I have asked, but have not been able to get a full landscape of where TivTalk is used across the Enterprise.  No new use of this technology in CIS/WAM solutions.
- IBM Integration Bus is in use with legacy systems.  No new use of this technology in CIS/WAM solutions.