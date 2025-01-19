#Technology #definition  #Document_Management #Content_Management #Records_Management
## Document Management

[Document management](https://www.aiim.org/What-Is-Document-Imaging) is used to track and manage documents that are in process. More specifically, it’s used to manage the overall process of document creation, from inception through completion. It formalizes the document creation process to ensure transparency and accountability at every step in the process. It also serves to make the process more efficient by automating key tasks such as assembly, approval, and quality assurance steps.

For documents of any importance or complexity, this process will include the following steps:

1.  **Creation:** The document is created from a blank template. This results in the creation of the initial version.
    
2.  **Drafting:** The contents of the document are created by one or more contributors. Depending on the nature of the document, the contents could include typed text, formatting, images, hyperlinks, and any number of other elements.
    
    If the process uses multiple contributors, there needs to be a way to let them work on the document without inadvertently overwriting each other’s work. Different systems handle this in different ways:
    
    -   **Check-out and check-in:** The document management system allows a single user to check out the document, allowing other users to read it but not make any changes to it. Once the user is done making any changes, the document is checked in and is available for another user to check out. Every time the document is checked in with changes, a new version is created so everyone involved can see what has changed between each version. If a change is made that is not desired, the document can be rolled back to a previous version.
        
    -   **Co-authoring:** The document management system allows multiple users to work on a document simultaneously, but does internal locking within the document at some granular level. In SharePoint, for example, a Word document is locked at the paragraph level. This approach is not as widely supported.
        
3.  **Review:** This step generally involves having someone other than the content creator review the document for its overall content as well as things like grammar, spelling, document flow, the accuracy of tables and images, etc. The document management system can provide business rules to assign a review to a particular individual or role and ensure that the review is complete before the document can move on in the process.

4.  **Revision:** Once the review is complete, the draft is returned to the creator to make any necessary changes. This step is substantially similar to the drafting step above, including the creation of new versions.
    
5.  **Assembly:** Not every document requires this, but many more complex ones will. Consider, for example, a contract with different terms and conditions depending on where the work is to be performed. The document management system can ensure that there are terms and conditions included in the document and that they are the correct terms based on business rules.
    
6.  **Approval:** Some documents will have a formal approval process, perhaps ending with a signature of some sort. Contracts are an excellent example of this. Others will be less formal – the document is approved once it’s published and ready for use.
    
7.  **Storage:** Once a document is complete, it’s a good practice to store it in a repository of some sort to allow authorized users to find it and access it and the information it contains.
    

In short, document management is used to create information objects and to provide transparency and accountability for how a particular information object has come to be.

## Records Management

Some documents need to be managed more formally because they serve as evidence of a transaction or decision that imposes an obligation on the organization. We call these information objects _records_ and store them in such a way as to safeguard that evidentiary weight. A particular record may be comprised of multiple items – for example, an insurance claim that includes the claim form, statements from witnesses or authorities, photographs, etc.

Records are complete. Once an information object has been declared as a record, no further changes are expected or in fact, allowed. If changes are required, for example, the addition of an exhibit to a contract, the resulting output is a new record in its own right.

Here are the key capabilities associated with [records management](https://www.aiim.org/What-is-Electronic-Records-Management?_ga=2.51911594.249551674.1598470138-1235767968.1598470138) processes and systems:

**Declaration and Registration:** The record is placed in a repository, and a unique identifier is assigned so it can be managed consistently throughout its lifecycle.

**Access Controls:** Authorized users will be able to access, retrieve, and read the record – but make no changes to it. In some circumstances, there may be a reason to allow changes to the metadata associated with a record.

**Retention Rules:** Different types of records have different requirements for how long they must be kept, according to their legal, fiscal, administrative, or historical value. The records management system will assign retention rules based on the contents of the records.

**Disposition:** At the end of the records lifecycle, records that have no further business value and that are not involved with a legal audit, or other sort of matter will either be [destroyed or transferred to a controlling legal authority](https://blog.doculabs.com/good-bad-ugly-defensible-disposition) such as a national or state archives or a corporate library.

**Audit Trails:** This serves as the final documentation for how a record was managed from declaration to disposition. In many organizations, audit trails are themselves records that need to be managed.

## Conclusion

Both document and records management processes and systems bring value to the organization. Document management helps to ensure accountability for the process of document creation; records management helps to ensure accountability for managing records that are needed to conduct the business of the organization. Most enterprise content management systems today provide effective capabilities for both document and records management.

## Via SharePoint
### Enterprise Content Management ([[ECM]])
- Can be implemented via SharePoint out of the box
- Others:
	- DocuWare
	- OpenText
	- IBM
### Records Management
- Possible out of the box but potentially complicated
- Via Colligo ([Records management - Colligo - Make SharePoint records management a breeze with Colligo](https://www.colligo.com/365-apps-for-business/sharepoint-records-management/))
	- Leverages SharePoint but with a new (controlled) UI
## Source

[Document Management vs. Records Management: What’s the Difference? (aiim.org)](https://info.aiim.org/aiim-blog/document-management-vs.-records-management)