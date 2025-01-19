#Technology #Oracle #Integration #OIC #HA_DR 

# OIC Import / Export Feature
With the August 2020 release, Oracle Integration now includes a great new feature that allows you to export all the design-time meta-data from your instance into a single export file stored on OCI Object Storage. That same export file can then be imported into a different instance of Oracle Integration, effectively giving you a complete migration and/or backup capability. There are several options that can be chosen when configuring an export job depending on your intended use and we will explore those a bit later on.

I have also included a _Further Reading_ section at the bottom of this guide that will take you to the relevant documentation for this UI and it’s underlying API’s – should you wish to automate these activities in your devops processes.

This guide will walk you through these major steps:

1.  Create a storage bucket in OCI Object Storage
2.  Create an OCI Auth Token for accessing to your storage bucket
3.  Configure your storage bucket for use in Oracle Integration source instance
4.  Create an Export Job in Oracle Integration source instance
5.  Configure your storage bucket for use in Oracle Integration target instance
6.  Create an Import Job in Oracle Integration target instance

## Create a storage bucket in OCI Object Storage

Before we get started creating export jobs, we must create a storage bucket in OCI and then configure secure access so that Oracle Integration can connect to your storage bucket. Let’s first go and create a storage bucket in OCI and then we will come back to Oracle Integration to configure and use it.

First, open your OCI console for your cloud account. Next, locate “Object Storage” in the left sidebar menu and select the sub menu “Object Storage” i.e. Object Storage  Object Storage

[![](https://blogs.oracle.com/content/published/api/v1.1/assets/CONT41F7D56008AD46A893B49AC81EAEA563/Medium?cb=_cache_2ce1&format=jpg&channelToken=ab27f6bb69794bb08279a9ba941a2cd1)](https://blogs.oracle.com/content/published/api/v1.1/assets/CONT34A73897989646A5AB1AC24C36FF21D4/Medium?cb=_cache_2ce1&format=jpg&channelToken=ab27f6bb69794bb08279a9ba941a2cd1)

This will open a page that lists all the storage buckets you have in the current compartment. Note in the image below, I have already selected a compartment called “steve\_tindall”. You should select an appropriate compartment for your storage buckets.

![](https://blogs.oracle.com/content/published/api/v1.1/assets/CONTD5B8DC499B6846F0897A74E0D7C310D5/Medium?cb=_cache_2ce1&format=jpg&channelToken=ab27f6bb69794bb08279a9ba941a2cd1)

Click the “Create Bucket” button and fill in the required information. I took all the defaults except for the name. From the screenshot above you can see that I created a bucket called “oicmigrations”.

Next, select you bucket from the list to open the bucket details screen.

![](https://blogs.oracle.com/content/published/api/v1.1/assets/CONT0CA540DC845F4AE1B3B89C79037954F3/Medium?cb=_cache_2ce1&format=jpg&channelToken=ab27f6bb69794bb08279a9ba941a2cd1)

**Important Point!**

From here you can see that you have created a new bucket and that bucket is empty. At this point we need to **take note of the namespace for your bucket.** You will need this later on when configuring the Oracle Integration Import/Export UI. I suggest copying this text, along with the bucket name now, and pasting it into a text document for later use.

## Create an OCI Auth Token for accessing to your storage bucket

## Next we need to create a security token that is required by OCI when you access your storage bucket via an API. Oracle Integration is going to use the OCI Storage Service API’s to read and write files to your bucket, so we need to have this Auth Token ready to go.

To create an Auth Token, click on your Avatar in the top right of the OCI console and select your username under the heading “Profile” in the menu. 

![](https://blogs.oracle.com/content/published/api/v1.1/assets/CONT6100E4C3D0664F73A6142CAF3C9D4DB3/Medium?cb=_cache_2ce1&format=jpg&channelToken=ab27f6bb69794bb08279a9ba941a2cd1)

This will bring you to your profile page where you can create your Auth Token. On the left of the page under the heading “Resources” you will find several links including “Auth Tokens”, click on this to list your existing tokens.

![](https://blogs.oracle.com/content/published/api/v1.1/assets/CONT3726465FA6984576A3E70FA6D012C152/Medium?cb=_cache_2ce1&format=jpg&channelToken=ab27f6bb69794bb08279a9ba941a2cd1)

Click the “Generate Token” button to create a new token. Give the token a description. I gave mine a description of “Import-Export Token”.

**Important Point!**

When you generate your token (see image below) **YOU MUST COPY** the token straight away. You will not be able to see this token or retrieve it ever again. I suggest you copy it straight away and paste it into a text document. You will need it in the next step.

![](https://blogs.oracle.com/content/published/api/v1.1/assets/CONT1F1ACE3F16F8401BBE9FC7233E859542/Medium?cb=_cache_2ce1&format=jpg&channelToken=ab27f6bb69794bb08279a9ba941a2cd1)

## Configure your storage bucket for use in Oracle Integration 

Now we have a storage bucket ready to go, but before we can run an export job in Oracle Integration, we need to connect our Integration instance to our storage bucket.

To do this, open you Oracle Integration instance homepage and the click on “Settings” in the left sidebar. Under the settings menu you will find “Storage”. This is where you configure you Oracle Integration instance to connect to your storage bucket.

![](https://blogs.oracle.com/content/published/api/v1.1/assets/CONT1768E214A14044C4996D96B07392E26D/Medium?cb=_cache_2ce1&format=jpg&channelToken=ab27f6bb69794bb08279a9ba941a2cd1)

On this page you need to fill in all four of the fields as follows:

-   **Name:**  Any name will do. I used the same name as my bucket – so “oicmigrations”
-   **Swift URL:** This is URL to your storage bucket. It is made up of the following:
    -   **Protocol, host and version:** I used [https://swiftobjectstorage.ap-sydney-1.oraclecloud.com/v1](https://swiftobjectstorage.ap-sydney-1.oraclecloud.com/v1) because my storage bucket was created in the Sydney data center. The best place to find this is in the URL of your OCI console. Look at the URL when you log into OCI and get the data center name from that. For example, you could replace “ap-sydney-1” with “us-ashburn-1”. In this case your URL would be [https://swiftobjectstorage.us-ashburn-1.oraclecloud.com/v1](https://swiftobjectstorage.us-ashburn-1.oraclecloud.com/v1)
    -   **Namespace:** This is the namespace value you copied from your storage bucket in step 1. If you failed to keep it in a text document as suggested, go back to your OCI console now and retrieve it.
    -   **Bucket Name:** This is the name you gave your bucket. In my case “oicmigrations”
    -   **My full URL:** [https://swiftobjectstorage.ap-sydney-1.oraclecloud.com/v1/<my-namespace>/oicmigrations](https://swiftobjectstorage.ap-sydney-1.oraclecloud.com/v1/%3cmy-namespace%3e/oicmigrations)
-   **Username:** This is your OCI username. If you are a federated user then you will most likely need to append “oracleidentitycloudservice” and a “/” to your actual username. For example, my full username to connect to the storage bucket is [oracleidentitycloudservice/steve.tindall@oracle.com](mailto:oracleidentitycloudservice/steve.tindall@oracle.com). If you use a different identity federator, enter its name instead.
-   **Password:** Pay attention here. **This IS NOT your OCI password** as it might seem. This is where you need to provide your Auth Token that you created in the previous step. Hopefully you saved your token as suggested and have it in a text document. If so, use that as your password. If not, , go back to OCI and regenerate a new token.

![](https://blogs.oracle.com/content/published/api/v1.1/assets/CONTD8A87D40887740BA8B14729B7E9A9835/Medium?cb=_cache_2ce1&format=jpg&channelToken=ab27f6bb69794bb08279a9ba941a2cd1)

Once you see the green banner appear saying that you have saved the storage bucket config successfully, you are good to move onto the next step.

## Create an Export Job in Oracle Integration 

Now we can finally configure the export job in Oracle Integration. Under the settings menu in the left sidebar you will find the Import/Export UI.

![](https://blogs.oracle.com/content/published/api/v1.1/assets/CONT8C00868FC65E46629B2AA6F8D8E9FE8B/Medium?cb=_cache_2ce1&format=jpg&channelToken=ab27f6bb69794bb08279a9ba941a2cd1)

To create a new export job, click the “Export” button in the top right corner of the Import/Export screen. You will see a configuration drawer slide out from the right side of the page.

Coincidently, this new slide-out draw feature of the UI is now used throughout the whole Oracle Integration UI for these types of configuration tasks.

The required information to create a job is simple and quite self-explanatory. You need to provide a **Job Name,** choose whether to include **security** **artefacts**, and a **Description.** You will also note that the storage bucket name you defined in the Storage configuration UI is listed here indicating that this is the target location for this export job. See the image below for reference.

![](https://blogs.oracle.com/content/published/api/v1.1/assets/CONTAEF66E46A598455BAA786C1095B3CF72/Medium?cb=_cache_2ce1&format=jpg&channelToken=ab27f6bb69794bb08279a9ba941a2cd1)

The security artefacts that will be exported with your meta-data are as follows:

-   Security policies
-   Security credentials (for connections)
-   Customer certificates
-   Application role memberships (for Processes)

Once you have completed all the fields, click the “Start Export Job” button. The export will take anywhere from 3 to 15 minutes to complete.

Once completed, you can check that the export file was generated successfully by looking at your bucket in the OCI console. See image below showing the zip file created in my “oicmigrations” bucket called “Steve-Blog-Export.zip”. **Note** that during the export process you will see several temporary files written to the storage bucket. Do not delete or move these files. The export process generates many files during its operations and then finally puts them all in one resulting zip file with the name of your export job. Only once you see this file can you use it correctly.

![](https://blogs.oracle.com/content/published/api/v1.1/assets/CONTD5E524AA431E47AFBAF2A853896487C9/Medium?cb=_cache_2ce1&format=jpg&channelToken=ab27f6bb69794bb08279a9ba941a2cd1)

## Create an Import Job in Oracle Integration

We are now onto the final step in this guide. Let’s take our export file and import it into our target Oracle Integration instance.

Before we can do that though we need to configure your target instance to read the storage bucket just like we did in the first instance. Following the same steps, configure your target instance using the fields on the Storage page under Settings in the left sidebar.

Next, click “Import/Export” in the left sidebar. You should see an empty list of import jobs (unless someone else in your company has already run an import).

![](https://blogs.oracle.com/content/published/api/v1.1/assets/CONT4B58C7E24B8B43A19F5EBE039BEF81F8/Medium?cb=_cache_2ce1&format=jpg&channelToken=ab27f6bb69794bb08279a9ba941a2cd1)

Click the “Import” button in the top right of the page. You will see a configuration drawer slide out from the right side of the screen. Here you can configure the options for importing an export file into your Oracle Integration instance. There are several options for importing into your instance. These are explained below.

![](https://blogs.oracle.com/content/published/api/v1.1/assets/CONT6FCBDD9F6BCD4582B60BCA2A0D77F4B8/Medium?cb=_cache_2ce1&format=jpg&channelToken=ab27f6bb69794bb08279a9ba941a2cd1)

The different import options allow you to control the state of the integrations and processes after the import job completes. The simplest option is to tick all options. If you tick all options the import job will do the following:

-   **Import**: Import all integrations and process and related artefacts like connections look-ups, decision rules etc.
-   **Include security artefacts**: All connections will be created with security credentials in place and ready to connect
-   **Activate**: Integrations that were active in the source instance will be activated in the target after the import completes
-   **Start Schedules**: Any scheduled integrations that were active in the source instance will be running (activated according to their schedule) in the target instance.

**Important Point!**

It is important to note that you can execute an import without choosing Activate or Start Schedules. This is useful if you know you need to change some of the endpoints in your connections (say from test systems to production systems) before you want them to be active. If you are using the import/export tool, for example, to move integrations from a test instance to a production instance, you might want to follow a sequence similar to this:

1.  Run the import WITHOUT selecting Activate or Start Schedules
2.  Modify the connections of the recently imported integrations so that their endpoints and/or credential information point to your production systems
3.  Rerun the import but this time WITHOUT the import option i.e. just the Activate and Start Schedule options.

This third step will cause the integrations in the in the export file (which are now already in your target instance as well) to be activated and to have their schedules started without replacing their meta-data or updating their respective connection credentials.

Lastly, you can check the status of you job, for both import and exports, by clicking on the job name in the Import/Export UI. This will expand the list with details of the job and it current status. It the image below, you can see that for my job, the Process component of the export has completed but the integration component is still running. You can also see the overall status of the job next to the job name.

![](https://blogs.oracle.com/content/published/api/v1.1/assets/CONT9C8BA57481A4476BB24FEFF8DA387411/Medium?cb=_cache_2ce1&format=jpg&channelToken=ab27f6bb69794bb08279a9ba941a2cd1)

Finally, if you need to debug a problem, you can download a log of what was exported. You will find this download icon next to the job name ONLY AFTER the job has completed. This will download a full report of the import or export job.

## Further Reading

The documentation for these new features can be found here: [https://docs.oracle.com/en/cloud/paas/integration-cloud/oracle-integration-oci/import-and-export-instances.html](https://docs.oracle.com/en/cloud/paas/integration-cloud/oracle-integration-oci/import-and-export-instances.html)

If you would like to automate this export and import process, so that it could be included in your automated devops processes or your CI/CD pipelines for example, you can call the underlying API's in Oracle Integration server by following this documentation in the admin guide: [https://docs.oracle.com/en/cloud/paas/integration-cloud/integration-cloud-auton/export-integration-and-process-design-time-metadata-instances.html](https://docs.oracle.com/en/cloud/paas/integration-cloud/integration-cloud-auton/export-integration-and-process-design-time-metadata-instances.html)

![](https://blogs.oracle.com/content/published/api/v1.1/assets/CONT66B0893DDAA249A69DEDBBE4B33562DE/Thumbnail?cb=_cache_2ce1&format=jpg&channelToken=ab27f6bb69794bb08279a9ba941a2cd1)

#### Steve Tindall

##### Director, Product Management, Oracle Integration

<p>Steve Tindall is currently part of the Oracle Integration Product Management team.&nbsp;</p> <p>He has over 25 years of business and technical industry experience including founding his own integration and java performance management services business in early years of the 2000&#39;s. He has experience on the implementation side of things delivering large consulting projects in the areas of distributed computing, application performance management, and enterprise application Integration.</p> <p>Has has also held several business roles in both sales and sales management as well as technical sales and pre-sales roles for companies including Open Environment Corporation, Borland, BEA Systems and Oracle.&nbsp;</p>

Show more