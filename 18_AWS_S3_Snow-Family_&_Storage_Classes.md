# AWS S3 - Snow Family and Storage Classes

## AWS Snow Family
- Provides **physical devices** to migrate large amounts of data into and out of AWS when traditional network transfers are too slow, expensive, or unreliable
- Useful for petabyte-scale migrations or locations with limited bandwidth
- All Snow devices feature tamper-evident enclosures and use encryption to protect data in transit

### 1. AWS Snowcone & Snowcone SSD
- Used for small-scale data transfer and edge computing in space-constrained or portable environments
- Equipped with 2 vCPUs and 4 GB of memory for basic edge computing tasks (e.g., running simple AWS IoT Greengrass functions or small EC2 instances)
- **Form Factor**: The smallest member; highly portable, rugged, and lightweight (around 4.5 lbs / 2.1 kg)
- **Capacity**:
    - **Snowcone (HDD)**: 8 TB usable storage
    - **Snowcone SSD**: 14 TB usable NVMe SSD storage (faster performance)
- **Connectivity**: Includes Wi-Fi, dual 1/10 GbE network ports. Optional battery power and LTE support for true mobility
- **Use Cases**: Edge computing in remote or disconnected locations, IoT data aggregation and preprocessing, tactical edge deployments, content distribution to dispersed sites, small data migration jobs

### 2. AWS Snowball Edge
- Used for larger data transfers and more powerful edge computing capabilities compared to Snowcone
- **Form Factor**: Ruggedized, portable (but heavier than Snowcone) shipping container-like devices
- **Types & Capacity**:
    - **Snowball Edge Storage Optimized**: Designed primarily for large data transfers. Offers **80 TB usable HDD storage**. Includes significant compute power (e.g., 40 vCPUs, 80 GiB memory) suitable for data processing during migration
    - **Snowball Edge Compute Optimized**: Built for demanding edge computing applications requiring more processing power or specialized hardware. Offers less storage (e.g., **42 TB usable HDD** or **32 TB usable NVMe SSD**) but significantly more compute resources (e.g., up to 104 vCPUs, 416 GiB memory) and **optional GPUs**
- Both types can run EC2 instances, Lambda functions, and containerized applications locally using AWS IoT Greengrass or native EC2 APIs, enabling data processing, analysis, or machine learning inference at the edge before or instead of transferring to AWS. Can be clustered for higher availability or performance
- **Use Cases**: Large-scale data migrations (terabytes to petabytes), data center decommissioning, disaster recovery (data staging), remote site data collection and processing (e.g., industrial sites, ships), machine learning inference at the edge, video analysis

### 3. AWS Snowmobile
- Used for extremely large-scale data migration, typically for moving entire data centers
- This is a fully managed service. AWS personnel handle the transport, setup, data transfer monitoring, and return
- **Form Factor**: A **45-foot long ruggedized shipping container** transported by a semi-trailer truck
- **Capacity**: Can transfer up to **100 Petabytes (PB)** per Snowmobile, enabling Exabyte-scale transfers with multiple units
- **Security**: Features multiple layers of security including GPS tracking, alarm monitoring, 24/7 video surveillance, and optional dedicated security personnel or an escort vehicle during transit. The container is climate-controlled, water-resistant, and tamper-resistant
- **Use Cases**: Migrating massive datasets (multiple petabytes or exabytes), moving entire data centers to AWS, archiving enormous volumes of data (e.g., video libraries, scientific research data, seismic data)


## S3 Storage Classes
### 1. S3 Standard
- It is the default class, offering high durability, availability, and performance for frequently accessed data
- **Benefits**: Fast access, high durability, availability, and ideal for active data
- **Limitations**: Higher cost compared to other classes
- **Use Cases**: Active data that requires high availability and frequent access

### 2. S3 Intelligent-Tiering (S3 Glacier Instant Retrieval)
- It automatically transitions data between frequent access (S3 Standard) and infrequent access tiers (S3 Glacier) based on usage patterns 
- **Benefits**: 
  - Automatically optimizes storage costs based on access patterns
  - Cost-effective for data with unknown or changing access patterns
- **Limitations**: Potential retrieval charges for infrequently accessed data
- **Use Cases**: Data with unpredictable or changing access patterns, where automatic cost optimization is desired

> **Note**: S3 Intelligent-Tiering is popular due to its automated storage management. It automatically analyzes access patterns and seamlessly moves data between frequent and infrequent access tiers. This makes it ideal for dynamic data sets where access patterns might be unpredictable

### 3. S3 Glacier
- It is designed for long-term archival storage of rarely accessed data
- **Benefits**: Very low cost for long-term data retention
- **Limitations**: Retrieval can take hours
- **Use Cases**: Data with regulatory or compliance requirements for long-term retention

### 4. S3 Glacier Deep Archive
- It is the most cost-effective storage class for infrequently accessed data with retrieval times of 12 hours or more. 
- **Benefits**: Extremely low cost for data with very infrequent access requirements
- **Limitations**: Long retrieval times (12 hours or more) and minimum retention periods
- **Use Cases**: Data with minimal access requirements and where retrieval times are not a concern

### 5. S3 One Zone
- It is a single Availability Zone storage class offering high performance and reduced latency for frequently accessed data in a specific region
- **Benefits**: Lower cost than S3 Standard for specific regions
- **Limitations**: Data resides in a single zone, potentially impacting availability during outages
- **Use Cases**: Non-critical or reproducible data with infrequent access needs and lower availability requirements

### 6. Reduced Redundancy Storage (RRS)
- It offers a lower-cost option for non-critical, easily reproducible data
- **Benefits**: Very low cost
- **Limitations**: Reduced data redundancy compared to other classes
- **Use Cases**: Non-critical, easily reproducible data where absolute cost minimization is essential

### Life Cycle Rules and S3 Storage Classes
- Life cycle rules allows to automate the transition of objects between storage classes based on user-defined criteria (e.g., time since last access)
- This helps ensure cost-effectiveness by moving infrequently accessed data to lower-cost tiers while keeping frequently accessed data readily available

### Summary
| Storage Class | Availability | Min Storage Duration | Retrieval Time | Ideal Use Case | Cost (Approx) |
|----|----|----|----|----|----|
| **S3 Standard** | 99.99% | None | Instant | Frequently accessed data like websites, apps  | Higher per GB  |
| **S3 Intelligent-Tiering** | 99.9% | 30 days | Instant | Unknown access patterns, auto cost-optimized  | Low monitoring fee (~$0.0025 per 1000 objects/month) |
| **S3 Standard-IA (Infrequent Access)** | 99.9% | 30 days | Instant | Backups, disaster recovery (less frequent access) | Lower storage cost than Standard, higher retrieval cost |
| **S3 One Zone-IA** | 99.5% | 30 days  | Instant  | Infrequently accessed data that can tolerate AZ loss | Cheaper than Standard-IA |
| **S3 Glacier** | Varies| 90 days | Minutes to hours     | Long-term archival (e.g., logs, compliance)   | Very low storage, retrieval cost varies |
| **S3 Glacier Deep Archive** | Varies | 180 days | Up to 12 hours       | Rare access data (e.g., historical records)   | Cheapest storage, slowest retrieval |
| **S3 Outposts** | Local | Custom  | Local | Store S3 data on-prem with low latency access | On request – hardware managed by AWS on-prem |
