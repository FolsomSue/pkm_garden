#Technology #definition #Industry_Definitions  #OPC
**OPC Unified Architecture** (**OPC UA**) is a [machine to machine](https://en.wikipedia.org/wiki/Machine_to_machine "Machine to machine") [communication protocol](https://en.wikipedia.org/wiki/Communication_protocol "Communication protocol") for [industrial automation](https://en.wikipedia.org/wiki/Industrial_automation "Industrial automation") developed by the [OPC Foundation](https://en.wikipedia.org/wiki/OPC_Foundation "OPC Foundation"). Distinguishing characteristics are:

-   Based on a client server communication
-   Focus on communicating with industrial equipment and systems for data collection and control
-   [Open](https://en.wikipedia.org/wiki/Open_standard "Open standard") - freely available and implementable under GPL 2.0 license [\[1\]](https://en.wikipedia.org/wiki/OPC_Unified_Architecture#cite_note-1)
-   [Cross-platform](https://en.wikipedia.org/wiki/Cross-platform "Cross-platform") - not tied to one operating system or programming language
-   [Service-oriented architecture](https://en.wikipedia.org/wiki/Service-oriented_architecture "Service-oriented architecture") (SOA)
-   Inherent complexity - in September 2020, the specification consisted of 3151 pages in 15 documents
-   Offers [security](https://en.wikipedia.org/wiki/Information_security "Information security") functionality for authentication, authorization, integrity and confidentiality[\[2\]](https://en.wikipedia.org/wiki/OPC_Unified_Architecture#cite_note-2)
-   Integral [information model](https://en.wikipedia.org/wiki/Information_model "Information model"), which is the foundation of the infrastructure necessary for information integration where vendors and organizations can model their complex data into an OPC UA namespace to take advantage of the rich service-oriented architecture of OPC UA. There are over 35 collaborations with the OPC Foundation currently. Key industries include [pharmaceutical](https://en.wikipedia.org/wiki/Pharmaceutical_industry "Pharmaceutical industry"), [oil and gas](https://en.wikipedia.org/wiki/Oil_and_gas_industry "Oil and gas industry"), [building automation](https://en.wikipedia.org/wiki/Building_automation "Building automation"), [industrial robotics](https://en.wikipedia.org/wiki/Industrial_robotics "Industrial robotics"), security, manufacturing and [process control](https://en.wikipedia.org/wiki/Process_control "Process control").

## History\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=1 "Edit section: History")\]

Although developed by the same organization, OPC UA differs significantly from its predecessor, [Open Platform Communications](https://en.wikipedia.org/wiki/Open_Platform_Communications "Open Platform Communications") (OPC). The Foundation's goal for OPC UA was to provide a path forward from the original [OPC](https://en.wikipedia.org/wiki/OLE_for_process_control "OLE for process control") communications model (namely the [Microsoft Windows](https://en.wikipedia.org/wiki/Microsoft_Windows "Microsoft Windows")\-only process exchange COM/[DCOM](https://en.wikipedia.org/wiki/Distributed_Component_Object_Model "Distributed Component Object Model")) that would better meet the emerging needs of [industrial automation](https://en.wikipedia.org/wiki/Industrial_automation "Industrial automation").[\[3\]](https://en.wikipedia.org/wiki/OPC_Unified_Architecture#cite_note-3)

After more than three years of specification work and another year for a prototype implementation, the first version of the Unified Architecture was released in 2006.

The current version of the specification is on 1.04 (22 November 2017[\[4\]](https://en.wikipedia.org/wiki/OPC_Unified_Architecture#cite_note-4)). The new version of OPC UA now has added publish/subscribe in addition to the client/server communications infrastructure.

## Innovations\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=2 "Edit section: Innovations")\]

Although the original binding to COM/[DCOM](https://en.wikipedia.org/wiki/Distributed_Component_Object_Model "Distributed Component Object Model") helped [OPC](https://en.wikipedia.org/wiki/OLE_for_process_control "OLE for process control") to distribute well, it had several drawbacks:

-   Frequent configuration issues with DCOM;
-   No configurable time-outs;
-   [Microsoft Windows](https://en.wikipedia.org/wiki/Microsoft_Windows "Microsoft Windows") only;
-   Lower security;
-   No control over DCOM (COM/DCOM is kind of a black box, developers have no access to sources and therefore have to deal with bugs or insufficient implementations).

These drawbacks along with a number of other considerations pushed the decision to develop a new and independent stack for OPC UA, which replaces COM/DCOM. The main characteristics of this communication stack were:

-   Multi-platform implementation, including portable [ANSI C](https://en.wikipedia.org/wiki/ANSI_C "ANSI C"), [Java](https://en.wikipedia.org/wiki/Java_(software_platform) "Java (software platform)") and [.NET](https://en.wikipedia.org/wiki/.NET_Framework ".NET Framework") implementations;
-   Scalability: from smart sensors and smart actuators to mainframes;
-   Multi-threaded, as well as single-threaded/single-task operation—necessary for porting the stack to embedded devices;
-   Security, based on new standards;
-   Configurable time-outs for each service;
-   Chunking of big datagrams.

This communication stack reflects the beginning of various innovations. The OPC UA architecture is a service-oriented architecture (SOA) and is based on different logical levels.

OPC Base Services are abstract method descriptions, which are protocol independent and provide the basis for OPC UA functionality. The transport layer puts these methods into a protocol, which means it serializes/deserializes the data and transmits it over the network. Two [protocols](https://en.wikipedia.org/wiki/Communication_protocol "Communication protocol") are specified for this purpose. One is a binary [TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol "Transmission Control Protocol") protocol, optimized for high performance and the second is [Web service](https://en.wikipedia.org/wiki/Web_service "Web service")\-oriented.

The OPC information model is a so-called Full Mesh Network based on [nodes](https://en.wikipedia.org/wiki/Node_(networking) "Node (networking)"). These nodes can include any kind of meta information, and are similar to the objects of [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming") (OOP). A node can have attributes for read access (DA, HDA), methods that can be called (Commands), and triggered events that can be transmitted (AE, DataAccess, DataChange). Nodes hold process data as well all other types of [metadata](https://en.wikipedia.org/wiki/Metadata "Metadata"). The OPC namespace contains the type model.

Client software can verify what profiles a server supports. This is necessary to obtain information, if a server only supports DA functionality or additionally AE, HDA, etc. Additionally, information can be obtained about whether a server supports a given profile. New and important features of OPC UA are:

-   Redundancy support
-   Heartbeat for connections in both directions (to indicate whether the other end is "alive"). This means that both server and client recognize interrupts.
-   Buffering of data and acknowledgements of transmitted data. Lost connections don't lead to lost data anymore. Lost datagrams can be refetched.

At the OPC UA DevCon in October 2006, in Munich the first prototypes were presented live. Various UA Servers have been shown on a Beckhoff [programmable logic controller](https://en.wikipedia.org/wiki/Programmable_logic_controller "Programmable logic controller") and an embedded test board from Euros. The Beckhoff PLC is based on Windows XP Embedded and the embedded controller is based on the [real-time operating system](https://en.wikipedia.org/wiki/Real-time_operating_system "Real-time operating system") Euros. The company Embedded Labs Ltd demonstrated an OPC UA Server based on their own C++ UA Stack executing on a single chip [ARM](https://en.wikipedia.org/wiki/ARM_Holdings "ARM Holdings") microcontroller with 64kB [RAM](https://en.wikipedia.org/wiki/RAM "RAM"). In October 2012 the German Fraunhofer-Application Center IOSB-INA and the Institute for industrial Information Technologies (inIT) showed that an OPC UA server is scalable down to 15 kB RAM and 10 kB ROM and therefore usable at chip level.[\[5\]](https://en.wikipedia.org/wiki/OPC_Unified_Architecture#cite_note-5)

## Protocols\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=3 "Edit section: Protocols")\]

OPC UA supports two protocols.[\[6\]](https://en.wikipedia.org/wiki/OPC_Unified_Architecture#cite_note-6) This is visible to application programmers only via changes to the URL. The binary protocol is opc.tcp://Server and http://Server is for Web Service. Otherwise OPC UA works completely transparent to the [API](https://en.wikipedia.org/wiki/Application_programming_interface "Application programming interface").

The binary protocol offers the best performance/least overhead, takes minimum resources (no XML Parser, [SOAP](https://en.wikipedia.org/wiki/SOAP "SOAP") and [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol "Hypertext Transfer Protocol") required, which is important for embedded devices), offers best interoperability (binary is explicitly specified and allows fewer degrees of freedom during implementation) and uses a single arbitrarily choosable TCP port for communication easing tunneling or easy enablement through a firewall.

The Web Service (SOAP) protocol is best supported from available tools, e.g., from Java or .NET environments, and is firewall-friendly, using standard HTTP(S) ports.

Binary is supported by all implementations, while only .NET implementation supports SOAP.

## Specifications\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=4 "Edit section: Specifications")\]

The OPC UA specification is a multi-part specification and consists of the following parts:

1.  Concepts
2.  Security Model
3.  Address Space Model
4.  Services
5.  Information Model
6.  Mappings
7.  Profiles
8.  Data Access
9.  Alarms and Conditions
10.  Programs
11.  Historical Access
12.  Discovery and Global Services
13.  Aggregates
14.  PubSub

In contrast to the COM-based specifications, the UA specifications are not pure application specifications. They describe typically UA internal mechanisms, which get handled through the communication stack and are normally only of interest for those that port a stack to a specific target or those that want to implement their own UA stack.

The OPC UA application developers code against the OPC UA API and therefore mainly use API documentation. Nevertheless, part 3, 4, and 5 may be of interest for application developers.[\[7\]](https://en.wikipedia.org/wiki/OPC_Unified_Architecture#cite_note-7)

## Discussion\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=5 "Edit section: Discussion")\]

The OPC UA protocol specification consists of 14 documents for a total of 1250 pages. Due to this complexity, existing implementations are usually incomplete. In addition, the existence of several serialization formats, as well as the possibility of selectively implementing certain services such as PubSub, eventually lead to a great heterogeneity of the OPC UA connection points. Under these conditions, it is finally difficult to develop client applications that are independent of the specific implementation of each server. In this sense, OPC UA does not achieve its promise of ensuring good interoperability of systems. This can be seen typically in factory and infrastructure projects integrating various PLC technologies, each delivered with a different and limited implementation of the OPC UA protocol.

The specification is still evolving, the last specification document volume 14 is dated February 6, 2018, while the first publication of the standard OPC UA dates from 2006.

As a result, despite considerable marketing efforts to support its adoption, OPC UA may be considered at this stage as a standardization attempt rather than an established standard.

## UA communication stack\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=6 "Edit section: UA communication stack")\]

The architecture of a UA application, independent of whether it is the server or client part, is structured into levels.

Some parts equalize to the former COM Proxy/Stubs and get provided by the OPC Foundation. The portability level is new; it simplifies porting the UA ANSI C stack to other target platforms. A port layer for Windows and [Linux](https://en.wikipedia.org/wiki/Linux "Linux") is also provided by the OPC Foundation.

## UA security\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=7 "Edit section: UA security")\]

UA Security consists of authentication and authorization, encryption and data integrity via signatures. For Web Services the [WS-SecureConversation](https://en.wikipedia.org/wiki/WS-SecureConversation "WS-SecureConversation") gets used and is therefore compatible to [.NET](https://en.wikipedia.org/wiki/.NET_Framework ".NET Framework") and other [SOAP](https://en.wikipedia.org/wiki/SOAP "SOAP") implementations. For the binary variant, the algorithms of WS-SecureConversation have been followed and also converted to a binary equivalent. This is named as UA Secure Conversation.

There is also a mixed version where the code is binary, but the transport layer is SOAP. This is a compromise between efficient binary coding and firewall-friendly transmission. Binary coding always requires UA Secure Conversation. The authentication uses [X.509](https://en.wikipedia.org/wiki/X.509 "X.509") certificates exclusively. It relies on the application developer to choose which certificate store the UA application gets bound to. For instance, it is possible to use the [public key infrastructure](https://en.wikipedia.org/wiki/Public_key_infrastructure "Public key infrastructure") (PKI) of an [Active Directory](https://en.wikipedia.org/wiki/Active_Directory "Active Directory").

## Built-in data types\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=8 "Edit section: Built-in data types")\]

The OPC UA standard defines 25 built-in data types:

OPC UA built-in data types

Built-in type

[C/C++ equivalent](https://en.wikipedia.org/wiki/C_data_types "C data types")

Details

NodeId type

Boolean

bool

0/1 (true or false)

0 (numeric)

SByte

int8\_t

\-128 to 127

Byte

uint8\_t

0 to 255

Int16

int16\_t

\-32768 to 32767

UInt16

uint16\_t

0 to 65535

Int32

int32\_t

\-2147483648 to 2147483647

UInt32

uint32\_t

0 to 4294967295

Int64

int64\_t

\-9223372036854775808 to 9223372036854775807

UInt64

uint64\_t

0 to 18446744073709551615

Float

float

IEEE single precision (32 bit) floating point value

Double

double

IEEE double precision (64 bit) floating point value

StatusCode

uint32\_t

String

uint8\_t\* / std::string

3 (string)

DateTime

int64\_t

number of 100 nanosecond intervals since 1/1/1601 (UTC)

GUID

implementation dependent

16-byte number used as a [unique identifier](https://en.wikipedia.org/wiki/Universally_unique_identifier "Universally unique identifier")

4 (GUID)

ByteString

(same as String)

5 (byte string)

XmlElement

(same as String)

NodeId

namespace index and NodeId type

ExpandedNodeId

(similar to NodeId)

QualifiedName

namespace index and string

LocalizedText

string and a locale indicator

NumericRange

string (e.g. "0:4,1:5" for \[0..4\]\[1..5\] array)

Variant

(built-in data types only)

ExtensionObject

scalars of any type

DataValue

a composite of a value, timestamps and status code

DiagnosticInfo

detailed error/diagnostic information

## OPC UA APIs\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=9 "Edit section: OPC UA APIs")\]

UA APIs are available in several programming languages. Commercial SDK are available for C, C++, Java, and .NET. Open-source stacks are available at least for C, C++, Java, Javascript(node), Tcl and Python [\[1\]](https://github.com/open62541/open62541/wiki/List-of-Open-Source-OPC-UA-Implementations).

### C++/C Implementation\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=10 "Edit section: C++/C Implementation")\]

-   The [open62541](https://open62541.org/) project provides an Open Source implementation for OPC UA server and clients and is licensed under the [Mozilla Public License](https://en.wikipedia.org/wiki/Mozilla_Public_License "Mozilla Public License") v2.0. Besides Linux and Windows, it also supports OS X, QNX and different embedded systems as compilation target.
-   The [S2OPC project](https://gitlab.com/systerel/S2OPC) provides an Open Source secured implementation and is licensed under the [Apache 2.0](https://en.wikipedia.org/wiki/Apache_License "Apache License") license. It supports Linux, Windows, FreeRTOS, Zephyr, VxWorks and aims to be safe, secure and fast. The core of the software is formally designed with the help of the [B-Method](https://en.wikipedia.org/wiki/B-Method "B-Method").
-   The [ASNeG project](https://asneg.github.io/) provides a C++ open source (Apache License 2.0) OPC UA Application Server and an OPC UA Web Server (beta state, currently only base functions).
-   The [FreeOpcUa](https://freeopcua.github.io/) project provides an open source ([LGPL](https://en.wikipedia.org/wiki/GNU_Lesser_General_Public_License "GNU Lesser General Public License")) server and client implementation in C++.
-   The [UAF](https://github.com/uaf/uaf) project offers an open source (LGPL) C++/Python implementation.

### .NET implementation\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=11 "Edit section: .NET implementation")\]

The .NET implementation uses ANSI C for the lower levels and implements the rest natively in .NET. That means only the handling of the socket and the Message-Chunking gets integrated from the ANSI C stack. De-serialization takes place directly in .NET and therefore gets converted directly into .NET structures and objects. This provides better performance than de-serializing into a C structure first and then copying the data to a .NET structure afterwards.

### Java implementation\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=12 "Edit section: Java implementation")\]

Various stacks for Java were being developed.\[_[when?](https://en.wikipedia.org/wiki/Wikipedia:Manual_of_Style/Dates_and_numbers#Chronological_items "Wikipedia:Manual of Style/Dates and numbers")_\] Similar to .NET, there are principally three variants:

1.  Encapsulate the complete ANSI C stack via [JNI](https://en.wikipedia.org/wiki/Java_Native_Interface "Java Native Interface"), which complicates portability. Although the stack can be ported to different operating systems, it needs to get compiled for those individually. Also, the data needs to get copied to the JNI boundary, but benefits from the performance of C during de-serialization.
2.  Code directly on the network layer (similar to the current .Net implementation) and de-serialize in Java. This saves one data copy execution, but still depends on the C stack.
3.  Write a native Java OPC UA stack. This was observed to be the most portable, but estimated to take the most engineering effort to implement. The Eclipse Milo project provides a pure-Java, open-source, implementation of the UA 1.03 client and server specification.[\[8\]](https://en.wikipedia.org/wiki/OPC_Unified_Architecture#cite_note-8)

Alternatively, there is the simple variant to only support the WebService protocol. For that, a SOAP Toolkit that supports [WS-Security](https://en.wikipedia.org/wiki/WS-Security "WS-Security") is needed.

### JavaScript implementation\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=13 "Edit section: JavaScript implementation")\]

[node-opcua](https://github.com/node-opcua/node-opcua) is a complete implementation of the OPC UA for client and server entirely writing in JavaScript for [Node.js](https://en.wikipedia.org/wiki/Node.js "Node.js").

### Python implementation\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=14 "Edit section: Python implementation")\]

-   The [FreeOpcUa](https://freeopcua.github.io/) project provides two implementations in pure Python programming language - [opcua-asyncio](https://github.com/FreeOpcUa/opcua-asyncio) (requires Python >=3.7) and [python-opcua](https://github.com/FreeOpcUa/python-opcua) (compatible with Python 2, 3 and pypy; it requires Cython for the lxml library, but is in maintenance mode and [opcua-asyncio](https://github.com/FreeOpcUa/opcua-asyncio) is recommended). Both provide high-level abstractions of an OPC UA client and server which can be used as is or readily extended for custom applications.
-   The [S2OPC](https://gitlab.com/systerel/S2OPC) C-implementation provides a python wrapper [PyS2OPC](https://sourceforge.net/projects/pyopc/).

### Rust implementation\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=15 "Edit section: Rust implementation")\]

[Rust for OPC UA](https://github.com/locka99/opcua) provides an API and samples for implementing OPC UA client and servers up to embedded profile level. This includes support for encryption, subscriptions and the default node set.

### TypeScript / JavaScript implementation\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=16 "Edit section: TypeScript / JavaScript implementation")\]

[TypeScript / JavaScript OPC UA client for the browser](https://github.com/HBM/opcua) is an OPC UA client that works in the browser. It is completely written in TypeScript and compiled to JavaScript. The source code is publicly available and has an MIT license. It includes OPC UA binary data encoding and uses WebSockets as the transport protocol.

### Tcl implementation\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=17 "Edit section: Tcl implementation")\]

[Topcua](https://wiki.tcl-lang.org/page/topcua) is a Tcl binding to OPC UA client and server. It provides several operations to manage and communicate using the OPC UA implementation. It is available on common POSIX and Windows platforms.

## IEC 62541\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=18 "Edit section: IEC 62541")\]

IEC 62541[\[9\]](https://en.wikipedia.org/wiki/OPC_Unified_Architecture#cite_note-9) is a standard for OPC Unified Architecture.

IEC 62541 Overview

ID

release date

title

IEC/TR 62541-1

2016

OPC Unified Architecture - Part 1: Overview and Concepts

IEC/TR 62541-2

2016

OPC Unified Architecture - Part 2: Security Model

IEC 62541-3

2020

OPC Unified Architecture - Part 3: Address Space Model

IEC 62541-4

2020

OPC Unified Architecture - Part 4: Services

IEC 62541-5

2020

OPC Unified Architecture - Part 5: Information Model

IEC 62541-6

2020

OPC Unified Architecture - Part 6: Mappings

IEC 62541-7

2020

OPC Unified Architecture - Part 7: Profiles

IEC 62541-8

2020

OPC Unified Architecture - Part 8: Data Access

IEC 62541-9

2020

OPC Unified Architecture - Part 9: Alarms and Conditions

IEC 62541-10

2020

OPC Unified Architecture - Part 10: Programs

IEC 62541-11

2020

OPC Unified Architecture - Part 11: Historical Access

IEC 62541-12

2020

OPC unified architecture - Part 12: Discovery and global services

IEC 62541-13

2020

OPC Unified Architecture - Part 13: Aggregates

IEC 62541-14

2020

OPC unified architecture - Part 14: PubSub

IEC 62541-100

2015

OPC Unified Architecture - Part 100: Device Interface

## See also\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=19 "Edit section: See also")\]

-   [OPC Data Access](https://en.wikipedia.org/wiki/OPC_Data_Access "OPC Data Access")
-   [OLE for process control](https://en.wikipedia.org/wiki/OLE_for_process_control "OLE for process control")
-   [OPC Foundation](https://en.wikipedia.org/wiki/OPC_Foundation "OPC Foundation")

## References\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=20 "Edit section: References")\]

1.  **[^](https://en.wikipedia.org/wiki/OPC_Unified_Architecture#cite_ref-1 "Jump up")** [https://opcfoundation.org/license/gpl.html](https://opcfoundation.org/license/gpl.html)
2.  **[^](https://en.wikipedia.org/wiki/OPC_Unified_Architecture#cite_ref-2 "Jump up")** Roepert, Linus; Dahlmanns, Markus; Fink, Ina Berenice; Pennekamp, Jan; Henze, Martin [https://www.comsys.rwth-aachen.de/fileadmin/papers/2020/2020-roepert-opcua-security.pdf](https://www.comsys.rwth-aachen.de/fileadmin/papers/2020/2020-roepert-opcua-security.pdf) Assessing the Security of OPC UA Deployments, 2020
3.  **[^](https://en.wikipedia.org/wiki/OPC_Unified_Architecture#cite_ref-3 "Jump up")** Mahnke, Wolfgang; Leitner, Stefan-Helmut [https://library.e.abb.com/public/75d70c47268d78bfc125762d00481f78/56-61%203M903\_ENG72dpi.pdf](https://library.e.abb.com/public/75d70c47268d78bfc125762d00481f78/56-61%203M903_ENG72dpi.pdf) OPC Unified Architecture - The future standard for communication and information modeling in automation\], 3/2009 [ABB Review 3/2009, page 56-61](http://www.abb.com/abbreview)
4.  **[^](https://en.wikipedia.org/wiki/OPC_Unified_Architecture#cite_ref-4 "Jump up")** [https://opcfoundation.org/developer-tools/specifications-unified-architecture](https://opcfoundation.org/developer-tools/specifications-unified-architecture)
5.  **[^](https://en.wikipedia.org/wiki/OPC_Unified_Architecture#cite_ref-5 "Jump up")** [The world's smallest OPC UA server comes from Germany](https://www.hs-owl.de/init/en/aktuelles/news/news-detail/news/the-worlds-smallest-opc-ua-server-comes-from-germany.html)
6.  **[^](https://en.wikipedia.org/wiki/OPC_Unified_Architecture#cite_ref-6 "Jump up")** Leitner, Stefan-Helmut; Mahnke, Wolfgang [OPC UA – Service-oriented Architecture for Industrial Applications](http://pi.informatik.uni-siegen.de/stt/26_4/01_Fachgruppenberichte/ORA2006/07_leitner-final.pdf), 11/2006 [Softwaretechnik-Trends](http://pi.informatik.uni-siegen.de/stt/index.html) [ISSN](https://en.wikipedia.org/wiki/ISSN_(identifier) "ISSN (identifier)") [0720-8928](https://www.worldcat.org/search?fq=x0:jrnl&q=n2:0720-8928)
7.  **[^](https://en.wikipedia.org/wiki/OPC_Unified_Architecture#cite_ref-7 "Jump up")** Massaro, Simone [What is OPC UA and how does it affect your world?](http://www.plantengineering.com/index.php?id=1792&cHash=081010&tx_ttnews%5Btt_news%5D=35007), 5/15/2008 [planetengineering.com](http://www.plantengineering.com/)
8.  **[^](https://en.wikipedia.org/wiki/OPC_Unified_Architecture#cite_ref-8 "Jump up")** ["OPC Unified Architecture (UA) client and/or server functionality in any JVM-based project"](https://projects.eclipse.org/proposals/milo). Retrieved 22 August 2016.
9.  **[^](https://en.wikipedia.org/wiki/OPC_Unified_Architecture#cite_ref-9 "Jump up")** ["IEC Webstore for IEC 62541"](https://webstore.iec.ch/searchform&q=iec%2062541). Retrieved 1 June 2018.

## Literature\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=21 "Edit section: Literature")\]

-   Wolfgang Mahnke, Stefan-Helmut Leitner, Matthias Damm: _OPC Unified Architecture._ Springer Verlag 2009; [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [978-3-540-68898-3](https://en.wikipedia.org/wiki/Special:BookSources/978-3-540-68898-3 "Special:BookSources/978-3-540-68898-3")
-   Lange, J., Iwanitz, F., Burke, T. OPC From Data Access to Unified Architecture 2010; [ISBN](https://en.wikipedia.org/wiki/ISBN_(identifier) "ISBN (identifier)") [978-3-8007-3242-5](https://en.wikipedia.org/wiki/Special:BookSources/978-3-8007-3242-5 "Special:BookSources/978-3-8007-3242-5")

## External links\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Unified_Architecture&action=edit&section=22 "Edit section: External links")\]

-   [OPC Foundation](http://www.opcfoundation.org/)
-   [Introduction to OPC UA based on the open source open62541 SDK](http://open62541.org/doc/current/)
-   [CECILL-C Licensed OPC UA implementation](http://www.openopcua.org/)
-   [Cross platform OPC UA development and free cross platform clients (Windows, Linux, Android, iOS)](http://www.unified-automation.com/)
-   [Multiplatform OPC UA mySCADA running on Windows, Linux, MacOS, Android and iOS](http://www.myscada.org/)
-   [Ignition Native Java OPC UA Stack](http://www.inductiveautomation.com/products/ignitionopc)
-   [Introduction to OPC UA Address Space modelling](https://www.youtube.com/watch?v=pYOQA4atlRI)
-   [Node-OPCUA -OPC UA for nodejs - (MIT licence)](https://node-opcua.github.io/)
-   [OPC UA for Android devices](http://teslascada.com/)
-   [OPC Unified Architecture e-Book](http://www.commsvr.com/UAModelDesigner/Index.aspx)
-   [Open Source OPC UA SDK for Java](https://github.com/digitalpetri/opc-ua-sdk)
-   [The FreeOpcUa project implement an open-source (LGPL) OPC UA stack and associated tools.](https://freeopcua.github.io/)
-   [SDK for OPC UA (Java) and free client/server](http://www.prosysopc.com/)
-   [The OPC Programmer's Connection](http://www.opcconnect.com/ua.php)
-   [A Tale of Two Industrial IoT Standards: DDS and OPC UA](https://www.rtinsights.com/dds-opc-ua-industrial-iot-standards/)
-   [Woopsa - a protocol bringing functionalities similar to OPC UA to the Web](https://www.woopsa.org/)
-   [OPC UA Gateway for Industry 4.0](http://www.opc-router.com/)
-   [S2OPC open source safe OPC UA](https://www.s2opc.com/)
-   [A complete guide on OPC UA](https://www.kalycito.com/opcua/)
-   [Learn OPC UA online](https://kalycito.teachable.com/)