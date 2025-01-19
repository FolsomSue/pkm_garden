#Technology #definition 
## Oracle ETL Phases

Oracle BI Applications [[ETL]] processes include the following phases:

-   [[SDE]]. SDE stands for Source Dependent Extract. In the first phase, SDE tasks extract data from the source system and stage it in staging tables. SDE tasks are source specific.
    
-   [[SIL]]. SIL stands for Source Independent Load. Load tasks transform and port the data from staging tables to base fact or dimension tables. SIL tasks are source independent.
    
-   [[PLP]]. PLP stands Post Load Process. PLP tasks are only executed after the dimension and fact tables are populated. A typical usage of a PLP task is to transform data from a base fact table and load it into an aggregate table. PLP tasks are source independent.