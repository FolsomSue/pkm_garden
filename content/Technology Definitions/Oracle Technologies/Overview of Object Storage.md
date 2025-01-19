#Oracle #definition 
The Oracle Cloud Infrastructure Object Storage service is an internet-scale, high-performance storage platform that offers reliable and cost-efficient data durability. The Object Storage service can store an unlimited amount of unstructured data of any content type, including analytic data and rich content, like images and videos.

With Object Storage, you can safely and securely store or retrieve data directly from the internet or from within the cloud platform. Object Storage offers multiple [management interfaces](https://docs.oracle.com/en-us/iaas/Content/Object/Concepts/objectstorageoverview.htm#accessways) that let you easily manage storage at scale. The elasticity of the platform lets you start small and scale seamlessly, without experiencing any degradation in performance or service reliability.

Object Storage is a regional service and is not tied to any specific compute instance. You can access data from anywhere inside or outside the context of the Oracle Cloud Infrastructure, as long you have internet connectivity and can access one of the [Object Storage endpoints](https://docs.oracle.com/iaas/api/#/en/objectstorage/latest/). Authorization and resource limits are discussed later in this topic.

Oracle Cloud Infrastructure supports multiple [storage tiers](https://docs.oracle.com/en-us/iaas/Content/Object/Concepts/understandingstoragetiers.htm#understanding_object_storage_tiers) that offer cost and performance flexibility. Standard is the default storage tier for Object Storage buckets.

Object Storage also supports private access from Oracle Cloud Infrastructure resources in a VCN through a _service gateway_. A service gateway allows connectivity to the Object Storage public endpoints from private IP addresses in private subnets. For example, you can back up DB systems to an Object Storage bucket over the Oracle Cloud Infrastructure backbone instead of over the internet. You can optionally use IAM policies to control which VCNs or ranges of IP addresses can access Object Storage. See [Access to Oracle Services: Service Gateway](https://docs.oracle.com/en-us/iaas/Content/Network/Tasks/servicegateway.htm#Access_to_Oracle_Services_Service_Gateway) for details.

Object Storage is Always Free eligible. For more information about Always Free resources, including capabilities and limitations, see [Oracle Cloud Infrastructure Free Tier](https://docs.oracle.com/en-us/iaas/Content/FreeTier/freetier.htm#Oracle_Cloud_Infrastructure_Free_Tier).

## Object Storage Resources

Use the following Object Storage resources to store and manage data. Authorization and resource limits are discussed later in this topic.

### Buckets

Buckets are logical containers for storing objects. Users or systems create buckets as needed [within a region](https://docs.oracle.com/en-us/iaas/Content/Identity/Tasks/managingregions.htm#regionalresources). A bucket is associated with a single **compartment**  that has **policies**  that determine what actions a user can perform on a bucket and on all the objects in the bucket.

### Objects

Any type of data, regardless of content type, is stored as an object. An object is composed of the object itself and metadata about the object. Each object is stored in a bucket.

### Namespace

Object Storage namespace serves as the top-level container for all buckets and objects. At account creation time, each Oracle Cloud Infrastructure tenant is assigned one unique system-generated and immutable Object Storage namespace name. The namespace spans all compartments within a region. You control bucket names, but those bucket names must be unique within a namespace. While the namespace is region-specific, the namespace name itself is the same in all regions. See [Understanding Object Storage Namespaces](https://docs.oracle.com/en-us/iaas/Content/Object/Tasks/understandingnamespaces.htm#Understanding_Object_Storage_Namespaces) for more details, including information about older tenancy names, illustrative examples of namespaces, and how to obtain your namespace string.

### Compartment

A compartment is the primary building block used to organize your cloud resources. When your tenancy is provisioned, a root compartment is created for you. You can then create compartments under your root compartment to organize your resources. You control access by creating policies that specify what actions groups of users can take on the resources in those compartments. An Object Storage bucket can only exist in one compartment.

## Authentication and Authorization

Each service in Oracle Cloud Infrastructure integrates with IAM for authentication and authorization, for all interfaces (the Console, SDK or CLI, and REST API). IAM also manages user credentials for things like API signing keys, auth tokens, and customer secret keys for Amazon S3 Compatibility API. See [User Credentials](https://docs.oracle.com/en-us/iaas/Content/Identity/Concepts/usercredentials.htm#User_Credentials) for details.

An administrator in your organization needs to set up **groups** , **compartments** , and **policies**  that control which users can access which services, which resources, and the type of access. For example, the policies control who can create users and groups, create buckets, download objects, and manage Object Storage\-related policies and rules. For more information, see [Getting Started with Policies](https://docs.oracle.com/en-us/iaas/Content/Identity/Concepts/policygetstarted.htm#Getting_Started_with_Policies). For specific details about writing policies for each of the different services, see the [Policy Reference](https://docs.oracle.com/en-us/iaas/Content/Identity/policyreference/policyreference.htm). For specific details about writing policies for Object Storage, see [Details for Object Storage, Archive Storage, and Data Transfer](https://docs.oracle.com/en-us/iaas/Content/Identity/Reference/objectstoragepolicyreference.htm#Details_for_Object_Storage_Archive_Storage_and_Data_Transfer).

If you’re a regular user (not an administrator) who needs to use the Oracle Cloud Infrastructure resources that your company owns, contact your administrator to set up a user ID for you. The administrator can confirm which compartment or compartments you should be using.