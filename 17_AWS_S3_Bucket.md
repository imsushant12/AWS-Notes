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


## Snow Family
Helps to move large volumes of data **physically** between on-premise and AWS when network transfer is slow, costly, or unreliable

### 1. AWS Snowcone
- Smallest device (8 TB usable storage)
- Portable, rugged, and lightweight (~4.5 lbs)
- Has optional battery and LTE support
- **Use Case**: Edge computing, remote locations, IoT setups

### 2. AWS Snowball
- Comes in two types:
  - **Snowball Edge Storage Optimized** (up to 80 TB usable)
  - **Snowball Edge Compute Optimized** (has GPU + compute power)
- Can run EC2 instances and Lambda at edge
- Automatically integrates with AWS services upon upload
- **Use Case**: Data migration, edge computing, disaster recovery

### 3. AWS Snowmobile
- Massive data transfer (up to 100 PB)
- Physical 45-foot shipping container transported via truck
- Encrypted and GPS-tracked for security
- **Use Case**: Data center migrations, large-scale archival to AWS


## S3 Storage Classes
| Storage Class | Availability | Min Storage Duration | Retrieval Time | Ideal Use Case | Cost (Approx) |
|----|----|----|----|----|----|
| **S3 Standard** | 99.99% | None | Instant | Frequently accessed data like websites, apps  | Higher per GB  |
| **S3 Intelligent-Tiering** | 99.9% | 30 days | Instant | Unknown access patterns, auto cost-optimized  | Low monitoring fee (~$0.0025 per 1000 objects/month) |
| **S3 Standard-IA (Infrequent Access)** | 99.9% | 30 days | Instant | Backups, disaster recovery (less frequent access) | Lower storage cost than Standard, higher retrieval cost |
| **S3 One Zone-IA** | 99.5% | 30 days  | Instant  | Infrequently accessed data that can tolerate AZ loss | Cheaper than Standard-IA |
| **S3 Glacier** | Varies| 90 days | Minutes to hours     | Long-term archival (e.g., logs, compliance)   | Very low storage, retrieval cost varies |
| **S3 Glacier Deep Archive** | Varies | 180 days | Up to 12 hours       | Rare access data (e.g., historical records)   | Cheapest storage, slowest retrieval |
| **S3 Outposts** | Local | Custom  | Local | Store S3 data on-prem with low latency access | On request – hardware managed by AWS on-prem |