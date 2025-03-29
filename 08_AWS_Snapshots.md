# AWS Snapshots

## Snapshot
- Captures the complete data at the moment the snapshot is initiated. 
- Acts as a backup to restore data in case of accidental deletion, corruption, or hardware failure.
- Can be used to recover EBS volumes in a different AZ.
- Can be used to create a snapshot and launching a new volume from it.
- Can also schedule automated snapshots to create regular backups of EBS volumes.
- Should create snapshots before making significant changes to EBS volume for easy rollback if needed.
- Snapshots inherit the encryption settings of the source EBS volume.
- Can change the volume type (e.g., SSD to HDD) when creating a new volume from a snapshot.
- Cannot create a new volume in a different region directly from a snapshot. 
- AWS allows configuring scheduled snapshots using AWS Lambda or CloudWatch Events. 
- **Limitations**:
  - Snapshots are stored in S3, which incurs storage costs.
  - Currently, AWS creates full snapshots, capturing the entire volume data each time.

> Note: **Incremental vs Full Snapshots**
> Full snapshot captures the entire volume data each time. Incremental snapshots, capturing only data changes since the last snapshot, are not yet available.


## AWS Retention Rules
Rules that define how long AWS will retain snapshots before automatically deleting them. These rules can be configured to ensure that snapshots are stored for the desired period for compliance or recovery purposes.