The **OPC Data Access** Specification is the first of a group of [specifications](https://en.wikipedia.org/wiki/Specification_(technical_standard) "Specification (technical standard)") known as the [OPC](https://en.wikipedia.org/wiki/OLE_for_process_control "OLE for process control") Classic Specifications.[\[1\]](https://en.wikipedia.org/wiki/OPC_Data_Access#cite_note-1)

OPC Data Access is a group of [client-server](https://en.wikipedia.org/wiki/Client-server_model "Client-server model") standards that provides specifications for communicating real-time data from [data acquisition](https://en.wikipedia.org/wiki/Data_acquisition "Data acquisition") devices such as [PLCs](https://en.wikipedia.org/wiki/Programmable_logic_controller "Programmable logic controller") to display and interface devices like [Human-Machine Interfaces](https://en.wikipedia.org/wiki/Human-machine_interface "Human-machine interface") (HMI), [SCADA](https://en.wikipedia.org/wiki/SCADA "SCADA") systems[\[2\]](https://en.wikipedia.org/wiki/OPC_Data_Access#cite_note-2) and also [ERP](https://en.wikipedia.org/wiki/Enterprise_resource_planning "Enterprise resource planning")/[MES](https://en.wikipedia.org/wiki/Manufacturing_execution_system "Manufacturing execution system") systems.[\[3\]](https://en.wikipedia.org/wiki/OPC_Data_Access#cite_note-3) The specifications focus on the continuous communication of data.

The OPC Data Access specification is also known as OPC DA. OPC DA deals only with real-time data and not historical data (for historical data you need to use [OPC Historical Data Access](https://en.wikipedia.org/wiki/OPC_Historical_Data_Access "OPC Historical Data Access"), or OPC HDA) or events (for Alarms and Events you need to use [OPC Alarms and Events](https://en.wikipedia.org/w/index.php?title=OPC_Alarms_and_Events&action=edit&redlink=1 "OPC Alarms and Events (page does not exist)"), or OPC AE). There are three attributes associated with OPC DA data. These are

1.  a value,
2.  the [quality](https://en.wikipedia.org/wiki/Quality_(business) "Quality (business)") of the value, and
3.  a [timestamp](https://en.wikipedia.org/wiki/Timestamp "Timestamp").

The OPC DA specification states that these three attributes have to be returned to an OPC client making a request. Therefore, if the data source is not capable of providing a timestamp, for example, the OPC DA server must create a timestamp.

The OPC Classic specifications are based on the [Microsoft](https://en.wikipedia.org/wiki/Microsoft "Microsoft") [COM](https://en.wikipedia.org/wiki/Component_Object_Model "Component Object Model") technology[\[4\]](https://en.wikipedia.org/wiki/OPC_Data_Access#cite_note-4) and define a [C](https://en.wikipedia.org/wiki/C_language "C language")/[C++](https://en.wikipedia.org/wiki/C%2B%2B "C++") [interface](https://en.wikipedia.org/wiki/Interface_(computing) "Interface (computing)"). A standard [Automation](https://en.wikipedia.org/wiki/OLE_Automation "OLE Automation") [wrapper](https://en.wikipedia.org/wiki/Wrapper_library "Wrapper library") interface is also defined for access from [Visual Basic](https://en.wikipedia.org/wiki/Visual_Basic "Visual Basic"), [Delphi](https://en.wikipedia.org/wiki/Embarcadero_Delphi "Embarcadero Delphi") and other automation-enabled languages.[\[5\]](https://en.wikipedia.org/wiki/OPC_Data_Access#cite_note-5) Several vendors offer [.NET](https://en.wikipedia.org/wiki/.NET_Framework ".NET Framework") toolkits to make the OPC interface accessible in .NET [applications](https://en.wikipedia.org/wiki/Application_software "Application software").

The newer OPC .NET ([OPC Xi](https://en.wikipedia.org/wiki/OPC_Xi "OPC Xi")) specification is based on WCF ([Windows Communication Foundation](https://en.wikipedia.org/wiki/Windows_Communication_Foundation "Windows Communication Foundation")) and defines a .NET interface with the functionality of the OPC Classic specifications OPC DA, OPC HDA and OPC AE (Alarms&Events).[\[6\]](https://en.wikipedia.org/wiki/OPC_Data_Access#cite_note-6)

The more recent [OPC Unified Architecture](https://en.wikipedia.org/wiki/OPC_Unified_Architecture "OPC Unified Architecture") allows the same functionality but offers platform independence and optionally complex information modelling capabilities.[\[7\]](https://en.wikipedia.org/wiki/OPC_Data_Access#cite_note-7)

## See also\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Data_Access&action=edit&section=1 "Edit section: See also")\]

-   [OPC Foundation](https://en.wikipedia.org/wiki/OPC_Foundation "OPC Foundation")
-   [Distributed Component Object Model](https://en.wikipedia.org/wiki/Distributed_Component_Object_Model "Distributed Component Object Model")
-   [OPC Unified Architecture](https://en.wikipedia.org/wiki/OPC_Unified_Architecture "OPC Unified Architecture")
-   [OPC Xi](https://en.wikipedia.org/wiki/OPC_Xi "OPC Xi")

## References\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Data_Access&action=edit&section=2 "Edit section: References")\]

## External links\[[edit](https://en.wikipedia.org/w/index.php?title=OPC_Data_Access&action=edit&section=3 "Edit section: External links")\]

-   [OPC Foundation Home Page](http://www.opcfoundation.org/)
-   [OPC Programmers' Connection](http://www.opcconnect.com/)