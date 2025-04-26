# AWS - Instance Types

## Instance Naming
- Example: **`t2.micro`**:
  - **First letter (t)**: Instance family (e.g., t - Burstable, m - General Purpose, c - Compute Optimized)
  - **Number (2)**: Generation within the family (higher number usually signifies newer architecture)
  - **Size (micro)**: Resource configuration (micro - smallest, large, xlarge, etc.)

## Types of Instances
- **General Purpose (A Series, M Series)**: Balanced computing, memory, and storage for various applications (e.g., web servers and databases)
- **Compute Optimized (C Series, R Series)**: High processing power for computationally intensive workloads (e.g., scientific computing, video processing)
- **Memory Optimized (R Series, Z Series)**: Large amounts of memory for in-memory analytics and databases (e.g., real-time analytics, large datasets)
- **Storage Optimized (D Series, ST Series)**: High storage capacity and throughput for data-intensive applications (e.g., log processing, data warehousing)
- **Accelerated Computing (P Series, G Series)**: Specialized hardware for workloads requiring GPUs, FPGAs, or machine learning accelerators (e.g., graphics rendering, scientific simulations)

## Other Instance Types
- **Reserved Instances**: They offer significant discounts compared to on-demand pricing but require a commitment in advance
   - **All Upfront**: Pay the entire reserved instance cost in advance for the most significant discount
   - **Partial Upfront**: Pay a more minor advance cost with a lower hourly rate
   - **Scheduled Instances**: Reserve instances for specific periods each day or week
   - **Standard Reserved Instances**: These provide the highest discount rates among all Reserved Instance types. They offer the lowest hourly rates but provide less flexibility regarding instance attribute modification
   - **Convertible Reserved Instances**: While offering slightly lower discounts than Standard RIs, Convertible RIs provide more flexibility. During the term, users can modify instance attributes like instance type, operating system, or tenancy
- **Spot Instances**: They can offer significant cost savings, but their availability can fluctuate
   - **One-Time Spot Instances**: Bid on a specific instance for a set duration. These instances suit short-term, transient workloads with flexible start and end times
   - **Interrupt Spot Instances**: AWS can reclaim the instance anytime, but they offer the lowest prices
   - **Persistent Spot Instances**: These instances continue running until the user terminates them or the Spot price exceeds the bid price. They are ideal for workloads that require continuous availability with potential interruptions
   - **Spot Blocks**: They provide a defined duration for running instances, ensuring stability and predictability. Users specify a duration (1 to 6 hours) and a maximum price, and AWS guarantees capacity

## Important Instance Families
- **General Purpose**: A Series (cost-optimized), M Series (balanced)
- **Compute Optimized**: C Series (high CPU), R Series (memory-optimized CPUs)
- **Memory Optimized**: R Series (powerful CPUs, high memory), Z Series (extreme memory)
- **Storage Optimized**: D Series (HDD-based), ST Series (SSD-based)

## Load Testing
Load testing simulates real-world traffic to assess an application's performance under load. It helps in 
- Choosing the right instance type by identify the instance that can handle expected traffic without compromising performance
- Scale the infrastructure for future growth and ensures that instances can handle the increased load

## AWS Pricing
- Charged based on the usage of resources (**Pay-as-you-go**) per hour or second (e.g., instance type, storage, network traffic)
- **On-Demand Instances**: Ideal for temporary workloads or unpredictable usage patterns
- **Reserved Instances**: Purchase capacity in advance for a fixed term (1 or 3 years) at a significant discount
- **Spot Instances**: Bid on unused EC2 capacity for cheap prices, but availability is not guaranteed
- **OS**: Pricing typically remains the same across various Linux distributions. Windows and specialized licenses may have additional costs

## Factors Affecting Discount
- Larger, more powerful instances generally cost more
- Pricing may vary depending on the AWS region where the instance is to be launched
- Longer commitment terms offer more discounts

## Dedicated Hosts
Dedicated hosts offer physical servers dedicated to use in an AWS data centre which provides:
  - Consistent performance by eliminating the possibility of other instances on shared hardware
  - Provides more control over the underlying hardware and software environment

## Saving Plans
Saving Plans offer a commitment to a specific usage level over a one or 3-year term in exchange for a discount on overall computing costs across various instance types and services.