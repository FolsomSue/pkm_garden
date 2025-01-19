#Oracle #definition 

Storage Gateway is a cloud storage gateway that lets you connect your on-premises applications with Oracle Cloud Infrastructure. Applications that can write data to an NFS target can also write data to the Oracle Cloud Infrastructure Object Storage, without requiring application modification to uptake the REST APIs.

Install Storage Gateway by going to the [Storage Gateway download](https://www.oracle.com/downloads/cloud/oci-storage-gateway-downloads.html) page. Click the Download link for all supported platforms. This page contains a license agreement that you must accept. Then click the link to download a compressed archive file (approximately 1 GB) to your local host. Here you can use the SFTP tool of your choice to copy the tar archive into the `/tmp` folder of the host machine.

See [Installing Storage Gateway](https://docs.oracle.com/en-us/iaas/Content/StorageGateway/Tasks/installingstoragegateway.htm#installing "Describes how to install Storage Gateway on your host.") for complete installation instructions.

**Important**

Storage Gateway is the evolution of the Storage Software Appliance that was launched with Oracle Cloud Infrastructure Classic. By migrating to Oracle Cloud Infrastructure Object Storage, you are using Storage Gateway with its enhanced file-to-object transparency and improved scale and performance.

## Availability

The Storage Gateway service is available in all Oracle Cloud Infrastructure commercial regions. See [Regions and Availability Domains](https://docs.oracle.com/iaas/Content/General/Concepts/regions.htm) for the list of available regions, along with associated locations, region identifiers, region keys, and availability domains.

## Storage Gateway and Oracle Cloud Infrastructure Concepts

The following concepts are essential to working with Oracle Cloud Infrastructure Storage Gateway.

FILE SYSTEM

A Storage Gateway file system on a local host maps its files and directories to objects with the same names in a corresponding Oracle Cloud Infrastructure Object Storage bucket.

FILE SYSTEM CACHE

Storage Gateway's configurable file system cache enables asynchronous and optimized movement of data to the cloud. The file system cache serves as both a write buffer and a read cache for data storage and retrieval. The write buffer contains data that copied to the disk cache and queued for upload to Oracle Cloud Infrastructure. The read cache contains frequently retrieved data that’s accessible locally for read operations.

Proper file system cache configuration is critical to Storage Gateway performance. See [Configuring the Cache for File Systems](https://docs.oracle.com/en-us/iaas/Content/StorageGateway/Concepts/configuringcachefilesystems.htm#Configuring_the_Cache_for_File_Systems "Describes how to configure the cache for file systems using Storage Gateway.") for details.

METADATA

The metadata associated with a Storage Gateway file is stored as custom metadata for the corresponding object in Oracle Cloud Infrastructure Object Storage. Examples of file metadata include object id, creation date, modification date, size, and permissions. Storage Gateway caches all metadata for the file system locally.

NFSV4

NFS is an established and widely adopted distributed file system protocol for handling network storage. NFS lets client computers mount file systems on remote servers and access those remote file systems over the network as though they were local file systems. Storage Gateway performs the NFS to REST API translation needed to interact with Oracle Cloud Infrastructure Object Storage.

ORACLE CLOUD INFRASTRUCTURE

Oracle Cloud Infrastructure is a set of complementary cloud services that lets you build and run a wide range of applications and services in a highly available hosted environment. Oracle Cloud Infrastructure offers high-performance compute capabilities (as physical hardware instances) and storage capacity in a flexible overlay virtual network that is securely accessible from your on‑premises network.

TENANCY

A tenancy is a secure and isolated partition within Oracle Cloud Infrastructure where you can create, organize, and administer your cloud resources.

OBJECT STORAGE AND ARCHIVE STORAGE

Oracle Cloud Infrastructure offers two distinct storage tiers for you to store your unstructured data. Use the [Object Storage](https://docs.oracle.com/iaas/Content/Object/Concepts/objectstorageoverview.htm) **Standard** tier for data to which you need fast, immediate, and frequent access. Use the [Archive Storage](https://docs.oracle.com/iaas/Content/Archive/Concepts/archivestorageoverview.htm) service's **Archive** tier for data that you access infrequently, but which must be preserved for long periods of time. Both storage tiers use the same manageable resources (for example, objects and buckets). The difference is that when you upload a file to Archive Storage, the object is immediately archived. Before you can access an archived object, you must first restore the object to the Standard tier.

**Note**

In the Storage Gateway documentation, generic references to Object Storage encompass both the Standard and Archive storage tiers.

Both storage tiers are simple to use, perform well, and scale to an unlimited capacity.

bucket

An Object Storage bucket is a logical container for storing objects. A file system created in Storage Gateway maps to a corresponding bucket by the same name in Object Storage. A bucket is associated with a single Oracle Cloud Infrastructure **compartment** . The compartment has **policies**  that determine what actions a user can perform on the bucket the objects it contains.

object

An individual file or directory written to a Storage Gateway file system on an NFS share creates an identically named object in the target Object Storage bucket. An object is composed of the object itself and metadata about the object.

NAMESPACE

A logical entity that serves as a top-level container for all Oracle Cloud Infrastructure Object Storage buckets and objects. The namespace enables you to control bucket naming within your tenancy. Each tenancy has one unique and uneditable Object Storage [namespace](https://docs.oracle.com/iaas/Content/Object/Tasks/understandingnamespaces.htm) that is global, spanning all compartments and regions. Bucket names must be unique within your tenancy.

COMPARTMENT

A collection of Oracle Cloud Infrastructure\-related resources. Only users and groups with access permissions explicitly granted by an administrator can access the resources. Compartments help you organize resources and make it easier to control access to those resources. Oracle Cloud Infrastructure automatically creates a root compartment when a tenancy is provisioned. An administrator can then create more compartments within the root compartment and add access rules for those compartments. A bucket can exist in only one compartment.

## How Storage Gateway Works

Storage Gateway is installed in an Oracle Cloud Infrastructure compute instance or as a Linux Docker instance on one or more hosts in your on-premises data center. Applications store and retrieve objects from Oracle Cloud Infrastructure Object Storage through _file systems_ that you create in Storage Gateway.

Storage Gateway exposes an NFS mount point that can be mounted to any host that supports an NFSv4 client. The Storage Gateway mount point maps to an Object Storage bucket.

There is file-to-object transparency between Storage Gateway and Object Storage:

-   A Storage Gateway file system directory on a local host maps to a bucket with an identical name in Oracle Cloud Infrastructure Object Storage.
    
-   Any file written to a Storage Gateway file system is written as an object with the same name in the associated Object Storage bucket. The system stores associated file attributes as object metadata.
    
    The files written are uploaded to the associated Object Storage bucket asynchronously.
    
-   You can access Object Storage objects directly using native APIs, SDKs, third-party tools, the HDFS connector, and the Oracle Cloud Infrastructure CLI and Console. You use the **Refresh** operation in Storage Gateway to ingest any data that was added or modified directly in Object Storage.
    

Enterprise applications typically work with files in nested directories. Object Storage buckets, and the objects within those buckets, exist in a flat hierarchy. Storage Gateway flattens the directory hierarchy into nested object prefixes in Object Storage. See [Interacting With Object Storage](https://docs.oracle.com/en-us/iaas/Content/StorageGateway/Tasks/interactingwithobjectstorage.htm#Interacting_With_Object_Storage "Describes the Object Storage environment and how it interacts with a Storage Gateway.") for details.

## FastConnect

Learn about using FastConnect with Storage Gateway tasks.

You can use Oracle Cloud Infrastructure FastConnect with your Storage Gateway tasks. FastConnect provides an easy way to create a dedicated, private connection between your data center and Oracle Cloud Infrastructure. FastConnect provides higher-bandwidth options, and a more reliable and consistent networking experience compared to internet-based connections.

See [FastConnect](https://docs.oracle.com/iaas/Content/Network/Concepts/fastconnect.htm) for more information.

## Site-to-Site VPN

Learn about using Site-to-Site VPN with Storage Gateway tasks.

You can use Oracle Cloud Infrastructure Site-to-Site VPN with your Storage Gateway tasks. Site-to-Site VPN provides an IPSec connection between your on-premises network your virtual cloud network (VCN).

See [Site-to-Site VPN](https://docs.oracle.com/iaas/Content/Network/Tasks/managingIPsec.htm) for more information.

## Recommended Uses and Workloads

The following summarizes some of the ways that you can use Storage Gateway.

DATA TRANSFER

Use Storage Gateway to move data from your on-premises host to Oracle Cloud Infrastructure. Storage Gateway is not a replacement for general-purpose network attached storage (NAS), though it behaves similarly to NAS. Use Storage Gateway's integrated Cloud Sync feature to transfer and synchronize data to Oracle Cloud Infrastructure.

CLOUD TIERING

Use Storage Gateway to expand the capacity of on-premises storage solutions without capital expenditures. Configuring and connecting a Storage Gateway file system with a large cache to Oracle Cloud Infrastructure Object Storage provides unlimited scale to create a workflow in which files get automatically moved to the cloud and retrieved only on demand. Even though on-demand retrieval is slower than access to local storage, capital expenditures or changes to existing tools and software are not required.

BACKUPS

Use Storage Gateway to move files to Oracle Cloud Infrastructure Archive Storage as a cost-effective backup solution. You can move individual files and compressed or uncompressed ZIP or TAR archives. Storing secondary copies of data is an ideal use case for Storage Gateway.

ARCHIVAL

Storage Gateway is ideal for archive use cases.

DISASTER RECOVERY

Storage Gateway lets traditional applications move data to highly durable object storage. When you need to recover data, create a fresh instance of Storage Gateway to return the data from Object Storage.

## Uses and Workloads Not Supported

Storage Gateway does not support the following uses and workloads.

WINDOWS OPERATING SYSTEM

Storage Gateway does not currently support the Windows operating environment or Windows solutions.

**Note**

See [Object Storage](https://docs.oracle.com/iaas/Content/Object/Concepts/objectstorageoverview.htm) for more information on accessing Object Storage. You can also consult with your architecture team on solutions for working with Windows and Oracle Cloud Infrastructure Object Storage.

GENERAL-PURPOSE NETWORK STORAGE

Storage Gateway isn't a general-purpose storage filer and must not be used as a replacement for traditional network storage appliances.

FILE SYNC AND SHARE

Though Storage Gateway is an effective data mover, it’s not a replacement for file sync and share services. Evaluate Oracle services like Oracle Document Cloud service if you need file sync and share functionality.

CONTENT COLLABORATION

Storage Gateway does not support multiple Storage Gateway instances simultaneously reading from and writing to a single Object Storage bucket. Do not use Storage Gateway as a tool for distributed teams to collaborate on creating and managing content.

FREQUENTLY MODIFIED FILES

Do not use Storage Gateway if you expect your data to be modified frequently. Each time a file is modified and closed, Storage Gateway creates an updated version and uploads it to Object Storage as a new object. Frequently modified data results in substantial inefficiency, in terms of both bandwidth consumption and capacity utilization.

SYNCHRONOUS WORKLOADS

Storage Gateway asynchronously uploads files to your Object Storage bucket to offer eventual consistency. Files uploaded directly to an Object Storage bucket are not reflected back to the local Storage Gateway file system in real time. Click Refresh in the Storage Gateway management console or use autorefresh to ingest any data that was added or modified directly in Object Storage.

If autorefresh is configured at an aggressive interval, refreshes only occur when in-progress refreshes finish. That means the elapsed time between the beginning of any two successive refreshes is equal to the specified auto-refresh interval plus the time required to run a file system refresh, thus making the Storage Gateway NFS mount and Object Storage bucket contents asynchronous. Also, if any network connectivity issues exist, files uploaded directly to the bucket might not have synced.

See [Managing Storage Gateway File Systems](https://docs.oracle.com/en-us/iaas/Content/StorageGateway/Tasks/managingfilesystems.htm#Managing_File_Systems "Describes how to create and manage Storage Gateway file systems") for more information.

RENAMING LARGE DIRECTORY TREES

Renaming directories in the Storage Gateway works well for a small directory tree. However, renaming a parent directory with many children can be slow. The service updates the object ID of every corresponding child object in the object store to reflect the new path. If you do start a rename, ensure that the action finishes by monitoring the **Pending Uploads** field in the Storage Gateway user interface.

## Security Considerations

ADMIN PASSWORD

Because Storage Gateway administrators can create, modify, and delete file systems, follow these password guidelines:

-   Set a strong password.
-   Ensure that the password is secure.
-   Share passwords with others only on a need-to-know basis.

DOCKER

Storage Gateway runs inside a Docker container for security and isolation. Follow these Docker-related guidelines and recommendations:

-   Avoid or minimize Docker instance operations.
-   Avoid logging in to the Docker container. If there is a genuine requirement to log in to the Docker container, use extreme caution to avoid service disruption. Do not change the Docker configuration or the Docker instance unless instructed to do so by Oracle support personal.
-   Although the NFS protocol controls access to the file system from clients, Storage Gateway file systems are also locally mounted inside the Docker container. To prevent unauthorized access to file system data, ensure that a Docker container is accessible only by an administrator or an authorized user.
-   Configure the Docker host to limit user access to the Storage Gateway Docker container.
-   Files and directories in a Docker container are also visible in the Docker host - typically file systems and directories that are provisioned in the Docker host and mapped to the container. Set the appropriate ownership and modes to ensure that only an administrator or an authorized user can access these folders. We recommend the following:
    -   A dedicated Storage Gateway host.
    -   Limit who can access the Storage Gateway host.
    -   Set firewall rules to limit access to the Docker host and Docker container.
    -   Implement backup and retention policies for the files associated with Storage Gateway.

ACCESS CONTROL

Default file system export options are too permissive. Set more restrictive export options so that only trusted NFS clients can access the file system data and metadata. Modify the advanced file system settings for **NFS Allowed Hosts** and **NFS Export Options** to restrict access to a file system. In addition to NFS protocol security, you can also set up and configure a firewall on the host to further control access to the file system. UID/GID/modes control access to files and directories. Set the appropriate ownership mode to protect sensitive data.

OBJECT STORAGE

Files in a file system are uploaded to Oracle Cloud Infrastructure and stored as objects in an Object Storage bucket. Associated file attributes are stored as object metadata. Access control for Object Storage is different from access control for a traditional file system. Anyone with permission to read or modify any object in the bucket can read or modify all objects in the bucket. To protect sensitive data, set up Oracle Cloud Infrastructure IAM policies to limit who can access objects in the bucket.

Storage Gateway transfers data to Oracle Cloud Infrastructure using HTTPS, which encrypts data packets in flight between Storage Gateway and the cloud. Data written to Object Storage is always automatically encrypted in the cloud.

NETWORKING

Only use open network port access to networks that you trust. Oracle strongly recommends that you do not open network ports to the public internet. Instead, use a private connection to the machine hosting the Storage Gateway management console, for example a VPN or SSH local forward tunnel. See [Site-to-Site VPN](https://docs.oracle.com/iaas/Content/Network/Tasks/managingIPsec.htm) for more information.

Use the following syntax for SSH local forward tunnel:

```
ssh -L localHost:localPort:remoteHost:remotePort remoteHost
```

See [https://www.ssh.com/ssh/tunneling/example#local-forwarding](https://www.ssh.com/ssh/tunneling/example#local-forwarding) for more information.

## Limits on Storage Gateway Resources

See [Service Limits](https://docs.oracle.com/iaas/Content/General/Concepts/servicelimits.htm) for a list of applicable limits and instructions for requesting a limit increase.

Other limits include:

-   Ensure that the number of file systems per Storage Gateway doesn't exceed 10. For best performance, host each file system on a dedicated Storage Gateway.
-   Ensure that the number of objects stored in a Storage Gateway file system doesn’t exceed 100 million. For datasets that consist of more than 100 million objects, distribute the objects across multiple Storage Gateways.
-   Ensure that you configure adequate local storage for file system cache. Storage Gateway warns you if you have configured less than the recommended 500 GB.
-   The minimum amount of memory required for any Storage Gateway file system is 16 GB.
    
    -   File systems with up to 50 million files require 32 GB of memory.
    -   Large file systems with up to 100 million files require 64 GB of memory.
-   The number of files in the cache is limited to 20,000 regardless of the specified cache size in bytes.
-   To improve the efficiency of file ingestion, cloud upload operations, and to reduce the number of objects in the namespace, bin-pack or zip small files before writing them to Storage Gateway.

## Storage Gateway Release Notes

Release notes provide version-specific release information and important Storage Gateway issues. See [Storage Gateway Release Notes](https://docs.oracle.com/iaas/releasenotes/services/storage-gateway/) for more information.