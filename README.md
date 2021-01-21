# S3
**Basics**
- Simple secure storage
- Safe place to store files
- Object based storage
- Data is spread across multiple devices/facilities
- Files can be 0-5 terabytes
- Unlimited storage
- Files stored in buckets
- S3 is a universal namespace - name must be unique globally
- Uploading a file to S3 gives you a HTTP 200 code if successful upload
- Objects consist of:
  - Key - name of object
  - Value - the data
  - Version ID
  - Metadata - data about your data
  - Subresources
    - ACL
    - Torrent
  - Data consistency
    - Read after write consistency for PUTS of new objects
    - Eventual consistency for overwrite PUTS and DELETES
  - Guarantees
    - Built for 99.99% availability
    - Amazon guarantees 99.9% availability
    - Amazon guarantees 11x9s durability for S3 info
  - Features
    - Tiered storage
      - S3 Standard
        - 99.99% availability, 11x9s durability
        - Stored redundantly across multiple devices in multiple facilities
        - Can sustain the loss of 2 facilities concurrently
      - S3 IA (Infrequently Accessed)
        - Data accessed less frequently, but may need rapid access when necessary
        - Lower fee than S3, but retrieval fee
      - S3 One Zone - IA (Reduced Redundancy Storage)
        - Lower cost option for IA data
        - Do not require multiple AZ
      - S3 Intelligent Tiering
        - Optimizes costs by automatically moving data to the most cost effective access tier, without performance impact or operational overhead
      - Glacier
	      - S3 Glacier
		      - Secure, durable, low cost storage for data archiving
		      - Can reliably store any amount of data for really cheap
		      - Retrieval times configurable from minutes and hours
	      - S3 Glacier Deep Archive
		      - Lowest cost storage
		      - Retrieval time of 12 hours is acceptable
    - Lifecycle management
    - Versioning
    - Encryption
    - MFA for Deleting
    - Secure data using ACLs and bucket policies
    - Charges
      - Storage
      - Requests
      - Storage Management Pricing
      - Data transfer pricing
      - Transfer acceleration - fast easy secure transfers over long distances to end users. Uses edge locations
      - Cross region replication pricing
    - Read the S3 FAQs
&nbsp;  
&nbsp;  
**S3 Security and Encryption**
  - Buckets are private by default. Access control to buckets can be setup using bucket policies and ACLs
  - S3 buckets can be configured to create access logs which log all requests. Can be sent to another bucket or another account’s bucket
  - Encryption in transit - SSL/TLS
  - Encryption at rest (server side)
	  - S3 managed keys - amazon manages the keys (SSE-S3) (Server Side Encryption)
	  - AWS Key Management Service, Managed Keys (SSE-KMS)
	  - Server Side Encryption with Customer Provided Keys (SSE-C)
  - Client


  **S3 Version Control**
 - Stores all versions of an object (including all writes and even if you delete an object)
 - Great backup tool
 - Once enabled, can’t be disabled, only suspended
 - Integrates with lifecycle rules
 - Versioning’s MFA Delete capability can be used for added security
