# AWS Instances

- They are virtual servers in the AWS cloud that provide processing power, memory, storage, and networking capabilities. They can be configured and launched based on specific needs.
- An instance runs an OS and various applications and software can be installed on it.

## Types of AWS Instances
- **General Purpose**: Suitable for a wide range of applications. It offers a balance of CPU, memory, and storage. 
  - Example: `t2.micro`, `m5.large`
- **Compute Optimized**: Designed for computationally intensive workloads that requires high processing power. 
  - Example: `c5.xlarge`, `r5.metal`
- **Memory Optimized**: Ideal for applications requiring large amounts of memory, like databases in-memory analytics. 
  - Example: `r5.large`, `z1d.large`
- **Storage Optimized**: Offer high storage capacity and throughput for data-intensive applications. 
  - Example: `st1.xlarge`, `d2.xlarge`
- **Accelerated Computing**:  These are ideal for machine learning, scientific simulations, and video editing 
  - Example: For specialized workloads (e.g., P4d, G4dn instances), include GPUs (Graphics Processing Units) or FPGAs (Field-Programmable Gate Arrays)..


## Most Commonly Used Instances
- **Free Tier**:
  - **`t2.micro`**: A general-purpose instance with limited CPU power but suitable for low-traffic websites or learning purposes.
- **Paid**:
  - **`m5.large`**: A versatile general-purpose instance that balances CPU, memory, and storage for various applications.
  - **`c5.xlarge`**: A compute-optimized instance with high processing power for computationally intensive workloads.


## EC2 Instance
- Elastic Compute Cloud (EC2) instances are virtual servers in the AWS cloud.
- It works on the principle - pay only for the resources you use.
- EC2 instance can be accessed using various methods depending on the OS:
  - **Windows**: Using Remote Desktop Connection (RDP) with instance's public IP address or DNS name.
  - **Linux/Mac**: Using SSH client with instance's public IP address, DNS name, and private key.


### Suspending and Terminating Instances 
- **Stop Instance**: Stops the instance but charges for storage and Elastic Block Store (EBS) volumes attached to it.
- **Terminate Instance**: Permanently deletes the instance and associated data, stopping all charges.

> **Note**: EBS is a service that provides persistent block storage volumes for use with EC2 instances. These volumes are similar to physical hard drives and can be attached to one or more EC2 instances in the same Availability Zone.


## How to choose the right instance
- Identify the primary purpose of instance (e.g., web server, database server).
- Select the CPU type and core count based on workload requirements.
- Choose the appropriate amount of memory to support applications efficiently.
- Select the storage type (e.g., SSD, HDD) and capacity based on data needs.
- Choose the preferred operating system for instance.
- Consider the pricing of different instance types to optimize budget.