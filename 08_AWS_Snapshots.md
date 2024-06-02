## AWS Snapshots: Capturing Your EBS Volumes

### What is a Snapshot?
An AWS snapshot is a point-in-time copy of your entire EBS volume. It captures the complete data at the moment the snapshot is initiated. This snapshot acts as a backup, allowing you to restore your data in case of accidental deletion, corruption, or hardware failure.

#### Benefits of Snapshots
* **Data Backup and Recovery**: Restore lost data or recreate volumes quickly from a snapshot.
* **Disaster Recovery**: Recover your EBS volumes in a different Availability Zone (AZ) for enhanced disaster preparedness.
* **Migration**: Easily migrate your data to a new EBS volume or a new EC2 instance using snapshots.
* **Version Control**: Maintain historical snapshots of your EBS volume at different points in time for rollback or data analysis.

#### Use Cases for Snapshots
* **Regular Backups**: Schedule automated snapshots to create regular backups of your EBS volumes.
* **Testing and Development**: Create snapshots before making significant changes to your EBS volume for easy rollback if needed.
* **Data Migration**: Migrate data between EC2 instances or across regions by creating a snapshot and launching a new volume from it.
* **Long-Term Data Archiving**: Store snapshots of inactive volumes for long-term data retention.

#### Limitations of Snapshots
* **Not Real-time Backups**: Snapshots capture data at a specific point in time. Data changes after the snapshot creation are not captured.
* **Cost**: Snapshots are stored in S3, which incurs storage costs.
* **Incremental vs. Full Snapshots**: Currently, AWS creates full snapshots, capturing the entire volume data each time.

#### Snapshots and Encryption
* Snapshots inherit the encryption settings of the source EBS volume.
* If the source volume is encrypted, the resulting snapshot will also be encrypted. 
* You can choose to encrypt the snapshot independently during creation for additional security.


### AWS Retention Rules
AWS allows you to set retention rules for snapshots. These rules define how long AWS will retain your snapshots before automatically deleting them. You can configure retention rules to ensure your snapshots are stored for the desired period for compliance or recovery purposes.


### FAQs
**Question 1**: Where does AWS stores the snapshot of EBS?

**Answer**: AWS stores snapshots in Amazon S3, a highly durable and scalable object storage service. This ensures data redundancy and availability for restoring your EBS volumes.

**Question 2**: What is AWS Snapshots?

**Answer**: AWS snapshots capture the entire data on an EBS volume at the time the snapshot is initiated. This includes the file system, data blocks, and metadata associated with the volume.

**Question 3**: AWS follows which snapshot strategy? (Incremental or Full Snapshots)

**Answer**: AWS currently uses full snapshots, meaning they capture the entire volume data each time. Incremental snapshots, capturing only data changes since the last snapshot, are not yet available. This simplifies snapshot management but can lead to higher storage costs compared to incremental backups.

**Question 4**: Can we share snapshot within regions?

**Answer**: Yes, you can share snapshots across regions.  However, there are associated data transfer costs for transferring the snapshot data between regions.

**Question 5**: How to create snapshot in AWS?

**Answer**: You can create snapshots through the AWS Management Console, AWS CLI, or AWS SDKs. Simply navigate to your EBS volume in the console, select "Actions," and choose "Create Snapshot." 

**Question 6**: Can we change volume, AZ, regions, volume type while creating a new volume and new instance from a snapshot?

**Answer**:
* **Volume Type**: You can change the volume type (e.g., SSD to HDD) when creating a new volume from a snapshot.
* **AZ**: You can create a new volume in a different AZ within the same region from the snapshot.
* **Region**:  No, you cannot create a new volume in a different region directly from a snapshot. However, you can copy the snapshot to the target region and then create a new volume from the copied snapshot.
* **Instance Type**: When launching a new instance from a snapshot, you need to choose an instance type compatible with the volume size and operating system stored in the snapshot.

**Question 7**: How to create scheduled snapshot in AWS?

**Answer**: AWS allows you to configure scheduled snapshots using AWS Lambda or CloudWatch Events. These tools trigger snapshot creation automatically based on your defined schedule.

### Summary
![](https://i.imgur.com/fJAmXUW.png)
