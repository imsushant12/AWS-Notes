## Amazon DynamoDB

Amazon DynamoDB is a NoSQL database service offered by Amazon Web Services (AWS). It's a high-performance and scalable database designed for the cloud. Unlike traditional relational databases, DynamoDB doesn't use rows and columns. Instead, it stores data as key-value pairs with flexible schemas.

Important Points
- Serverless
- Scale Up/Down easily (Automatic Scaling)
- Idle Cost Saving
- On-demand Pricing (Pay only for read/write)
- Zero Downtime

## DAX (DynamoDB Accelerator)

## DynamoDB Global Table



#### Advantages of DynamoDB
* **Fast Performance:** Delivers high throughput and low latency for demanding applications.
* **Scalability:** Easily scales storage and capacity on-the-fly to meet changing data needs.
* **Flexibility:** Accommodates various data structures and access patterns.
* **Cost-Effective:** Pay only for the resources you use (provisioned throughput or on-demand).
* **Highly Available:** Offers built-in redundancy and automatic failover for continuous operation.

#### Disadvantages of DynamoDB
* **Limited Schema Support:**  Not ideal for complex queries requiring joins or aggregations across different tables.
* **Eventual Consistency:** Data updates might have a slight delay in reflecting across all replicas.
* **Learning Curve:** Understanding data modeling for NoSQL databases can require a different approach.

#### Use Cases of DynamoDB
* **Real-time Analytics:**  Process and analyze large data streams efficiently.
* **Mobile Backends:**  Store and manage data for mobile applications.
* **IoT Applications:**  Scale to handle data from numerous connected devices.
* **Gaming Leaderboards:**  Provide fast and consistent updates for player rankings.
* **Catalog Management:**  Store product information and user preferences efficiently.


### How DynamoDB Works?
* Data is stored in tables, but instead of rows and column s, it uses key-value pairs.
* Each table has a primary key that uniquely identifies an item (data element). This key can be a single element (partition key) or a combination (partition key and sort key).
* Partition key:  This is a mandatory element that acts like a folder. It efficiently distributes data across multiple servers for scalability and performance.

### Creating Tables in DynamoDB
* You define the table structure, including the primary key and data types for attributes.
* You provision read and write capacity units based on your expected request rate.

### Data Size Limits
* An individual item can have up to 400 KB of data.
* There are no strict limitations on the number of rows (items) or columns (attributes) in a table. However, very large tables can impact performance and cost.

### Partition Key
DynamoDB partitions data based on the partition key. Items with the same partition key are stored together in the same partition. It is similar to the primary key of databases.

* The partition key plays a crucial role in how DynamoDB stores and retrieves data.
* It determines how data is distributed across servers and how efficiently DynamoDB can access specific items.
* Choose a partition key that reflects how you'll most frequently query your data. 
* DynamoDB automatically scales partitions to accommodate increasing data volume and throughput requirements.

## Summary
![image](https://imgur.com/KHCZkiH.png)
