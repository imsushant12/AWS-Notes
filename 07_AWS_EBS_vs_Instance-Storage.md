## Understanding AWS Storage Options: EBS vs. Instance Storage

### Types of AWS Storages
AWS offers various storage options, including Amazon S3, Amazon EBS, Amazon EFS, and instance storage (ephemeral storage).
* **Amazon EBS (Elastic Block Store)**: Persistent, block-level storage for EC2 instances. Volumes persist independently of the instance lifecycle (start/stop/termination).
* **Amazon S3 (Simple Storage Service)**: Object-level storage for various use cases like backups, archives, and static website hosting.
* **Amazon EFS (Elastic File System)**: Scalable file storage for sharing data across multiple EC2 instances in a VPC.
* **Instance Storage**: Local storage associated with an EC2 instance (ephemeral). Data is lost when the instance stops or terminates.

### EBS Volume in AWS
Amazon Elastic Block Store (EBS) provides block-level storage volumes for use with Amazon EC2 instances. It is different from other storage options, EBS volumes are persistent, meaning they exist independently of the life of an EC2 instance.

#### Important Points
* **Persistent storage**: Data survives instance stops, restarts, and terminations.
* **Block-level storage**: Similar to a physical hard drive, accessible by partitions and file systems.
* **Highly available**: Backed by redundant storage infrastructure for durability.
* **Scalable**: Volumes can be attached, detached, and resized while running.
* **Multiple volume types**: cater to different performance and cost requirements (SSD, HDD etc.)

#### EBS Volume Types
* **General Purpose SSD (``gp2``, ``gp3``)**: Balanced performance for a wide range of applications (e.g., databases, web servers).
* **Provisioned IOPS SSD (``io1``, ``io2``)**: High and consistent IOPS (Input/Output Operations Per Second) for performance-critical workloads (e.g., real-time analytics).
* **Throughput Optimized HDD (``st1``)**: Cost-effective option for frequent data access with moderate throughput needs (e.g., log processing).
* **Cold HDD (``sc1``)**: Lowest-cost option for infrequently accessed data archives (e.g., backups).

#### EBS Use Cases and Benefits
* **Persistent applications**: Databases, web servers, and applications requiring data to survive instance restarts.
* **Scalability**: EBS volumes can be scaled up or down based on changing storage needs.
* **Availability**: EBS provides high availability for your data with built-in redundancy.
* **Flexibility**: You can attach, detach, and move EBS volumes between compatible instances.

#### EBS Limitations
* **Cost**: EBS volumes can be more expensive than instance storage, especially for high-performance or large-capacity needs.
* **Latency**: EBS introduces some latency compared to local instance storage due to network communication.

#### FAQs
**Question 1**: Can we attach multiple instances to an EBS and vice versa?

**Answer**: Yes, you can attach multiple EBS volumes to a single EC2 instance, but each volume can only be attached to one instance at a time.

**Question 2**: Can we increase the volume of EBS while using it?

**Answer**: You can increase the size of an EBS volume while it's in use, but you cannot decrease its size.

**Question 3**: Can we change the AZ of EBS while using it? 

**Answer**: You cannot change the Availability Zone (AZ) of an existing EBS volume while it's in use. However, you can detach the volume, snapshot it, and create a new volume in the desired AZ.


**Question 4**: Does AWS created a replica of our EBS by default?

**Answer**: By default, AWS creates replicas of EBS volumes within the same Availability Zone for durability.

**Question 5**: Does instance and EBS has to be in the same AZ?

**Answer**: No, instance and EBS volumes do not have to be in the same Availability Zone (AZ). However, when launching an EC2 instance, it's recommended to select an EBS volume in the same AZ for optimal performance. An EBS volume can be attached to an instance in a different Availability Zone within the same region.

**Question 6**: Which EBS storage allows multiple-attach?

**Answer**: Amazon Elastic Block Store (EBS) does not natively support multiple attachment to EC2 instances. However, you can use Amazon EBS Multi-Attach enabled volumes for certain configurations, allowing a single EBS volume to be attached to multiple EC2 instances simultaneously. Provisioned IOPS SSD (``io1``, ``io2``) volumes allow attaching a single volume to up to 16 Nitro-based instances in the same AZ.

**Question 7**: Which instance allows multiple-attach?

**Answer**: Certain EC2 instance types support multiple network interfaces (ENIs), which can be attached to the same instance. Examples of such instance types include the ``m5d``, ``r5d``, ``z1d``, and ``i3en`` families. Multiple ENIs enable additional network throughput and provide flexibility in networking configurations.

**Question 8**: Can we increase the root volume in EBS? If yes, then how?

**Answer**: You can increase the size of the root volume (the volume from which an EC2 instance boots) by modifying the volume size in the AWS Management Console or using the AWS CLI/API. However, this process requires stopping the instance.

**Question 9**: Does EBS causes latency?
**Answer**: EBS introduces some latency compared to instance storage due to network communication between the instance and the EBS volume. However, modern EBS offerings like provisioned IOPS SSDs offer very low latency suitable for most applications.


### Instance Storage
Instance storage, or ephemeral storage, is physically attached to the EC2 instance hosting it.

#### Important Points
* **Temporary storage**: Data is lost when the instance stops or terminates.
* **Lower cost**: Ideal for temporary data or workloads that don't require persistence.
* **Faster access**: Provides lower latency compared to EBS volumes due to direct access.
* **Advantage**: High performance, low latency, and no additional cost (included with EC2 instance).
* **Disadvantage**:  Data loss if the instance is stopped or terminated, limited durability compared to EBS.
* **Use Cases**:
  * **Temporary workloads**: Tasks that don't require persistent data storage (e.g., web scraping, log processing for a short duration).
  * **Development environments**: Setting up a quick development environment where data persistence is not critical.
  * **Caching**: Temporary storage of frequently accessed data for faster retrieval.


### Summary
![](https://i.imgur.com/tS1Ri5i.png)
