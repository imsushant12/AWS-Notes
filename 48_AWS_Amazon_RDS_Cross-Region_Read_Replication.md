## Cross-Region Read Replicas in Amazon RDS

A feature that allows you to create a read-only replica of your RDS database instance in a different AWS region. This enables disaster recovery, read scaling, and data locality benefits.

#### Advantages of Cross-Region Read Replicas in Amazon RDS
* **Disaster Recovery**: Provides a backup in case of a catastrophic outage in your primary region. You can promote the read replica in the secondary region to become the new primary, minimizing downtime.
* **Read Scaling**: Improves read performance for geographically distributed users by offloading read traffic to the replica in the closer region. This reduces latency for read operations.
* **Data Locality**: Keeps your data closer to users in the secondary region, potentially improving compliance and data residency requirements.

#### Disadvantages of Cross-Region Read Replicas in Amazon RDS
* **Eventual Consistency**: Data on the replica might not be immediately consistent with the primary due to asynchronous replication. This can be a concern for applications requiring strict real-time data consistency.
* **Increased Cost**: You incur additional charges for storing and managing the replica instance in the secondary region.
* **Latency**: There might be some additional latency for writes compared to using a replica in the same region as the primary.

#### Use Cases of Cross-Region Read Replicas in Amazon RDS
* Disaster recovery scenarios for regional outages.
* Improving read performance for geographically distributed applications.
* Meeting data residency requirements by keeping data geographically close to users.


### Promoting a Replica
The process of converting a read replica into a writable primary instance. This can be done manually or automatically during a failover event.

When you promote a replica, it becomes synchronized with the primary database at the time of the promotion. Any data updates that occurred on the primary instance after the promotion will not be reflected on the newly promoted primary until further replication occurs.

### Snapshots vs Backups in RDS

#### Snapshots
They are point-in-time copies of your entire database instance, including data, configuration settings, and parameter groups.
* **Advantages**:
  * Used for creating backups for disaster recovery or testing purposes.
  * Can be used to create read replicas in different regions or Availability Zones.
  * Offer greater flexibility for restoring your database to a specific point in time.
* **Disadvantages**:
  * Can be time-consuming to create and restore, especially for large databases.
  * Incur storage costs for the snapshot itself.

#### Backups
They are automated, incremental backups of your database that capture changes since the last backup.
* **Advantages**:
  * Automated and require minimal configuration.
  * More space-efficient compared to full snapshots as they only store changes.
  * Enable faster restoration compared to snapshots for recent data loss.
* **Disadvantages**:
  * Limited restore options - typically used for full database restoration to the most recent backup point.
  * Not suitable for creating read replicas or restoring to a specific point in time.

#### When to Use Snapshots and Backups
* **Use Snapshots for**:
  * Disaster recovery to a specific point in time.
  * Creating read replicas across regions or Availability Zones.
  * Testing new database configurations or migrations.

* **Use Backups for**:
  * Automated disaster recovery to the most recent database state.
  * Improving recovery time objectives (RTO) for recent data loss.
  * Reducing administrative overhead for managing backups.


## Summary
![image](https://imgur.com/FYAYMhQ.png)
