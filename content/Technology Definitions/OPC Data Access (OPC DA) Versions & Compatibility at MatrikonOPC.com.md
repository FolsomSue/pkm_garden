## What is OPC DA?

OPC DA stands for [OPC Data Access](https://www.matrikonopc.com/opc-server/opc-data-access.aspx). It is an OPC Foundation specification that defines how real-time data can be transferred between a data source and a data sink (for example: a PLC and an HMI) without either of them having to know each other’s native protocol.

## Why is OPC DA so popular? How is it different than previous protocols?

The [OPC DA Client/Server architecture](https://www.matrikonopc.com/opc-server/opc-client-server.aspx) was the first architecture defined by the OPC Foundation. Before OPC DA, vendors’ products (devices, PLCs, HMIs) required any device or applications connecting to them to have a “custom driver” that translated between the third party connection and the product in question. There were many problems associated with custom driver based communications; some of these most common ones were: high cost, proprietary technology that tied users to a particular vendor, hard to configure and maintain because each custom driver had its own way of doing things, hard to keep up-to-date because of the constant release of new devices and applications. In contrast, OPC DA made it possible to connect to any real-time data source without a custom connector written specifically for the data-source/data-sink pair. Hence, reads and writes could be performed without the data-sink having to know the data-source’s native protocol or internal data structure.

## Is there only one OPC DA Specification?

Yes and no. While the OPC DA specification belongs to the OPC Foundation, it has gone through a number of revisions. The key ones are:

Year

Version

Comment

1996

1.0

Initial specification.

1997

DA 1.0a

**Data Access (DA)** name adopted to differentiate it from other specifications being concurrently developed.

1998

DA 2.0 - DA 2.05a

Numerous specification clarifications and modifications.

2003

DA 3.0

Further additions and modifications.

Given there are different versions of the OPC Data Access (OPC DA) specification, the key question is: are these versions backward compatible? For example: can an OPC DA 1.0a client communicate with an OPC DA 3.0 OPC Server? The answer is: depends.

## Data Access OPC Client and OPC Server backward compatibility

It is possible and recommended that vendors write OPC Clients and OPC Servers that are backwards compatible however, the reality is that backward compatibility is optional rather than mandatory which means: a number of vendors chose not to follow such advice (and continue to do so) and developed OPC DA Servers that only recognize one or two of the specifications but not all. What this means is that while these non-backward-compatible OPC Servers and OPC Clients still give users the advantage of using OPC… they only work with specific versions of the specification. The good news is that companies like MatirkonOPC not only develop fully backward-compatible OPC Servers, they also offer OPC data management products (ex. OPC Data Manager and OPC Security Gateway) that sit between the non-backward-compatible OPC Clients and OPC Servers to enable them to communicate with each other by translating between OPC DA revisions on the fly.

[![](https://www.matrikonopc.com/images/icons/translate.gif)](https://www.matrikonopc.com/main/translate.aspx)      [![](https://www.matrikonopc.com/images/icons/print.gif)](https://www.matrikonopc.com/opc-server/opc-data-access-versions.aspx?print=Y)