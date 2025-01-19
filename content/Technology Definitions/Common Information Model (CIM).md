#Technology #definition #ITSM #Standards #DMTF #CIM

# CIM
<table><caption>Common Information Model</caption><tbody><tr><th scope="row">Abbreviation</th><td>CIM</td></tr><tr><th scope="row">Status</th><td>Published</td></tr><tr><th scope="row">Year started</th><td>1999<span>; 23&nbsp;years ago</span></td></tr><tr><th scope="row">Organization</th><td><a href="https://en.wikipedia.org/wiki/Distributed_Management_Task_Force" title="Distributed Management Task Force">Distributed Management Task Force</a></td></tr><tr><th scope="row">Related standards</th><td><a href="https://en.wikipedia.org/wiki/Web-Based_Enterprise_Management" title="Web-Based Enterprise Management">WBEM</a> and <a href="https://en.wikipedia.org/wiki/Systems_Management_Architecture_for_Server_Hardware" title="Systems Management Architecture for Server Hardware">SMASH</a></td></tr><tr><th scope="row">Domain</th><td><a href="https://en.wikipedia.org/wiki/Information_model" title="Information model">Information model</a></td></tr><tr><th scope="row">Website</th><td><span><a rel="nofollow" href="http://www.dmtf.org/standards/cim">www<wbr>.dmtf<wbr>.org<wbr>/standards<wbr>/cim</a></span></td></tr></tbody></table>

The **Common Information Model** (**CIM**) is an [open standard](https://en.wikipedia.org/wiki/Open_standard "Open standard") that defines how managed elements in an [IT environment](https://en.wikipedia.org/wiki/Information_technology "Information technology") are represented as a common set of [objects](https://en.wikipedia.org/wiki/Object_(computer_science) "Object (computer science)") and relationships between them.

The [Distributed Management Task Force](https://en.wikipedia.org/wiki/Distributed_Management_Task_Force "Distributed Management Task Force") maintains the CIM to allow consistent [management](https://en.wikipedia.org/wiki/Systems_management "Systems management") of these managed elements, independent of their manufacturer or provider.

## Overview\[[edit](https://en.wikipedia.org/w/index.php?title=Common_Information_Model_(computing)&action=edit&section=1 "Edit section: Overview")\]

One way to describe CIM is to say that it allows multiple parties to exchange management information about these managed elements. However, this falls short in expressing that CIM not only represents these managed elements and the management information, but also provides means to actively control and manage these elements. By using a common model of information, management software can be written once and work with many implementations of the common model without complex and costly conversion operations or loss of information.

The CIM standard is defined and published by the [Distributed Management Task Force](https://en.wikipedia.org/wiki/Distributed_Management_Task_Force "Distributed Management Task Force") (DMTF). A related standard is [Web-Based Enterprise Management](https://en.wikipedia.org/wiki/Web-Based_Enterprise_Management "Web-Based Enterprise Management") (WBEM, also defined by DMTF) which defines a particular implementation of CIM, including protocols for discovering and accessing such CIM implementations.

## Schema and specifications\[[edit](https://en.wikipedia.org/w/index.php?title=Common_Information_Model_(computing)&action=edit&section=2 "Edit section: Schema and specifications")\]

The CIM standard includes the **CIM Infrastructure Specification** and the **CIM Schema**:

-   **CIM Infrastructure Specification**

The CIM Infrastructure Specification defines the architecture and concepts of CIM, including a language by which the CIM Schema (including any extension schema) is defined, and a method for mapping CIM to other information models, such as [SNMP](https://en.wikipedia.org/wiki/Simple_Network_Management_Protocol "Simple Network Management Protocol"). The CIM architecture is based upon [UML](https://en.wikipedia.org/wiki/Unified_Modeling_Language "Unified Modeling Language"), so it is object-oriented: The managed elements are represented as CIM [classes](https://en.wikipedia.org/wiki/Class_(computer_science) "Class (computer science)") and any relationships between them are represented as CIM [associations](https://en.wikipedia.org/wiki/Association_(object-oriented_programming) "Association (object-oriented programming)"). [Inheritance](https://en.wikipedia.org/wiki/Inheritance_(computer_science) "Inheritance (computer science)") allows specialization of common base elements into more specific derived elements.

-   **CIM Schema**

The [CIM Schema](https://en.wikipedia.org/wiki/CIM_Schema "CIM Schema") is a [conceptual schema](https://en.wikipedia.org/wiki/Conceptual_schema "Conceptual schema") which defines the specific set of objects and relationships between them that represent a common base for the managed elements in an [IT environment](https://en.wikipedia.org/wiki/Information_technology "Information technology"). The CIM Schema covers most of today's elements in an IT environment, for example [computer systems](https://en.wikipedia.org/wiki/Computer_system "Computer system"), [operating systems](https://en.wikipedia.org/wiki/Operating_system "Operating system"), [networks](https://en.wikipedia.org/wiki/Computer_network "Computer network"), [middleware](https://en.wikipedia.org/wiki/Middleware "Middleware"), [services](https://en.wikipedia.org/wiki/Daemon_(computer_software) "Daemon (computer software)") and [storage](https://en.wikipedia.org/wiki/Computer_storage "Computer storage"). Classes can be, for example: _CIM\_ComputerSystem_, _CIM\_OperatingSystem_, _CIM\_Process_, _CIM\_DataFile_. The CIM Schema defines a common basis for representing these managed elements. Since most managed elements have product and vendor specific behavior, the CIM Schema is extensible in order to allow the producers of these elements to represent their specific features seamlessly together with the common base functionality defined in the CIM Schema.

Updates to the CIM Schema are published regularly.[\[1\]](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_note-1)

CIM is the basis for most of the other DMTF standards (e.g. [WBEM](https://en.wikipedia.org/wiki/Web-Based_Enterprise_Management "Web-Based Enterprise Management") or [SMASH](https://en.wikipedia.org/wiki/Systems_Management_Architecture_for_Server_Hardware "Systems Management Architecture for Server Hardware")). It is also the basis for the [SMI-S](https://en.wikipedia.org/wiki/Storage_Management_Initiative_-_Specification "Storage Management Initiative - Specification") standard for storage management.

## Implementations\[[edit](https://en.wikipedia.org/w/index.php?title=Common_Information_Model_(computing)&action=edit&section=3 "Edit section: Implementations")\]

### Infrastructure Implementations\[[edit](https://en.wikipedia.org/w/index.php?title=Common_Information_Model_(computing)&action=edit&section=4 "Edit section: Infrastructure Implementations")\]

Many vendors provide implementations of CIM in various forms:

-   Some operating systems provide a CIM implementation, for example:
    -   the [Windows Management Instrumentation](https://en.wikipedia.org/wiki/Windows_Management_Instrumentation "Windows Management Instrumentation") (WMI) [API](https://en.wikipedia.org/wiki/Application_programming_interface "Application programming interface") available in [Microsoft](https://en.wikipedia.org/wiki/Microsoft "Microsoft") [Windows 2000](https://en.wikipedia.org/wiki/Windows_2000 "Windows 2000") and higher
    -   the Windows Management Infrastructure (MI) API for Microsoft Windows 2012 and higher[\[2\]](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_note-2)
    -   some [Linux distributions](https://en.wikipedia.org/wiki/Linux_distribution "Linux distribution") with the [SBLIM](https://en.wikipedia.org/w/index.php?title=SBLIM&action=edit&redlink=1 "SBLIM (page does not exist)") (Standards Based Linux Instrumentation for Manageability) project[\[3\]](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_note-3)
-   Some implementations are Independent of the systems they support, for example:
    -   Open Group's Pegasus
    -   WSI's J WBEM Server

There is also a growing\[_[quantify](https://en.wikipedia.org/wiki/Wikipedia:Manual_of_Style/Dates_and_numbers "Wikipedia:Manual of Style/Dates and numbers")_\] number of tools market around CIM.[\[4\]](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_note-4)

### Management Standards based on the CIM Schema\[[edit](https://en.wikipedia.org/w/index.php?title=Common_Information_Model_(computing)&action=edit&section=5 "Edit section: Management Standards based on the CIM Schema")\]

Standards organizations have defined management standards based on the CIM Schema:

-   The [Storage Networking Industry Association](https://en.wikipedia.org/wiki/Storage_Networking_Industry_Association "Storage Networking Industry Association") (SNIA) has heavily bought into using CIM and WBEM: they have defined their usage of CIM (called [Storage Management Initiative – Specification](https://en.wikipedia.org/wiki/Storage_Management_Initiative_%E2%80%93_Specification "Storage Management Initiative – Specification") or **SMI-S**) as a standard.
-   Some [server](https://en.wikipedia.org/wiki/Server_(computing) "Server (computing)") manufacturers collaborate in the DMTF under the [SMASH](https://en.wikipedia.org/wiki/Systems_Management_Architecture_for_Server_Hardware "Systems Management Architecture for Server Hardware") initiative to define CIM-based management of servers.
-   The [DASH](https://en.wikipedia.org/wiki/Desktop_and_mobile_Architecture_for_System_Hardware "Desktop and mobile Architecture for System Hardware") initiative in the DMTF attempts to define CIM-based management of [desktop computers](https://en.wikipedia.org/wiki/Desktop_computer "Desktop computer").

### Communication protocols used\[[edit](https://en.wikipedia.org/w/index.php?title=Common_Information_Model_(computing)&action=edit&section=6 "Edit section: Communication protocols used")\]

A number of protocols are defined for messages transmitted between clients and servers. The message protocols are transmitted on top of [HTTP](https://en.wikipedia.org/wiki/HTTP "HTTP"). There are two message types:

1.  operational messages, which provoke a response from the receiver ([RPC](https://en.wikipedia.org/wiki/Remote_Procedure_Call "Remote Procedure Call"))
2.  export messages, which are indications/events.

#### CIM Operations over HTTP (CIM-XML)\[[edit](https://en.wikipedia.org/w/index.php?title=Common_Information_Model_(computing)&action=edit&section=7 "Edit section: CIM Operations over HTTP (CIM-XML)")\]

CIM-XML forms part of the WBEM protocol family, and is standardised by the DMTF.

CIM-XML comprises three specifications:

1.  CIM Operations over HTTP[\[5\]](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_note-5)
2.  Representation of CIM using XML[\[6\]](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_note-6)
3.  CIM DTD[\[7\]](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_note-7)

#### WS-Management\[[edit](https://en.wikipedia.org/w/index.php?title=Common_Information_Model_(computing)&action=edit&section=8 "Edit section: WS-Management")\]

WS-MAN forms part of the WBEM protocol family, and is standardised by the DMTF.

WS-MAN comprises 3 specifications:

1.  WS-CIM Mapping Specification[\[8\]](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_note-8)
2.  WS-Management CIM Binding Specification[\[9\]](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_note-9)
3.  Web Services for Management (WS- Management) Specification[\[10\]](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_note-10)

#### CIM operations over RESTful services\[[edit](https://en.wikipedia.org/w/index.php?title=Common_Information_Model_(computing)&action=edit&section=9 "Edit section: CIM operations over RESTful services")\]

CIM-RS forms part of the WBEM protocol family, and is standardised by the DMTF.

CIM-RS comprises three specifications:

1.  CIM Operations Over RESTful Services[\[11\]](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_note-11)
2.  CIM-RS Protocol Specification[\[12\]](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_note-12)
3.  CIM-RS Payload Representation in JSON[\[13\]](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_note-13)

## See also\[[edit](https://en.wikipedia.org/w/index.php?title=Common_Information_Model_(computing)&action=edit&section=10 "Edit section: See also")\]

-   [Storage Management Initiative – Specification](https://en.wikipedia.org/wiki/Storage_Management_Initiative_%E2%80%93_Specification "Storage Management Initiative – Specification")

## References\[[edit](https://en.wikipedia.org/w/index.php?title=Common_Information_Model_(computing)&action=edit&section=11 "Edit section: References")\]

1.  **[^](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_ref-1 "Jump up")** ["CIM Schemas"](https://web.archive.org/web/20180928222603/https://www.dmtf.org/standards/cim/schemas). Distributed Management Task Force, Inc. Archived from [the original](http://dmtf.org/standards/cim/schemas) on 28 September 2018. Retrieved 28 September 2018.
2.  **[^](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_ref-2 "Jump up")** REDMOND\\\\markl. ["Windows Management Infrastructure (MI)"](https://docs.microsoft.com/en-us/previous-versions/windows/desktop/wmi_v2/windows-management-infrastructure). _docs.microsoft.com_. Retrieved 2019-12-31.
3.  **[^](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_ref-3 "Jump up")** [_SBLIM_](http://sourceforge.net/projects/sblim), Sourceforge
4.  **[^](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_ref-4 "Jump up")** ["CIM/WBEM Tools (in the DMTF members area)"](https://members.dmtf.org/members/tools/).
5.  **[^](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_ref-5 "Jump up")** [_CIM Operations over HTTP_](http://www.dmtf.org/sites/default/files/standards/documents/DSP0200_1.3.1.pdf) (PDF), DMTF
6.  **[^](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_ref-6 "Jump up")** [_Representation of CIM using XML_](http://www.dmtf.org/sites/default/files/standards/documents/DSP0201_2.3.1.pdf) (PDF), DMTF
7.  **[^](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_ref-7 "Jump up")** [_CIM-XML DTD_](http://www.dmtf.org/sites/default/files/standards/documents/DSP0203_2.4.0.dtd), DMTF
8.  **[^](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_ref-8 "Jump up")** ["WS-CIM Mapping Specification"](https://www.dmtf.org/sites/default/files/standards/documents/DSP0230_1.1.0.pdf) (PDF).
9.  **[^](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_ref-9 "Jump up")** ["WS-Management CIM Binding Specification"](https://www.dmtf.org/sites/default/files/standards/documents/DSP0227_1.2.0.pdf) (PDF).
10.  **[^](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_ref-10 "Jump up")** ["Web Services for Management (WS-Management) Specification"](https://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) (PDF).
11.  **[^](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_ref-11 "Jump up")** ["CIM Operations Over RESTful Services"](https://www.dmtf.org/sites/default/files/standards/documents/DSP-IS0201_1.0.0.pdf) (PDF).
12.  **[^](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_ref-12 "Jump up")** ["CIM-RS Protocol Specification"](https://www.dmtf.org/sites/default/files/standards/documents/DSP0210_2.0.0.pdf) (PDF).
13.  **[^](https://en.wikipedia.org/wiki/Common_Information_Model_(computing)#cite_ref-13 "Jump up")** ["CIM-RS Payload Representation in JSON"](https://www.dmtf.org/sites/default/files/standards/documents/DSP0211_2.0.0.pdf) (PDF).

## External links\[[edit](https://en.wikipedia.org/w/index.php?title=Common_Information_Model_(computing)&action=edit&section=12 "Edit section: External links")\]

-   [_CIM_](http://www.dmtf.org/standards/cim/), Standards, DMTF, including CIM Schema and CIM Infrastructure Specification.
-   [_CIM definition_](http://www.linktionary.com/c/cim.html), Linktionary.
-   [_CIM definition_](https://web.archive.org/web/20071009123101/http://www.networkcomputing.com/912/912ws1.html), Networkcomputing, archived from [the original](http://www.networkcomputing.com/912/912ws1.html) on 2007-10-09, retrieved 2006-12-11.
-   [_CIM definition_](http://searchstorage.techtarget.com/sDefinition/0,,sid5_gci875993,00.html), Searchstorage, Techtarget.
-   [_CIM_](https://web.archive.org/web/20080410002716/http://www.wbemsolutions.com/tutorials/CIM/cim.html), Tutorials, WBEM Solutions, archived from [the original](http://www.wbemsolutions.com/tutorials/CIM/cim.html) on 2008-04-10, retrieved 2006-12-11.
-   [_SBLIM_](http://sourceforge.net/projects/sblim), Sourceforge.