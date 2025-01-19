#Technology #definition #Oracle  #HA_DR 
1.  [Learn about architecting a highly available cloud topology](https://docs.oracle.com/en/solutions/design-ha/index.html)
2.  Learn About High Availability in the Cloud

You need your applications in the cloud to be available 24/7; their workloads must continue to run regardless of any outages in the cloud infrastructure. Designing a highly available service or application will help ensure maximum potential uptime and accessibility.

### About High Availability

To design a high availability architecture, three key elements should be considered— redundancy, monitoring, and failover:

-   Redundancy means that multiple components can perform the same task. The problem of a single point of failure is eliminated because redundant components can take over a task performed by a component that has failed.
-   Monitoring means checking whether or not a component is working properly.
-   Failover is the process by which a secondary component becomes primary when the primary component fails.

The best practices introduced here focus on these three key elements. Although high availability can be achieved at many different levels, including the application level and the cloud infrastructure level, here we will focus on the cloud infrastructure level.

### About the High Availability Capabilities of Oracle Cloud

An Oracle Cloud Infrastructure region is a localized geographic area composed of one or more availability domains, each composed of three fault domains. High availability is ensured by a redundancy of fault domains within the availability domains.

An availability domain is one or more data centers located within a region. Availability domains are isolated from each other, fault tolerant, and unlikely to fail simultaneously. Because availability domains do not share physical infrastructure, such as power or cooling, or the internal availability domain network, a failure that impacts one availability domain is unlikely to impact the availability of others.

A fault domain is a grouping of hardware and infrastructure within an availability domain. Each availability domain contains three fault domains. Fault domains let you distribute your instances so that they are not on the same physical hardware within a single availability domain. As a result, an unexpected hardware failure or a Compute hardware maintenance that affects one fault domain does not affect instances in other fault domains. You can optionally specify the fault domain for a new instance at launch time, or you can let the system select one for you.

All the availability domains in a region are connected to each other by a low-latency, high bandwidth network. This predictable, encrypted interconnection between availability domains provides the building blocks for both high availability and disaster recovery.

Oracle Cloud Infrastructure resources are either specific to a region, such as a virtual cloud network, or specific to an availability domain, such as a Compute instance. When you configure your cloud services, if the services are specific to an availability domain, it is important to leverage multiple availability domains or fault domains to ensure high availability and to protect against resource failure. By creating redundant Compute instances in other availability domains or fault domains, you can avoid an impact to your applications by an issue that affects the primary Compute instance or its domain. You can design solutions to have multiple regions, multiple availability domains, or multiple fault domains, depending on the class of failures you want protect against.

Learn about architecting a highly available cloud topology

F24736-01

February 2020

Copyright © 2020, Oracle and/or its affiliates. 

This software and related documentation are provided under a license agreement containing restrictions on use and disclosure and are protected by intellectual property laws. Except as expressly permitted in your license agreement or allowed by law, you may not use, copy, reproduce, translate, broadcast, modify, license, transmit, distribute, exhibit, perform, publish, or display any part, in any form, or by any means. Reverse engineering, disassembly, or decompilation of this software, unless required by law for interoperability, is prohibited.

The information contained herein is subject to change without notice and is not warranted to be error-free. If you find any errors, please report them to us in writing.

If this is software or related documentation that is delivered to the U.S. Government or anyone licensing it on behalf of the U.S. Government, then the following notice is applicable:

U.S. GOVERNMENT END USERS: Oracle programs (including any operating system, integrated software, any programs embedded, installed or activated on delivered hardware, and modifications of such programs) and Oracle computer documentation or other Oracle data delivered to or accessed by U.S. Government end users are "commercial computer software" or “commercial computer software documentation” pursuant to the applicable Federal Acquisition Regulation and agency-specific supplemental regulations. As such, the use, reproduction, duplication, release, display, disclosure, modification, preparation of derivative works, and/or adaptation of i) Oracle programs (including any operating system, integrated software, any programs embedded, installed or activated on delivered hardware, and modifications of such programs), ii) Oracle computer documentation and/or iii) other Oracle data, is subject to the rights and limitations specified in the license contained in the applicable contract. The terms governing the U.S. Government’s use of Oracle cloud services are defined by the applicable contract for such services. No other rights are granted to the U.S. Government.

This software or hardware is developed for general use in a variety of information management applications. It is not developed or intended for use in any inherently dangerous applications, including applications that may create a risk of personal injury. If you use this software or hardware in dangerous applications, then you shall be responsible to take all appropriate fail-safe, backup, redundancy, and other measures to ensure its safe use. Oracle Corporation and its affiliates disclaim any liability for any damages caused by use of this software or hardware in dangerous applications.

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.

Intel and Intel Inside are trademarks or registered trademarks of Intel Corporation. All SPARC trademarks are used under license and are trademarks or registered trademarks of SPARC International, Inc. AMD, Epyc, and the AMD logo are trademarks or registered trademarks of Advanced Micro Devices. UNIX is a registered trademark of The Open Group.

This software or hardware and documentation may provide access to or information about content, products, and services from third parties. Oracle Corporation and its affiliates are not responsible for and expressly disclaim all warranties of any kind with respect to third-party content, products, and services unless otherwise set forth in an applicable agreement between you and Oracle. Oracle Corporation and its affiliates will not be responsible for any loss, costs, or damages incurred due to your access to or use of third-party content, products, or services, except as set forth in an applicable agreement between you and Oracle.