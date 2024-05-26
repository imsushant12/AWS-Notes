# AWS Instances

#AWS Instances are Virtual servers in the AWS cloud that provide processing power, memory, storage, and networking capabilities. You can configure and launch instances based on your specific needs.

An instance runs an operating system (like Windows or Linux), allowing you to install various applications and software.

### Choosing an Instance
* **Important points**:
    * **Purpose**: Identify the primary purpose of your instance (e.g., web server, database server).
    * **Processing power**: Select the CPU type and core count based on your workload requirements.
    * **Memory (RAM)**: Choose the appropriate amount of memory to support your applications efficiently.
    * **Storage**: Select the storage type (e.g., SSD, HDD) and capacity based on your data needs.
    * **Operating system**: Choose the preferred operating system for your instance.
    * **Cost**: Consider the pricing of different instance types to optimise your budget.


### Types of AWS Instances
* **General Purpose**: These instances are suitable for a wide range of applications, offering a balance of CPU, memory, and storage. (e.g., `t2.micro`, `m5.large`)
* **Compute Optimized**: Designed for computationally intensive workloads requiring high processing power. (e.g., `c5.xlarge`, `r5.metal`)
* **Memory Optimized**: Ideal for applications requiring large amounts of memory, like databases in-memory analytics. (e.g., `r5.large`, `z1d.large`)
* **Storage Optimized**: Offer high storage capacity and throughput for data-intensive applications. (e.g., `st1.xlarge`, `d2.xlarge`)
* **Accelerated Computing**: For specialised workloads (e.g., P4d, G4dn instances), include GPUs (Graphics Processing Units) or FPGAs (Field-Programmable Gate Arrays). These are ideal for machine learning, scientific simulations, and video editing.


### Commonly Used Instances
* **Free Tier**:
    * **``t2.micro``**: A general-purpose instance with limited CPU power but suitable for low-traffic websites or learning purposes.
* **Paid**:
    * **``m5.large``**: A versatile general-purpose instance that balances CPU, memory, and storage for various applications.
    * **``c5.xlarge``**: A compute-optimized instance with high processing power for computationally intensive workloads.


## EC2 Instance
Amazon Elastic Compute Cloud (EC2) instances are virtual servers in the AWS cloud that provide processing power, memory, storage, and networking capabilities. You can configure and launch instances on demand based on your specific needs and pay only for the resources you use.

* Multiple ways exist to create a free tier EC2 instance, including the AWS Management Console, AWS CLI, and SDKs. Here's a general process using the Management Console:
    1. Log in to your AWS Management Console.
    2. Go to the Amazon EC2 service.
    3. Click on ``Launch Instance``.
    4. Choose an Amazon Machine Image (AMI)—a pre-configured software bundle with an operating system. Select a free tier-eligible AMI.
    5. Select an instance type like ``t2.micro`` (free tier eligible).
    6. Configure other details like storage and networking.
    7. Review and launch the instance.

### Important Points
* Remember to choose a free tier eligible AMI and instance type.
* Be mindful of the free tier usage limits.
* Tag your resources for better organisation and billing management.

### Accessing an EC2 Instance
You can access your EC2 instance using various methods depending on your operating system:
* **Windows**: Use Remote Desktop Connection (RDP) with your instance's public IP address or DNS name.
* **Linux/Mac**: Use SSH client with your instance's public IP address, DNS name, and private key.


### Suspending and Terminating Instances and Billing
* **Stop Instance**: Stops the instance but charges for storage and Elastic Block Store (EBS) volumes attached to it.
    > Note: EBS is a service that provides persistent block storage volumes for use with EC2 instances. These volumes are similar to physical hard drives and can be attached to one or more EC2 instances in the same Availability Zone.
* **Terminate Instance**: Permanently deletes the instance and associated data, stopping all charges.

### Checking Bill
You can view your AWS bill in the AWS Billing and Cost Management console.

## Summary
![Summary](https://i.imgur.com/DwKAWL2.png)