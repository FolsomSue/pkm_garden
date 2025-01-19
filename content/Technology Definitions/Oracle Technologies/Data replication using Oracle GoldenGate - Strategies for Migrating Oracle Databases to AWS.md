#Oracle #definition #Replication 
[Oracle GoldenGate](https://www.oracle.com/integration/goldengate/) is a tool for real-time change data capture and replication. Oracle GoldenGate creates trail files that contain the most recently changed data from the source database, then pushes these files to the destination database. You can use Oracle GoldenGate to perform minimal downtime data migration. Oracle GoldenGate is a licensed software from Oracle. You can also use it for nearly continuous data replication. You can use Oracle GoldenGate with both Amazon RDS for Oracle, and Oracle Database running on Amazon EC2.

The following steps show how to migrate data using Oracle GoldenGate:

1.  The Oracle GoldenGate Extract process extracts all the existing data for the first load. Extract, Pump and Replicat process refers to the GoldenGate Integrated capture mode.
    
2.  The Oracle GoldenGate Pump process transports the extracted data to the Replicat process running in Amazon EC2.
    
3.  The Replicat process applies the data to the destination database.
    
4.  After the first load, the process runs continually to capture changed data and applies it to the destination database.
    

GoldenGate Replicat is a key part of the entire system. You can run it from a server in the source environment, but AWS recommends that you run the Replicat process in an Amazon EC2 instance within AWS for better performance. This Amazon EC2 instance is referred to as a _GoldenGate Hub_. You can have multiple GoldenGate Hubs, especially if you are migrating data from one source to multiple destinations.

**Reference architecture for Amazon EC2:**

**Reference architecture for RDS:**

## Setting up Oracle GoldenGate Hub on Amazon EC2

To create an Oracle GoldenGate Hub on Amazon EC2, create an Amazon EC2 instance with a full client installation of Oracle DBMS 12c version 12.2.0.3 and Oracle GoldenGate 12.3.1.4. Additionally, apply Oracle patch 13328193. For more information about installing GoldenGate, see the [Oracle GoldenGate documentation](https://docs.oracle.com/cd/E35209_01/index.htm).

This GoldenGate Hub stores and processes all the data from your source database, so make sure that there is enough storage available in this instance to store the trail files. It is a good practice to choose the largest instance type that your GoldenGate license allows. Use appropriate Amazon EBS storage volume types, depending on the database change rate and replication performance.

The following process sets up a GoldenGate Hub on an Amazon EC2 instance.

1.  Add the following entry to the `tnsname.ora` file to create an alias. For more information about the `tnsname.ora` file, see the [Oracle GoldenGate documentation](https://www.orafaq.com/wiki/Tnsnames.ora).
    
    ```
    $ cat /example/config/tnsnames.ora 
    TEST=
    
    (DESCRIPTION= 
      (ENABLE=BROKEN) 
      (ADDRESS_LIST=
    
        (ADDRESS=(PROTOCOL=TCP)(HOST=ec2-dns)(PORT=8200))
    
    ) (
    CONNECT_DATA=
    
        (SID=ORCL)
    
      )
    
    )
    ```
    
2.  Next, create subdirectories in the GoldenGate directory by using the Amazon EC2 command line shell and `ggsci`, the GoldenGate command interpreter. The subdirectories are created under the `gg` directory and include directories for parameter, report, and checkpoint files:
    
    ```
    prompt$ cd /gg 
    prompt$ ./ggsci
    
      GGSCI> CREATE SUBDIRS
    ```
    
3.  Create a `GLOBALS` parameter file using the Amazon EC2 command line shell. Parameters that affect all GoldenGate processes are defined in the `GLOBALS` parameter file. The following example creates the necessary file:
    
    ```
    prompt$ cd $GGHOME 
    prompt$ vi GLOBALS
    
    CheckpointTable oggadm1.oggchkpt
    ```
    
4.  Configure the manager. Add the following lines to the `GLOBALS` file, and then start the manager by using `ggsci`:
    
    ```
    PORT 8199
    PurgeOldExtracts ./dirdat/*, UseCheckpoints, MINKEEPDAYS
    ```