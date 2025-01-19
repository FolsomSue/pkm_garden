#Oracle #definition 
Oracle Cloud Infrastructure (OCI) [Object Storage](https://www.oracle.com/ca-en/cloud/storage/block-volumes/what-is-block-storage/vs-object-storage/) enables customers to securely store any type of data in its native format. With built-in redundancy, OCI Object Storage is ideal for building modern applications that require scale and flexibility, as it can be used to consolidate multiple data sources for analytics, backup, or archive purposes.

## Object Storage product features

-   [Object Storage for the enterprise](https://www.oracle.com/ca-en/cloud/storage/object-storage/#rc30p1)
-   [Highly available and durable](https://www.oracle.com/ca-en/cloud/storage/object-storage/#rc30p2)
-   [Strong security and monitoring](https://www.oracle.com/ca-en/cloud/storage/object-storage/#rc30p3)
-   [Easy to use, cost-effective](https://www.oracle.com/ca-en/cloud/storage/object-storage/#rc30p4)

#### Object Storage for the enterprise

##### Harness business value

Object Storage is increasingly used as a data lake, where businesses store their digital assets for processing by analytical frameworks and pipelines in order to harness business insight.

##### Integrated data protection

Enterprises store data and backups on OCI Object Storage, which runs on redundant hardware for built-in durability. Data integrity is actively monitored, with any corrupt data detected and healed by automatically recreating a copy of the data.

##### End-to-end visibility

OCI Object Storage provides a dedicated (non-shared) storage ‘namespace’ or container unique to each customer for all stored buckets and objects. This encapsulation provides end-to-end visibility and reduces the risk of exposed buckets. Customers can define access to meet exact organizational requirements and avoid the open bucket vulnerabilities associated with AWS S3’s shared global namespace. [Read more about AWS S3 data leaks](https://github.com/nagwww/s3-leaks).

##### Long-term, low-cost storage

For longer-term data storage needs like compliance and audit mandates and log data, OCI Archive Storage uses the same APIs as Object Storage for easy setup and integration but at one-tenth the cost. Data is monitored for integrity, automatically healed, and encrypted at rest.

## Oracle Object Storage use cases

-   ### Backup Oracle Database to OCI Object storage
    
    Oracle Recovery Manager (RMAN) is an Oracle Database client that performs Oracle database backup and recovery. It automates the administration of Oracle backup strategies and greatly simplifies backing up, restoring, and recovering database files. RMAN connects and authenticates to a database in the same way as SQL\*Plus connects to a database.
    
    [Learn more about backing up to Object Storage](https://www.oraclecloudadmin.com/2020/08/backup-oracle-database-to-oci-object.html)
    
-   ### Using Storage Gateway file management operations
    
    OCI Storage Gateway enables connecting on-premises applications with OCI. Applications that can write data to an NFS target can also write data to OCI Object Storage, without requiring application modification to uptake the REST APIs.
    
    [Learn more about using Storage Gateway](https://docs.cloud.oracle.com/en-us/iaas/Content/StorageGateway/Concepts/storagegatewayoverview.htm#overview)
    
-   ### Oracle Data Lake by Infosys
    
    The quantity of data produced worldwide in a single day has been estimated at 2.5 quintillion bytes. Infosys reveals their strategy for performing analytics on this growing mountain of data and the importance of storing data in a way that helps extract value out of it.
    
