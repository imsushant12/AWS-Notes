## Amazon RDS Read Replicas

A read replica is a read-only copy of your primary Amazon RDS database instance. 
It helps distribute read traffic and improve the performance of your primary database by serving read queries from the replica.

#### Advantages of Amazon RDS Read Replicas
* **Improved Performance:** Reduces load on your primary database, allowing it to handle write operations more efficiently.
* **Scalability:**  Easily create additional read replicas to handle increased read traffic.
* **Disaster Recovery:**  Use a read replica for failover in case your primary database becomes unavailable.

#### Disadvantages of Amazon RDS Read Replicas
* **Eventual Consistency:**  Data on the replica might lag slightly behind the primary due to asynchronous replication.
* **Limited Functionality:**  Read replicas are read-only and cannot be used for write operations (e.g., inserts, updates, deletes).
* **Additional Cost:**  Incurs costs for storage and compute resources used by the read replica.

#### How AWS Makes It Work?
When you create a read replica, AWS takes a snapshot of your primary database and uses it to create the replica instance. The replica then applies changes from the primary database asynchronously (not in real-time) to maintain consistency. AWS manages the replication process, ensuring updates are reflected on the replica.

#### Things You Can't Do with Read Replicas
* You cannot perform write operations (insert, update, delete) on a read replica.
* You cannot use them for administrative tasks typically done on the primary database (e.g., creating users, modifying database schema).
* Due to replication lag, there may be a delay in data synchronization between the primary database and read replicas, leading to potential consistency issues for applications that require real-time data access.

### Synchronization
Read replicas are synchronized with the actual database through asynchronous replication, where changes made to the primary database are captured in binlog files and transmitted to the read replica instance. While read replicas provide a near-real-time copy of the primary database, there may be a delay (replication lag) between changes being made on the primary database and their propagation to read replicas. As a result, read replicas may not always be in sync with the primary database, particularly during periods of high write activity or network latency.


## Summary
![image](https://imgur.com/qllGOeE.png)
