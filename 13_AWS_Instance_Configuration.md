# AWS Instance Configuration

It includes the several configuration options included in the launch of an instance which influence instance's behavior, security, and cost

##  Termination Protection and Stop Protection
### Termination Protection
- It prevents accidental termination of running instance
- A confirmation prompt will popup before terminating of an instance if termination protection is enabled
- It saves instance from unintended instance deletion

### Stop Protection
- It prevents accidental stopping of instance
- A confirmation prompt will popup before stopping of an instance if termination protection is enabled

## Instance States - Hibernation and Stopping
### Hibernate State
- It is a power-saving option that puts instance in a low-power state while preserving its memory content
- Useful when there is a need to temporarily stop the instance but also want to resume it quickly later in its previous state
  
> **Note**: Hibernation is not supported for all instance types

### Stopping vs Hibernation
- Stopping an instance completely powers it down. As a result, it takes longer restart time compared to hibernation
- Can choose stopping when there is no need of the instance for an extended period and want to save costs

## Monitoring Instance - CloudWatch Monitoring
- By default, AWS CloudWatch collects basic monitoring data of instances
- If **Detailed CloudWatch Monitoring** is enabled, it provides a more detailed view of instance's performance metrics
  - It includes data points captured at a higher frequency, offering greater granularity for troubleshooting and performance optimization

> **Note**: Enabling detailed monitoring comes with additional charges

## Cost Management - Credit Specifications and Capacity Reservations
### Credit Specifications
- Only applies to specific instance types purchased through AWS Committed Use Discounts
- Allows defining how the upfront discount is distributed across hourly charges throughout the commitment period
- Helps to optimize costs based on usage patterns

### Capacity Reservations
- Reserving a set number of instances in a specific Availability Zone for a fixed period helps save costs compared to on-demand pricing
- It ensures that the required instances are always available at a lower price

## Placement and Isolation - Placement Groups and Tenancy
### Placement Groups
- Grouping instances within a specific Availability Zone using a placement group can be useful for applications with high network traffic or shared storage
- When these instances are placed close together physically, it optimize network performance by reducing latency

### Tenancy
- When launching an instance, there is an option to choose between a shared or dedicated tenancy model
- In a **shared tenancy**, instance resides on the same underlying hardware as other customer instances
  - This is the lower-cost option but may experience some performance variability
- In a **dedicated tenancy**, instance has exclusive access to the physical hardware
  - It potentially offers better performance and isolation but at a higher cost

## Network Configuration - Network Interfaces
- A network interface (ENI) acts like a virtual network adapter for instance
- Allows the instance to connect to a VPC and communicate over the network

One or more ENIs can be attached to an instance for various reasons:

#### Multiple IP Addresses
- Each ENI can have its own private and/or public IP address which enables the instance to have multiple network identities
- Can be useful for specific applications requiring multiple IP configurations

#### Security Isolation
- Attaching separate ENIs to different subnets within VPC helps in isolating network traffic for different parts of application, enhancing security

#### Scalability
- Can dynamically add or remove ENIs from a running instance to adjust its network capacity as needs evolve
- Provides flexibility in scaling instance's network capabilities