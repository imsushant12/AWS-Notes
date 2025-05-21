# AWS - S3 Replication, SRR vs. CRR, Batch Operations, and Transfer Acceleration

- S3 offers two data replication options to ensure the availability, durability, and disaster recovery of the data:
  1. S3 Same-Region Replication (SRR)
  2. S3 Cross-Region Replication (CRR)

## SRR (Same-Region Replication)
- Creates copies of S3 objects within the same AWS region but across geographically separate Availability Zones (AZs)
- Protects data from failures limited to a single AZ (if one AZ goes down, objects remain accessible from the replicated copy in another AZ). This also results in lower latency compared to CRR
- No egress charges are incurred for data transfer because replication happens within the same region
- **Use Case**: Replicate frequently accessed data within a region for faster retrieval from geographically dispersed users (within the region)

## CRR (Cross-Region Replication)
- Creates copies of S3 objects in a completely different AWS region, geographically distant from the source region
- Provides the highest level of data protection by storing copies in a separate region
- Accessing replicated data across regions might experience **higher latency** due to the inter-region data transfer
- Incur egress charges for data transfer out of the source region
- **Use Case**: Regulatory compliance that dictates data storage in specific regions

> **Note**: By default, SRR and CRR continuously replicate new objects uploaded to the source bucket

## One-Time Batch Operation Job in SRR and CRR
- SRR and CRR might not automatically replicate existing objects already present in the source bucket at the time replication is enabled. To solve this, S3 offers **S3 Batch Replication**
- It triggers a one-time job to copy a specific subset or all existing objects from the source bucket to the destination bucket, whether within the same region (SRR) or across regions (CRR)

## Choosing Between SRR and CRR
- **Scenario**: Prioritize data durability within a region with faster retrieval speeds
  - SRR
- **Scenario**: Need disaster recovery protection from outages impacting the entire region
  - CRR

## Replication Time Control
- Replication Time Control (RTC) can be used to define a time lag between object creation in the source bucket and its replication to the destination bucket
- It can be useful for scenarios where near-real-time replication might not be necessary and cost optimization is important

## Monitoring and Logging
- AWS CloudTrail can be used to monitor S3 replication events
- Provides logs for troubleshooting and auditing purposes

## Transfer Acceleration
- It enables faster uploads and downloads of files to and from S3 buckets and tackles the challenge of slow website loading times for users located far from the S3 bucket
- It uses Amazon CloudFront's global network of edge locations to significantly improve data transfer speeds
- Working:
  1. A file is uploaded to S3 bucket using a specially generated accelerated endpoint like: `https://<bucket-name>.s3-accelerate.amazonaws.com
  `
  2. The request is routed to the nearest CloudFront edge location
  3. From there, AWS uses its optimized backbone network to move the file to the destination S3 bucket much faster than over the public internet
- It is fully managed by AWS and it incurs additional charges compared to standard data transfer rates
- If the website offers large file downloads (e.g., software, media files), faster transfer speeds are essential, Transfer Acceleration can significantly reduce download times
- **Use Cases**:
  - Global media companies transferring large video files
  - SaaS applications syncing user data across continents
  - Enterprises backing up large datasets to S3 from global branch offices