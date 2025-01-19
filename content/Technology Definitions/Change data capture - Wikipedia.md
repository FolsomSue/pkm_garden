---
tags:
  - Data
  - definition
  - Databases
  - CDC
aliases:
  - Change Data Capture
  - CDC
---
# Change Data Capture (CDC)

In [databases](https://en.wikipedia.org/wiki/Database "Database"), **change data capture** (**CDC**) is a set of software [design patterns](https://en.wikipedia.org/wiki/Design_pattern_(computer_science) "Design pattern (computer science)") used to determine and track the data that has changed (the "deltas") so that action can be taken using the changed data. The result is a **delta-driven [dataset](https://en.wikipedia.org/wiki/Dataset "Dataset")**.

CDC is an approach to [data integration](https://en.wikipedia.org/wiki/Data_integration "Data integration") that is based on the identification, capture and delivery of the changes made to enterprise data sources.

CDC occurs often in [data-warehouse](https://en.wikipedia.org/wiki/Data_warehouse "Data warehouse") environments since capturing and preserving the state of data across time is one of the core functions of a data warehouse, but CDC can be utilized in any database or data repository system.

## Methodology\[[edit](https://en.wikipedia.org/w/index.php?title=Change_data_capture&action=edit&section=1 "Edit section: Methodology")\]

System developers can set up CDC mechanisms in a number of ways and in any one or a combination of system layers from application logic down to physical storage.

In a simplified CDC context, one computer system has data believed to have changed from a previous point in time, and a second computer system needs to take action based on that changed data. The former is the source, the latter is the target. It is possible that the source and target are the same system physically, but that would not change the design pattern logically. Multiple CDC solutions can exist in a single system.

### Timestamps on rows\[[edit](https://en.wikipedia.org/w/index.php?title=Change_data_capture&action=edit&section=2 "Edit section: Timestamps on rows")\]

Tables whose changes must be captured may have a column that represents the time of **last** change. Names such as LAST\_UPDATE, LAST\_MODIFIED, etc. are common. Any row in any table that has a timestamp in that column that is more recent than the last time data was captured is considered to have changed.

Timestamps on rows are also frequently used for [optimistic locking](https://en.wikipedia.org/wiki/Optimistic_locking "Optimistic locking") so this column is often available.

### Version numbers on rows\[[edit](https://en.wikipedia.org/w/index.php?title=Change_data_capture&action=edit&section=3 "Edit section: Version numbers on rows")\]

Database designers give tables whose changes must be captured a column that contains a version number. Names such as VERSION\_NUMBER, etc. are common.

One technique is to mark each changed row with a version number. A current version is maintained for the table, or possibly a group of tables. This is stored in a supporting construct such as a reference table. When a change capture occurs, all data with the latest version number is considered to have changed. Once the change capture is complete, the reference table is updated with a new version number.

(Do not confuse this technique with row-level versioning used for [optimistic locking](https://en.wikipedia.org/wiki/Optimistic_locking "Optimistic locking"). For optimistic locking each row has an independent version number, typically a sequential counter. This allows a process to atomically update a row and increment its counter only if another process has not incremented the counter. But CDC cannot use row-level versions to find all changes unless it knows the original "starting" version of every row. This is impractical to maintain.)

### Status indicators on rows\[[edit](https://en.wikipedia.org/w/index.php?title=Change_data_capture&action=edit&section=4 "Edit section: Status indicators on rows")\]

This technique can either supplement or complement timestamps and versioning. It can configure an alternative if, for example, a status column is set up on a table row indicating that the row has changed (e.g., a boolean column that, when set to true, indicates that the row has changed). Otherwise, it can act as a complement to the previous methods, indicating that a row, despite having a new version number or a later date, still shouldn't be updated on the target (for example, the data may require human validation).

### Time/version/status on rows\[[edit](https://en.wikipedia.org/w/index.php?title=Change_data_capture&action=edit&section=5 "Edit section: Time/version/status on rows")\]

This approach combines the three previously discussed methods. As noted, it is not uncommon to see multiple CDC solutions at work in a single system, however, the combination of time, version, and status provides a particularly powerful mechanism and programmers should utilize them as a trio where possible. The three elements are not redundant or superfluous. Using them together allows for such logic as, "Capture all data for version 2.1 that changed between 2005-06-01 00:00 and 2005-07-01 00:00 where the status code indicates it is ready for production."

### Triggers on tables\[[edit](https://en.wikipedia.org/w/index.php?title=Change_data_capture&action=edit&section=6 "Edit section: Triggers on tables")\]

May include a [publish/subscribe](https://en.wikipedia.org/wiki/Observer_pattern "Observer pattern") pattern to communicate the changed data to multiple targets. In this approach, [triggers](https://en.wikipedia.org/wiki/Database_trigger "Database trigger") log events that happen to the transactional table into another queue table that can later be "played back". For example, imagine an Accounts table, when transactions are taken against this table, triggers would fire that would then store a history of the event or even the deltas into a separate queue table. The queue table might have schema with the following fields: Id, TableName, RowId, Timestamp, Operation. The data inserted for our Account sample might be: 1, Accounts, 76, 2008-11-02 00:15, Update. More complicated designs might log the actual data that changed. This queue table could then be "played back" to replicate the data from the source system to a target.

\[More discussion needed\]

An example of this technique is the pattern known as the [log trigger](https://en.wikipedia.org/wiki/Log_trigger "Log trigger").

<table><caption>Queue</caption><tbody><tr><th>Id</th><th>TableName</th><th>RowId</th><th>Timestamp</th><th>Operation</th></tr><tr><td>1</td><td>Accounts</td><td>76</td><td>2008-11-02 00:15</td><td>Update</td></tr></tbody></table>

### Event programming\[[edit](https://en.wikipedia.org/w/index.php?title=Change_data_capture&action=edit&section=7 "Edit section: Event programming")\]

Coding a change into an application at appropriate points is another method that can give intelligent discernment that data changed. Although this method involves programming vs. more easily implemented "dumb" triggers, it may provide more accurate and desirable CDC, such as only after a COMMIT, or only after certain columns changed to certain values - just what the target system is looking for.

### Log scanners\[[edit](https://en.wikipedia.org/w/index.php?title=Change_data_capture&action=edit&section=8 "Edit section: Log scanners")\]

Most database management systems manage a [transaction log](https://en.wikipedia.org/wiki/Transaction_log "Transaction log") that records changes made to the database contents and to [metadata](https://en.wikipedia.org/wiki/Metadata "Metadata"). By scanning and interpreting the contents of the database transaction log, one can capture the changes made to the database in a non-intrusive manner.

Using transaction logs for change data capture offers a challenge in that the structure, contents and use of a transaction log is specific to a database management system. Unlike data access, no standard exists for transaction logs. Most database management systems do not document the internal format of their transaction logs, although some provide programmatic interfaces to their transaction logs (for example: Oracle, DB2, SQL/MP, SQL/MX and SQL Server 2008).

Other challenges in using transaction logs for change data capture include:

-   Coordinating the reading of the transaction logs and the archiving of log files (database management software typically archives log files off-line on a regular basis).
-   Translation between physical storage formats that are recorded in the transaction logs and the logical formats typically expected by database users (e.g., some transaction logs save only minimal buffer differences that are not directly useful for change consumers).
-   Dealing with changes to the format of the transaction logs between versions of the database management system.
-   Eliminating uncommitted changes that the database wrote to the transaction log and later [rolled back](https://en.wikipedia.org/wiki/Rollback_(data_management) "Rollback (data management)").
-   Dealing with changes to the metadata of tables in the database.

CDC solutions based on transaction log files have distinct advantages that include:

-   minimal impact on the database (even more so if one uses [log shipping](https://en.wikipedia.org/wiki/Log_shipping "Log shipping") to process the logs on a dedicated host).
-   no need for programmatic changes to the applications that use the database.
-   low [latency](https://en.wikipedia.org/wiki/Latency_(engineering) "Latency (engineering)") in acquiring changes.
-   [transactional integrity](https://en.wikipedia.org/wiki/Data_integrity "Data integrity"): log scanning can produce a change stream that replays the original transactions in the order they were committed. Such a change stream include changes made to all tables participating in the captured transaction.
-   no need to change the database schema

## Confounding factors\[[edit](https://en.wikipedia.org/w/index.php?title=Change_data_capture&action=edit&section=9 "Edit section: Confounding factors")\]

As often occurs in complex domains, the final solution to a CDC problem may have to balance many competing concerns.

### Unsuitable source systems\[[edit](https://en.wikipedia.org/w/index.php?title=Change_data_capture&action=edit&section=10 "Edit section: Unsuitable source systems")\]

Change data capture both increases in complexity and reduces in value if the source system saves [metadata](https://en.wikipedia.org/wiki/Metadata "Metadata") changes when the data itself is not modified. For example, some [Data models](https://en.wikipedia.org/wiki/Data_model "Data model") track the user who last looked at but did not change the data in the same structure as the data. This results in [noise](https://en.wikipedia.org/wiki/Noise_(signal_processing) "Noise (signal processing)") in the Change Data Capture.

### Tracking the capture\[[edit](https://en.wikipedia.org/w/index.php?title=Change_data_capture&action=edit&section=11 "Edit section: Tracking the capture")\]

Actually tracking the changes depends on the data source. If the data is being persisted in a modern [database](https://en.wikipedia.org/wiki/Database "Database") then Change Data Capture is a simple matter of permissions. Two techniques are in common use:

-   Tracking changes using [database triggers](https://en.wikipedia.org/wiki/Database_trigger "Database trigger")
-   Reading the [transaction log](https://en.wikipedia.org/wiki/Transaction_log "Transaction log") as, or shortly after, it is written.

If the data is not in a modern database, CDC becomes a programming challenge.

### Push versus pull\[[edit](https://en.wikipedia.org/w/index.php?title=Change_data_capture&action=edit&section=12 "Edit section: Push versus pull")\]

-   **Push**: the source process creates a snapshot of changes within its own process and delivers rows downstream. The downstream process uses the snapshot, creates its own subset and delivers them to the next process.
-   **Pull**: the target that is immediately downstream from the source, prepares a request for data from the source. The downstream target delivers the snapshot to the next target, as in the push model.

### Alternatives\[[edit](https://en.wikipedia.org/w/index.php?title=Change_data_capture&action=edit&section=13 "Edit section: Alternatives")\]

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/4/46/Scd_model.png/220px-Scd_model.png)](https://en.wikipedia.org/wiki/File:Scd_model.png)

[Slowly changing dimension](https://en.wikipedia.org/wiki/Slowly_changing_dimension "Slowly changing dimension") (SCD) model example

Sometimes the [slowly changing dimension](https://en.wikipedia.org/wiki/Slowly_changing_dimension "Slowly changing dimension") is used as an alternative method.<sup id="cite_ref-1"><a href="https://en.wikipedia.org/wiki/Change_data_capture#cite_note-1">[1]</a></sup> CDC and SCD are similar in that both methods can detect changes in a data set. The most common forms of SCD are type 1 (overwrite), type 2 (maintain history) or 3 (only previous and current value). SCD 2 can be useful if history is needed in the target system. CDC overwrites in the target system (akin to SCD1), and is ideal when only the changed data needs to arrive at the target,<sup id="cite_ref-2"><a href="https://en.wikipedia.org/wiki/Change_data_capture#cite_note-2">[2]</a></sup> i.e. a _delta-driven [dataset](https://en.wikipedia.org/wiki/Dataset "Dataset")_.<sup>[<i><a href="https://en.wikipedia.org/wiki/Wikipedia:Citation_needed" title="Wikipedia:Citation needed"><span title="This claim needs references to reliable sources. (March 2023)">citation needed</span></a></i>]</sup>

## See also\[[edit](https://en.wikipedia.org/w/index.php?title=Change_data_capture&action=edit&section=14 "Edit section: See also")\]

-   [Referential integrity](https://en.wikipedia.org/wiki/Referential_integrity "Referential integrity")
-   [Slowly changing dimension](https://en.wikipedia.org/wiki/Slowly_changing_dimension "Slowly changing dimension")

## References\[[edit](https://en.wikipedia.org/w/index.php?title=Change_data_capture&action=edit&section=15 "Edit section: References")\]

1.  **[^](https://en.wikipedia.org/wiki/Change_data_capture#cite_ref-1 "Jump up")** Eroe, Erit (2015). _4ggg_. Rty.
2.  **[^](https://en.wikipedia.org/wiki/Change_data_capture#cite_ref-2 "Jump up")** [Slowly Changing Dimensions (SCD) vs Change Data Capture (CDC)](https://streamsets.com/blog/slowly-changing-dimensions-vs-change-data-capture/)

-   ([Ankorion, 2005](https://en.wikipedia.org/w/index.php?title=Ankorion,_2005&action=edit&redlink=1 "Ankorion, 2005 (page does not exist)")) ⇒ [Itamar Ankorion](https://en.wikipedia.org/w/index.php?title=Itamar_Ankorion&action=edit&redlink=1 "Itamar Ankorion (page does not exist)"). ([2005](https://en.wikipedia.org/wiki/2005 "2005")). “Change Data Capture Efficient ETL for Real-Time BI.” Information Management, 15(1).

## See also\[[edit](https://en.wikipedia.org/w/index.php?title=Change_data_capture&action=edit&section=16 "Edit section: See also")\]

-   [Oracle Data Integrator](https://en.wikipedia.org/wiki/Oracle_Data_Integrator "Oracle Data Integrator")