#Oracle #definition 
Replication provides protection from regional outages, aids in disaster recovery efforts, and addresses data redundancy compliance requirements. Maintaining multiple copies of data in regional locations closer to user access can also reduce latency.

This topic describes Object Storage replication and provides details on how to replicate the objects in one bucket to another bucket in the same region or a different region.

## About Object Storage Replication

Enabling Object Storage replication is as simple as creating a replication policy on the source bucket that identifies the region and the bucket to replicate to. After the replication policy is created, the destination bucket is read-only and updated only by replication from the source bucket. Objects uploaded to a source bucket after policy creation are asynchronously replicated to the destination bucket. Objects deleted from the source bucket after policy creation are automatically deleted from the destination bucket. Objects uploaded to a source bucket before policy creation are not replicated.

Replication overwrites any object in the destination bucket that has the same name as an object in the source bucket. A replicated object has the same name, metadata, ETag, and MD5 value as the object in the source bucket. The creation timestamp, modified timestamp, and archival state can be different, so these attributes are not replicated from the source.

## Required IAM Policies

To use Oracle Cloud Infrastructure, you must be granted security access in a **policy**  by an administrator. This access is required whether you're using the Console or the REST API with an SDK, CLI, or other tool. If you get a message that you don’t have permission or are unauthorized, verify with your administrator what type of access you have and which **compartment**  to work in.

If you're new to policies, see [Getting Started with Policies](https://docs.oracle.com/en-us/iaas/Content/Identity/Concepts/policygetstarted.htm#Getting_Started_with_Policies) and [Common Policies](https://docs.oracle.com/en-us/iaas/Content/Identity/Concepts/commonpolicies.htm#top).

**Important**

Replication does not work if you do not authorize the Object Storage service to replicate objects on your behalf. See [Service Permissions](https://docs.oracle.com/en-us/iaas/Content/Object/Tasks/usingreplication.htm#Service) for more information.

### User Permissions

You must have the required access to both the source and destination buckets when configuring replication. You must also have permissions to manage objects in the source and destination buckets.

For administrators:

-   You can create a policy that lets the specified IAM group manage Object Storage namespaces, buckets, and their associated objects in all compartments in the tenancy. For example, here is a simple user access policy that lets a StorageAdmins group do anything with the Object Storage service resources in the tenancy:
    
    ```
    Allow group StorageAdmins to manage object-family in tenancy
    ```
    
-   Alternatively, you can create policies that reduce the scope of access. For example, you can create the policies to let the StorageAdmins group manage buckets and objects in a compartment called ObjectStore in the tenancy:
    
    ```
    Allow group StorageAdmins to manage buckets in compartment ObjectStore
    Allow group StorageAdmins to manage objects in compartment ObjectStore
    ```
    

For more information about other alternatives for writing policies, see [Details for Object Storage, Archive Storage, and Data Transfer](https://docs.oracle.com/en-us/iaas/Content/Identity/Reference/objectstoragepolicyreference.htm#Details_for_Object_Storage_Archive_Storage_and_Data_Transfer).

### Service Permissions

Because Object Storage is a regional service, you must authorize the Object Storage service for each region carrying out replication on your behalf. For example, you might authorize the Object Storage service in region US East (Ashburn) to manage objects on your behalf. After you authorize the Object Storage service, you can replicate the objects in a bucket in US East (Ashburn) to a bucket in another region.

To determine the region identifier value of an Oracle Cloud Infrastructure region, see [Regions and Availability Domains](https://docs.oracle.com/en-us/iaas/Content/General/Concepts/regions.htm#top).

For administrators:

To enable replication, you must authorize the service to manage objects on your behalf:

-   For example, here is a service access policy that lets the Object Storage service do anything with the resources in the tenancy in the US West (Phoenix) region:
    
    ```
    Allow service objectstorage-us-phoenix-1 to manage object-family in tenancy
    ```
    
-   Alternatively, you can create policies that reduce the scope of access. For example, you can create a policy that lets the Object Storage service do anything with the resources in a compartment called ObjectStore in the US West (Phoenix) region:
    
    ```
    Allow service objectstorage-us-phoenix-1 to manage object-family in compartment ObjectStore
    ```
    
-   You can also create more restrictive policies that grant the individual permissions required for replication. For example:
    
    ```
    Allow service objectstorage-us-phoenix-1 to manage object-family in compartment ObjectStore where any {request.permission='BUCKET_READ', request.permission='BUCKET_UPDATE', request.permission='OBJECT_READ', request.permission='OBJECT_INSPECT', request.permission='OBJECT_CREATE', request.permission='OBJECT_OVERWRITE', request.permission='OBJECT_RESTORE', request.permission='OBJECT_DELETE'}
    ```
    

## Scope and Constraints

-   Replication policy creation does not automatically create a destination bucket. Create the destination bucket before creating the replication policy on the source bucket.
-   A source or destination bucket can be in the Standard ([Object Storage](https://docs.oracle.com/en-us/iaas/Content/Object/Concepts/objectstorageoverview.htm#Overview_of_Object_Storage)) or [Archive Storage](https://docs.oracle.com/en-us/iaas/Content/Archive/Concepts/archivestorageoverview.htm#Overview_of_Archive_Storage) tier.
-   Maximum of one replication policy per source bucket.
-   Maximum of one source for each replication destination bucket.
-   Maximum of one destination for each replication source bucket.
-   A destination bucket cannot also be a replication source. Chained replication is not supported.
-   After the replication policy is created, the destination bucket is read-only and updated only by replication from the source bucket. Objects uploaded to the source bucket are automatically replicated to the destination bucket. Objects deleted from the source bucket are automatically deleted from the destination bucket.
-   You cannot delete a replication destination bucket unless you stop replication and make the bucket writable again.

## Interaction Between Replication and Other Object Storage Features

This section describes some key things you need to know about the interaction between replication and other Object Storage features.

### Lifecycle Management

You can combine replication with [Lifecycle Management](https://docs.oracle.com/en-us/iaas/Content/Object/Tasks/usinglifecyclepolicies.htm#Using_Object_Lifecycle_Management) policies that manage the archiving and deletion of objects. Lifecycle policies must, however, honor the read-only properties of the replication destination bucket. A lifecycle policy that deletes objects from the replication destination bucket does not work. Carefully review and test any combination replication and lifecycle policies that you implement.

Here are examples of combination policies that might benefit you:

-   You can create a lifecycle policy on the source that deletes objects with certain file extensions after a specified number of days. The result of that deletion would also be reflected in the replication destination.
-   You can create a lifecycle policy on the destination that archives objects after a specified number of days. If you do not need immediate access to those objects, you could benefit from reduced storage costs.

### Server-Side Encryption Using Your Own Keys

Replication cannot replicate objects that have been encrypted with an SSE-C key. For more information, see [Using Your Own Keys for Server-Side Encryption](https://docs.oracle.com/en-us/iaas/Content/Object/Tasks/encryption.htm#Using_Your_Own_Keys_for_ServerSide_Encryption).

## Stopping Replication

Stopping replication can be initiated from either the replication source or the destination.

-   To stop replication from the source, delete the replication policy. Deleting a replication policy is permanent. You cannot recover a deleted policy. If you want to replicate to that target destination again, create a new policy.
-   To stop replication from the destination, make the destination bucket writable again. When you make the bucket writable, the destination bucket no longer accepts replication requests from the source. Replication status on the source changes from active to a client error state. If you want this destination to again be the target replication destination, delete the policy on the source bucket and create a new policy.

## Troubleshooting Replication

This topic provides troubleshooting solutions for issues you might encounter using replication.

## Using the Console

## Using the Command Line Interface (CLI)

For information about using the CLI, see [Command Line Interface (CLI)](https://docs.oracle.com/en-us/iaas/Content/API/Concepts/cliconcepts.htm#Command_Line_Interface_CLI). For a complete list of flags and options available for CLI commands, see the [Command Line Reference](https://docs.oracle.com/iaas/tools/oci-cli/latest/oci_cli_docs/).

## Using the API