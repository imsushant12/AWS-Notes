# AWS S3 - Buckets, Versioning, Storage Gateway, Snow Family, and Storage Classes

- A scalable object storage service designed to store and retrieve any amount of data from anywhere on the web
- It is secure, highly scalable, highly available, and cost effective
- Offers various security features like access control lists (ACLs) and encryption to control who can access data
- By default, S3 objects are private
- Minimum and Maximum object size:
  - Minimum object size: 0 bytes (empty file)
  - Maximum object size: 5 TB
- **Can be used for**:
  - storing files, images, videos, backups, and static website content
  - hosting static websites
  - data lake storage for big data analytics
  - disaster recovery and backups
  - storing logs or application data
- **Key Features**:
  - Highly durable (99.999999999% durability)
  - Scalable and cost-effective
  - Supports lifecycle policies to automatically move data to cheaper storage (e.g., Glacier)
  - Built-in security with encryption, IAM policies, and access control

## Bucket
- A storage unit within **Simple Storage Service** (S3)
- Buckets are region specific and their name should be globally unique
- Stores data as objects and each object is stored as a key-value pair
  - Key is the object's name
  - Value is the content of the object
- It is region specific and the name of the bucket should be globally unique (3 to 63 characters long)
- **Drawbacks**:
  - Not ideal for applications requiring frequent data updates due to its object-based storage structure
  - There are some charges for transferring data out of S3 buckets

### Multipart Uploads in S3
- Used to upload large objects (recommended for files >100MB, required for >5GB)
- Only failed parts need to be retried if an error occurs

### `11 9’s` in S3
- Refers to **99.999999999% durability**
- Means losing 1 object every 10 million stored for 10,000 years
- AWS achieves this by:
  - Automatic replication across multiple availability zones (AZs)
  - Continuous data integrity checks and repairs


### Why Must an S3 Bucket Name Be Globally Unique?
- Bucket names are part of the public URL (e.g., `https://my-bucket.s3.amazonaws.com`). So, to avoid conflicts, names must be globally unique across all AWS accounts and regions
- Also helps AWS map DNS and route traffic correctly to the right bucket


### Encryption at Rest and In Transit
- S3 supports both encryption at rest and in transit
- **Encryption at rest**: Protects data when stored on disk
  - S3 supports:
    - SSE-S3 (S3-managed keys)
    - SSE-KMS (KMS-managed keys)
    - SSE-C (customer-managed keys)
- **Encryption in transit**: Protects data while it's being transferred
  - S3 supports this using **HTTPS (SSL/TLS)**


### ARN (Amazon Resource Name) in S3
- A unique identifier for AWS resources that follows a standard format specifying the AWS partition, service, region, account ID, and the bucket name. For example:
```
arn:aws:s3:<region>:<account-id>:<bucket-name>
```


### Entity Tag (`ETag`) in S3
- A unique identifier assigned to an object (file) in an S3 bucket
- Reflects the object's content and acts as a validation check so if the same object is uploaded twice, same ETag will be generated


## S3 Versioning
- S3 supports versioning
- Every version of an object is stored which leads to higher storage costs compared to non-versioned buckets
- Managing and keeping track of numerous object versions can add complexity, especially for frequently updated objects


## S3 Storage Gateway
- Connects on-premises environments with AWS cloud storage
- Enables on-premises apps to access data in S3 using standard protocols like NFS, SMB, and iSCSI
- Offers **File Gateway**, **Tape Gateway**, and **Volume Gateway** options


## Website Hosting with S3 Buckets
- S3 buckets can be used to host static websites
- Can configure S3 bucket for direct access to website content
- Can also use custom domain name instead of the S3 bucket URL

- **Advantages**:
  - Can easily handle traffic spikes without infrastructure limitations
  - Can be integrate with CloudFront for faster loading times worldwide
  - Pay only for the storage usage which makes it budget-friendly
- **Limitations**:
  - Does not support server-side scripting 
  - Less control over server configuration compared to traditional web hosting
  - No built-in support for things like user authentication, dynamic content generation, and server-side routing