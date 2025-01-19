#Technology #definition #ITSM #Standards  #DMTF #CIM 
# CIM Schema
<table><caption>CIM Schema</caption><tbody><tr><th scope="row">Status</th><td>Published</td></tr><tr><th scope="row">Organization</th><td><a href="https://en.wikipedia.org/wiki/Distributed_Management_Task_Force" title="Distributed Management Task Force">Distributed Management Task Force</a></td></tr><tr><th scope="row">Related standards</th><td><a href="https://en.wikipedia.org/wiki/Web-Based_Enterprise_Management" title="Web-Based Enterprise Management">WBEM</a>, <a href="https://en.wikipedia.org/wiki/Systems_Management_Architecture_for_Server_Hardware" title="Systems Management Architecture for Server Hardware">SMASH</a>, <a href="https://en.wikipedia.org/wiki/Storage_Management_Initiative_-_Specification" title="Storage Management Initiative - Specification">SMI-S</a></td></tr><tr><th scope="row">Website</th><td><span><a rel="nofollow" href="http://www.dmtf.org/standards/cim">www<wbr>.dmtf<wbr>.org<wbr>/standards<wbr>/cim</a></span></td></tr></tbody></table>

_CIM Schema_ is a computer specification, part of [Common Information Model](https://en.wikipedia.org/wiki/Common_Information_Model_(computing) "Common Information Model (computing)") standard, and created by the [Distributed Management Task Force](https://en.wikipedia.org/wiki/Distributed_Management_Task_Force "Distributed Management Task Force").[\[1\]](https://en.wikipedia.org/wiki/CIM_Schema#cite_note-1)

It is a conceptual diagram made of classes, attributes, relations between these classes and inheritances, defined in the world of [software](https://en.wikipedia.org/wiki/Software "Software") and [hardware](https://en.wikipedia.org/wiki/Computer_hardware "Computer hardware"). This set of objects and their relations is a conceptual framework for describing computer elements and organizing information about the managed environment.[\[2\]](https://en.wikipedia.org/wiki/CIM_Schema#cite_note-2)

This schema is the basis of other DMTF standards such as [WBEM](https://en.wikipedia.org/wiki/Web-Based_Enterprise_Management "Web-Based Enterprise Management"), [SMASH](https://en.wikipedia.org/wiki/Systems_Management_Architecture_for_Server_Hardware "Systems Management Architecture for Server Hardware") or [SMI-S](https://en.wikipedia.org/wiki/Storage_Management_Initiative_-_Specification "Storage Management Initiative - Specification") for storage management.

## Extensibility\[[edit](https://en.wikipedia.org/w/index.php?title=CIM_Schema&action=edit&section=1 "Edit section: Extensibility")\]

The CIM schema is object-based[\[3\]](https://en.wikipedia.org/wiki/CIM_Schema#cite_note-3) **·** [\[4\]](https://en.wikipedia.org/wiki/CIM_Schema#cite_note-4) and extensible, allowing manufacturers to represent their equipment using the elements defined in the core classes of CIM schema. For this, manufacturers provide software extensions called _providers_, which supplement existing classes by deriving them and adding new attributes.

## Examples of common core classes\[[edit](https://en.wikipedia.org/w/index.php?title=CIM_Schema&action=edit&section=2 "Edit section: Examples of common core classes")\]

-   _CIM\_ComputerSystem_[\[5\]](https://en.wikipedia.org/wiki/CIM_Schema#cite_note-5) for a [computer host](https://en.wikipedia.org/wiki/Host_(network) "Host (network)")
-   _CIM\_DataFile_:[\[6\]](https://en.wikipedia.org/wiki/CIM_Schema#cite_note-6) [Computer file](https://en.wikipedia.org/wiki/Computer_file "Computer file")
-   _CIM\_Directory_:[\[7\]](https://en.wikipedia.org/wiki/CIM_Schema#cite_note-7) [Files directory](https://en.wikipedia.org/wiki/Directory_(computing) "Directory (computing)")
-   _CIM\_DiskPartition_[\[8\]](https://en.wikipedia.org/wiki/CIM_Schema#cite_note-8) **·** :[\[9\]](https://en.wikipedia.org/wiki/CIM_Schema#cite_note-9) [disk partition](https://en.wikipedia.org/wiki/Disk_partitioning "Disk partitioning")
-   _CIM\_FIFOPipeFile_:[\[10\]](https://en.wikipedia.org/wiki/CIM_Schema#cite_note-10) [Named pipes](https://en.wikipedia.org/wiki/Named_pipe "Named pipe")
-   _CIM\_OperatingSystem_[\[11\]](https://en.wikipedia.org/wiki/CIM_Schema#cite_note-11) **·** :[\[12\]](https://en.wikipedia.org/wiki/CIM_Schema#cite_note-12) [Operating system](https://en.wikipedia.org/wiki/Operating_system "Operating system")
-   _CIM\_Process_:[\[13\]](https://en.wikipedia.org/wiki/CIM_Schema#cite_note-13) [Computer process](https://en.wikipedia.org/wiki/Process_(computing) "Process (computing)")
-   _CIM\_SqlTable_[\[14\]](https://en.wikipedia.org/wiki/CIM_Schema#cite_note-14) **·** :[\[15\]](https://en.wikipedia.org/wiki/CIM_Schema#cite_note-15) [Database table](https://en.wikipedia.org/wiki/Table_(database) "Table (database)")
-   _CIM\_SqlTrigger_:[\[16\]](https://en.wikipedia.org/wiki/CIM_Schema#cite_note-16) [Database trigger](https://en.wikipedia.org/wiki/Database_trigger "Database trigger")

## References\[[edit](https://en.wikipedia.org/w/index.php?title=CIM_Schema&action=edit&section=3 "Edit section: References")\]

1.  **[^](https://en.wikipedia.org/wiki/CIM_Schema#cite_ref-1 "Jump up")** [DMTF : CIM Schema](https://www.dmtf.org/documents/cim/cim-schema-2510)
2.  **[^](https://en.wikipedia.org/wiki/CIM_Schema#cite_ref-2 "Jump up")** [WBEM Solutions: CIM Schema](http://wbemsolutions.com/tutorials/CIM/cim-schema.html)
3.  **[^](https://en.wikipedia.org/wiki/CIM_Schema#cite_ref-3 "Jump up")** [CIM concepts: Object-Oriented Modeling](http://nets.ucar.edu/nets/intro/staff/siemsen/nandisc/dmtf/cim-2.5/tutorial/using/conc.html)
4.  **[^](https://en.wikipedia.org/wiki/CIM_Schema#cite_ref-4 "Jump up")** [Solaris WBEM Services Administrator's Guide: Common Information Model (CIM) Terms and Concepts](https://docs.oracle.com/cd/E19455-01/806-6468/6jfdjss9h/index.html)
5.  **[^](https://en.wikipedia.org/wiki/CIM_Schema#cite_ref-5 "Jump up")** [Class CIM\_ComputerSystem extends CIM\_System](https://schemas.dmtf.org/wbem/cim-html/2.49.0/CIM_ComputerSystem.html)
6.  **[^](https://en.wikipedia.org/wiki/CIM_Schema#cite_ref-6 "Jump up")** [Class CIM\_DataFile extends CIM\_LogicalFile](https://schemas.dmtf.org/wbem/cim-html/2.49.0/CIM_DataFile.html)
7.  **[^](https://en.wikipedia.org/wiki/CIM_Schema#cite_ref-7 "Jump up")** [Class CIM\_Directory extends CIM\_LogicalFile](https://schemas.dmtf.org/wbem/cim-html/2.49.0/CIM_Directory.html)
8.  **[^](https://en.wikipedia.org/wiki/CIM_Schema#cite_ref-8 "Jump up")** [CIM\_DiskPartition class](https://docs.microsoft.com/en-us/windows/desktop/cimwin32prov/cim-diskpartition)
9.  **[^](https://en.wikipedia.org/wiki/CIM_Schema#cite_ref-9 "Jump up")** [Class CIM\_DiskPartition extends CIM\_GenericDiskPartition](https://schemas.dmtf.org/wbem/cim-html/2.49.0/CIM_DiskPartition.html)
10.  **[^](https://en.wikipedia.org/wiki/CIM_Schema#cite_ref-10 "Jump up")** [Class CIM\_FIFOPipeFile extends CIM\_LogicalFile](https://schemas.dmtf.org/wbem/cim-html/2.51.0/CIM_FIFOPipeFile.html)
11.  **[^](https://en.wikipedia.org/wiki/CIM_Schema#cite_ref-11 "Jump up")** [CIM\_OperatingSystem class](https://docs.microsoft.com/en-us/windows/desktop/CIMWin32Prov/cim-operatingsystem)
12.  **[^](https://en.wikipedia.org/wiki/CIM_Schema#cite_ref-12 "Jump up")** [Class CIM\_OperatingSystem extends CIM\_EnabledLogicalElement](https://schemas.dmtf.org/wbem/cim-html/2.49.0/CIM_OperatingSystem.html)
13.  **[^](https://en.wikipedia.org/wiki/CIM_Schema#cite_ref-13 "Jump up")** [Class CIM\_Process extends CIM\_EnabledLogicalElement](https://schemas.dmtf.org/wbem/cim-html/2.49.0/CIM_Process.html)
14.  **[^](https://en.wikipedia.org/wiki/CIM_Schema#cite_ref-14 "Jump up")** [CIM\_SqlTable](https://users.suse.com/~kkaempf/cim/class/CIM_SqlTable.html)
15.  **[^](https://en.wikipedia.org/wiki/CIM_Schema#cite_ref-15 "Jump up")** [VMware vSphere 5.1 Documentation Center: Class CIM\_SqlTable](https://pubs.vmware.com/vsphere-51/index.jsp?topic=%2Fcom.vmware.cimsdk.smashref.doc%2Fclass_CIM_SqlTable.html)
16.  **[^](https://en.wikipedia.org/wiki/CIM_Schema#cite_ref-16 "Jump up")** [VMware CIM SMASH/Server Management API Reference: Class CIM\_SqlTrigger](https://code.vmware.com/docs/5499/vmware-cim-smash-server-management-api-reference/doc/class_CIM_SqlTrigger.html)