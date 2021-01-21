# awsCCP
Notes for AWS Certified Cloud Practitioner Exam


12:00
Create an alarm, notify you when you go over a certain threshold
Done in Cloudwatch
Uses an SNS topic
S3 Basics
Simple secure storage
Safe place to store files
Object based storage
Data is spread across multiple devices/facilities
Files can be 0-5 terabytes
Unlimited storage
Files stored in buckets
S3 is a universal namespace - name must be unique globally
Uploading a file to S3 gives you a HTTP 200 code if successful upload
Objects consist of:
Key - name of object
Value - the data
Version ID
Metadata - data about your data
Subresources
ACL
Torrent
Data consistency
Read after write consistency for PUTS of new objects
Eventual consistency for overwrite PUTS and DELETES
Guarantees
Built for 99.99% availability
Amazon guarantees 99.9% availability
Amazon guarantees 11x9s durability for S3 info
Features
Tiered storage
S3 Standard
99.99% availability, 11x9s durability
Stored redundantly across multiple devices in multiple facilities
Can sustain the loss of 2 facilities concurrently
S3 IA (Infrequently Accessed)
Data accessed less frequently, but may need rapid access when necessary
Lower fee than S3, but retrieval fee
S3 One Zone - IA (Reduced Redundancy Storage)
Lower cost option for IA data
Do not require multiple AZ
S3 Intelligent Tiering
Optimizes costs by automatically moving data to the most cost effective access tier, without performance impact or operational overhead
Glacier
S3 Glacier
Secure, durable, low cost storage for data archiving
Can reliably store any amount of data for really cheap
Retrieval times configurable from minutes and hours
S3 Glacier Deep Archive
Lowest cost storage
Retrieval time of 12 hours is acceptable
Lifecycle management
Versioning
Encryption
MFA for Deleting
Secure data using ACLs and bucket policies
Charges
Storage
Requests
Storage Management Pricing
Data transfer pricing
Transfer acceleration - fast easy secure transfers over long distances to end users. Uses edge locations
Cross region replication pricing
Read the S3 FAQs

1:00
Lunch

2:00
S3 Security and Encryption
Buckets are private by default. Access control to buckets can be setup using bucket policies and ACLs
S3 buckets can be configured to create access logs which log all requests. Can be sent to another bucket or another account’s bucket
Encryption in transit - SSL/TLS
Encryption at rest (server side)
S3 managed keys - amazon manages the keys (SSE-S3) (Server Side Encryption)
AWS Key Management Service, Managed Keys (SSE-KMS)
Server Side Encryption with Customer Provided Keys (SSE-C)
Client 
S3 Version Control
Stores all versions of an object (including all writes and even if you delete an object)
Great backup tool
Once enabled, can’t be disabled, only suspended
Integrates with lifecycle rules
Versioning’s MFA Delete capability can be used for added security

3:00
Lifecycle Management
Automates moving objects between different storage tiers
Can be used with versioning
Can be applied to current and previous versions
Cross Region Replication
Versioning must be enabled on source and destination buckets
Regions must be unique
Files in bucket are not replicated automatically
All subsequent files are replicated automatically
Delete markers are not replicated
Deleting individual versions or delete markers will not be replicated either
Transfer Acceleration
Uses CloudFront Edge Network to accelerate uploads to S3
Instead of uploading directly to S3 bucket, you use a distinct URL to upload to an edge location which then goes to S3

4:00
Cloudfront
A CDN is a system of distributed servers(network) that delivers webpages and other web content to a user based on user location, webpage origin, and content delivery server
Edge location - location where content is cached. These are Read and Write
Origin - origin of all the files that the CDN distributes
Distribution - the name given the CDN, which consists of a set of edge locations
Requests are automatically routed to the nearest edge location, so you get the best possible performance
Web distribution - used for websites
RTMP - used for media streaming
Objects are cached for the life of the TTL
You can clear cached objects, but you will be charged
Snowball - just need to know what it is, and that you can use it to import/export to S3
Petabyte-scale data transport solution to transport large amounts of data into and out of AWS
Addresses common challenges with large scale data transfers - high network costs, long transfer times, security concerns
Is simple, fast, secure, and cheaper
50 TB or 80 TB
Uses multiple layers of security - tamper resistant enclosure, 256 bit encryption, industry standard Trusted Platform Module (TPM)
Software erasure of appliance once transfer processed and verified
Snowball Edge
100 TB data transfer with on board storage and compute capabilities. 
Can use it to move large amounts of data in/out of AWS, as temporary storage tier for large local datasets, or support local workloads in remote or offline locations
Is basically a portable AWS
AWS Snowmobile
Exabyte-scale data transfer service - can transfer up to 100PB per Snowmobile
Is a 45 foot long ruggedized shipping container pulled by a truck
Secure, fast, cost effective

5:00
Storage Gateway
Service that connects on premise software appliance with cloud based storage
Software appliance is available to download as VM image
Can also get a physical device for this
Can use AWS management console to create gateway option you want
3 different types of storage
File gateway - NFS & SMP
Files are stored as objects in S3 buckets
Accessed through network file system
Ownership, permission, timestamps durably stored in S3
Once transferred to S3, they can be managed as native S3 objects, so bucket policies can apply to them
Volume Gateway - iSCSI
Presents your app with disk volumes using iSCSI block protocol
Data written to these volumes can be backed up as point in time snapshots of your volume, and stored as EBS snapshot
Snapshots are incremental backups that only capture changed blocks. Snapshot storage is compressed
Stored Volumes - Volume gateway
Let you store your primary data locally
The entire dataset
Cached Volumes
Retains most frequently accessed data locally in storage gateway
Caches the most actively used data
Tape Gateway - VTL
Durable cost effective solution to archive data into AWS
Get rid of tapes
Summary
File gateway - for flat files, stored directly on S3
Volume gateway
Stored volumes - entire dataset stored on site and backed up to S3
Cached volumes - entire dataset stored on S3, most frequently accessed data is cached on site
Gateway virtual tape library
Section Summary, Quiz

6:00 - 8:00
EC2
Resizable compute capacity in AWS
Reduces time to get and boot new server instances to minutes
Can quickly scale up and down as computing requirements change
Instance types
On demand - Pay fixed rate by the second, no commitment
Reserved - 1 or 3 year term, considerably cheaper
Spot - bid for it by the hour. Are not charged entire hour if EC2 terminates it, but will be charged if you terminate it yourself
Dedicated host - you get your own host
