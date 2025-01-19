---
source: 
tags:
  - EDI
  - Integration
  - Data_Integration
  - B2B
---
An EDI document is comprised of data elements, segments and envelopes that are formatted according to the rules of a particular EDI standard.

When you create an EDI document, such as a purchase order, you must adhere to the strict formatting rules of the standard you are using. These rules define exactly where and how each piece of information in the document will be found. That way, when the EDI translator on the receiving computer reads an incoming EDI purchase order, it will immediately understand where to find the buyer’s company name, the purchase order number, the items being ordered, the price for each item, etc. Then, that data will be fed into the receiver’s order entry system in the proper internal format without requiring any manual order entry.

## EDI in printed formats

The graphic below shows a sample purchase order in printed form and how it would look once it’s translated into the [ANSI](https://www.edibasics.com/edi-resources/document-standards/ansi/) and [EDIFACT](https://www.edibasics.com/edi-resources/document-standards/edifact/) EDI formats.

[![Example of a purchase order showing invoice details, ANSI EDI and EDIFACT purchase order codes.](https://edibasics.com/wp-content/uploads/purchase-order.png)](https://www.edibasics.com/wp-content/uploads/purchase-order.png)

In the EDI language, a single business document, such as a purchase order, invoice or advance ship notice, is called a “transaction set” or “message.” And, a transaction set is comprised of data elements, segments and envelopes.

### What is a Data Element?

**The data elements in an EDI Transaction Set are the individual items of information within the document.**

For example, within many documents, such as the purchase order and invoice, you will find data elements such as city, state, country, item number, quantity and price.

Each data element in a transaction set is defined in the EDI Standard by the type of data it represents. For example, it would be important to distinguish numeric data from text data or calendar dates. The data element definition will describe:

-   Data type of numeric, alphanumeric, date or time
-   Minimum and maximum length
-   Code values, if applicable, that must be observed with a particular type of data. For example, if the data element is unit cost, you would use a currency code element as well to allow you to indicate what currency (e.g., US dollars or euros) is being used in the unit cost field

### What is a Segment?

**A segment in an EDI transaction set is a group of like data elements.**

If you were filling out information on a purchase order, you would expect to see groups of related data. For example, look at the diagram below of a paper purchase order in which only one item is being ordered. Note that there are four sections, each providing a different set of information:

[![Details of a purchase order detailing the PO number date, the buyer, item details and summary.](https://edibasics.com/wp-content/uploads/PO-sections.png)](https://www.edibasics.com/wp-content/uploads/PO-sections.png)

In an EDI document, each section is described by a particular segment. Below is the set of EDI segments that would describe the purchase order above when using the ANSI standard. Each segment begins with a segment ID (e.g., ST, BEG, N1) that describes the type of data elements that follows. The elements within each segment are separated by a data element separator, in this case the ‘\*’.

<table><tbody><tr><td><strong>ST*850*1001</strong></td><td>ST, to indicate start of a transaction set – in this case the 850 purchase order</td><td>&nbsp;</td></tr><tr><td><strong>BEG*00*SA*4768*65*20120930</strong></td><td>BEG, to indicate the beginning of the PO, specifically</td><td>(1)</td></tr><tr><td><strong>N1*SO*XYZ Company</strong></td><td>N1, a name segment</td><td>(2)</td></tr><tr><td><strong>N3*123 Main Street</strong></td><td>N3, to provide street address</td><td>&nbsp;</td></tr><tr><td><strong>N4*Fairview*CA*94168</strong></td><td>N4, to provide city/state/zip</td><td>&nbsp;</td></tr><tr><td><strong>PO1*1*100*EA*27.65**VN*331896-42</strong></td><td>PO1, to provide line item detail</td><td>(3)</td></tr><tr><td><strong>CTT*1*100</strong></td><td>CTT, to provide summary data for the PO</td><td>(4)</td></tr><tr><td><strong>SE*8*1001</strong></td><td>SE, to indicate the end of the PO</td><td>&nbsp;</td></tr></tbody></table>

For each type of business document, the [EDI standard documentation](https://www.edibasics.com/edi-resources/document-standards/) defines:

-   The segments that may be included and which ones are mandatory, optional and/or conditional (i.e. must be included only if another segment or element is included)
-   For each segment, the elements that may be included – for every piece of information in a paper document there is a corresponding EDI element. These elements are defined in the standards dictionary and each standard has its own dictionary
-   The required sequence of the segments and elements
-   How many times a segment may be repeated

Now, once all the segments are collected into a prescribed sequence, they form a complete electronic document, or transaction set. Next, the transaction sets must be put into envelopes in preparation for transmission to your partners. You can view a [sample EDI document](https://www.edibasics.com/edi-resources/sample-rfp/) to see how this is put into practice.

## What are EDI Envelopes?

**EDI document transmission uses a system of three “envelopes” to house your transaction sets – Message envelope, Group envelope and Interchange envelope.**

Just as paper business documents are sent in envelopes and it’s possible to mail many documents in a single envelope, EDI documents are exchanged using several envelopes.

-   Each transaction set is placed in its individual envelope
-   A group of transaction sets – e.g., a group of purchase orders – is placed in a group envelope. (The group envelope is mandatory in ANSI and optional in EDIFACT.)
-   All group envelopes being sent from one sender to one receiver are placed in an Interchange envelope

See the diagram below:

[![Cycle showing EDI envelopes from transaction set envelopes, to a group envelope, to an interchange envelope.](https://edibasics.com/wp-content/uploads/edi-envelope.png)](https://www.edibasics.com/wp-content/uploads/edi-envelope.png)

An envelope is formed by a pair of segments that define the beginning and end of the appropriate section. Using the [EDIFACT standard](https://www.edibasics.com/edi-resources/document-standards/edifact/) as the example, the Transaction Set Envelope uses the UNH and UNT segments, the Group Envelope uses the UNG and UNE segments and the Interchange Envelope uses the UNA/UNB and UNZ segments. In each case, the “S” indicates the “start” of the envelope and the “E” indicates the “end” of the envelope. The diagram below illustrates the three levels of envelopes that would surround a single EDI purchase order.

[![Example of an interchange envelope with the data from the group envelope and the message envelope.](https://edibasics.com/wp-content/uploads/edi-envelope-3-levels-1.png)](https://www.edibasics.com/wp-content/uploads/edi-envelope-3-levels-1.png)

### Continue Reading