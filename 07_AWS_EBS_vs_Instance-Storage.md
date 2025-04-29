# AWS - Storage Options: EBS vs. Instance Storage

## Types of AWS Storages
- AWS offers various storage options, including Amazon S3, Amazon EBS, Amazon EFS, and instance storage (ephemeral storage)
  - **Amazon EBS (Elastic Block Store)**: Persistent, block-level storage for EC2 instances
  - **Amazon S3 (Simple Storage Service)**: Object-level storage for various use cases like backups, archives, and static website hosting
  - **Amazon EFS (Elastic File System)**: Scalable file storage for sharing data across multiple EC2 instances in a VPC
  - **Instance Storage**: Local storage associated with an EC2 instance. It is ephemeral so, data is lost when the instance stops or terminates

## EBS Volume (Amazon Elastic Block Store)
- Provides block-level storage volumes for use with Amazon EC2 instances
- Persistent, meaning they exist independently of the life of an EC2 instance
- Similar to a physical hard drive, accessible by partitions and file systems
- Backed up by redundant storage infrastructure for durability (hence highly available)
- Highly scalable so volumes can be attached, detached, and resized while running
- Numerous options are available depending on performance and cost requirements (SSD, HDD etc.)
- **Use Cases**: Databases, web servers, and applications requiring data to survive instance restarts
- **Limitations**:
  - Can be more expensive than instance storage, especially for high-performance or large-capacity needs
  - EBS introduces some latency compared to local instance storage due to network communication

### EBS Volume Types
- **General Purpose SSD (``gp2``, ``gp3``)**: Balanced performance for a wide range of applications (e.g., databases, web servers)
- **Provisioned IOPS SSD (``io1``, ``io2``)**: High and consistent IOPS (Input/Output Operations Per Second) for performance-critical workloads (e.g., real-time analytics)
- **Throughput Optimized HDD (``st1``)**: Cost-effective option for frequent data access with moderate throughput needs (e.g., log processing)
- **Cold HDD (``sc1``)**: Lowest-cost option for infrequently accessed data archives (e.g., backups)

> Notes:
> - Can attach multiple EBS volumes to a single EC2 instance, but each volume can only be attached to one instance at a time
> - Can increase the size of an EBS volume while it's in use, but cannot decrease its size
> - By default, AWS creates replicas of EBS volumes within the same Availability Zone for durability
> - Instance and EBS volumes do not have to be in the same AZ

## Instance Storage
- Also called ephemeral storage
- They are physically attached to the EC2 instance hosting it. So, data is lost when the instance stops or terminates
- Ideal for temporary data or workloads that don't require persistence
- Lower latency compared to EBS volumes due to direct access
- **Use Cases**:
  - Tasks that don't require persistent data storage (e.g., web scraping, log processing for a short duration)
  - Setting up a quick development environment where data persistence is not critical
  - Temporary storage of frequently accessed data for faster retrieval

## Other Storage Options provided by AWS
### Amazon Simple Storage Service (S3)
- Highly scalable, durable, and secure object storage service
- Ideal for storing and retrieving any amount of data, from websites and mobile apps to backups and archives
- Offers various storage classes optimized for different access patterns and cost requirements

### Block Storage
- **Amazon Elastic Block Store (EBS)**
  
### File Storage
- **Amazon Elastic File System (EFS)**:
  - Offers a scalable, fully managed network file system for Linux-based workloads
  - Enables shared file access for multiple EC2 instances, making it ideal for applications that require concurrent access to data
- **Amazon FSx**:
  - Provides fully managed file systems for various workloads, including:
    - **Amazon FSx for Lustre**: High-performance file system optimized for compute-intensive workloads
    - **Amazon FSx for Windows File Server**: Provides a fully managed native Microsoft Windows file system
- **Amazon File Cache**:
    - A fully managed, high-speed cache on AWS that makes it easier to process file data, regardless of where the data is stored

### Hybrid Cloud Storage
- **AWS Storage Gateway**:
  - Connects on-premises applications to AWS storage services
  - Provides various gateway types, including File Gateway, Volume Gateway, and Tape Gateway, to integrate on-premises workflows with the cloud

### Data Transfer
- **AWS Snow Family**:
  - A collection of physical devices that enables transferring large amounts of data into and out of AWS
    - This includes AWS Snowball, Snowball Edge, and Snowcone
- **AWS DataSync**:
  - Automates online data transfer between on-premises storage and AWS storage services