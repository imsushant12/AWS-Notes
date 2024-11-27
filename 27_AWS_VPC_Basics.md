## VPC Networking on AWS

### VPC (Virtual Private Cloud)
Imagine VPC as a gated community within the vast AWS cloud. It provides a logically isolated network segment where you can securely deploy your AWS resources.

An overview of the VPC and its working:
![VPC](https://imgur.com/HKjSph1.png)

#### Benefits of VPC
* **Enhanced Security**: Isolate your resources from the public internet and other AWS accounts, minimising the attack surface and potential security breaches.
* **Improved Scalability**: Easily add or remove resources within your VPC as your needs evolve. You won't have to worry about impacting other VPCs or the broader AWS environment.
* **Granular Control**: Define your IP address space (CIDR block) and network configuration, giving you complete control over how your resources communicate within the VPC.

#### Use Cases of VPC
* **Secure Applications**: Host private applications that don't require public internet access, such as internal databases or backend services.
* **Multi-Tier Architectures**: Build secure, layered architectures with separate public and private tiers. Public-facing web servers can reside in a public subnet, while core application logic and databases can be placed in private subnets for added protection.
* **Compliance Requirements**: Meet industry regulations or internal policies that mandate data isolation within a secure virtual network environment.

#### Scope and Limitations of VPC
* A VPC is regional and exists within your chosen AWS region.
* You can create multiple VPCs within a region to further segment your network based on project requirements or security best practices.
* You manage security groups and network access control lists (ACLs) within the VPC. These tools define how traffic flows within and outside your VPC.

## Key VPC Components
### CIDR Block
Similar to a postal code for your VPC, a CIDR block defines the range of IP addresses allocated to your VPC. When creating a VPC, specify a CIDR block (e.g., 10.0.0.0/16) that determines the available IP addresses for your resources within that VPC.

### Subnet
A subnet is a logical subdivision within your VPC. Think of it as a neighbourhood within the gated community (VPC). You can create multiple subnets to further segment your network based on function or security needs.

**Benefits of Subnets**
* **Enhanced Security**: You can create additional security boundaries within your VPC by isolating resources within subnets.
* **Improved Manageability**: Grouping resources with similar needs (e.g., web servers in a public subnet, databases in a private subnet) simplifies network management.

### Route Table
A virtual routing table acts like a traffic map for your VPC. Each subnet is associated with a route table that defines how traffic is directed within the VPC and to the internet.

**Benefits of Route Tables**
* **Traffic Control**: Route tables provide granular control over traffic flow within your VPC and to the internet.
* **Outbound Connections**: Route tables define how traffic from your VPC reaches the appropriate gateway (internet gateway or NAT gateway) for outbound connections.

### Internet Gateway
The internet gateway is the exit point for your VPC to access the public internet. Resources in public subnets with public IP addresses can directly communicate with the internet through the internet gateway.

### NAT Gateway (Highly Available Managed Service)
A NAT gateway allows resources in private subnets (without public IP addresses) to access the internet. It acts as an intermediary, translating private IP addresses to its public IP for outbound internet traffic.  

**Benefits of NAT Gateway**:

* **Managed Service**: Unlike NAT instances (EC2 instances configured for NAT), NAT gateways are managed by AWS, eliminating the need for additional instance management overhead.
* **Scalability**: NAT gateways are highly available and can scale automatically to meet traffic demands.
* **Simplicity**: NAT gateways offer a more straightforward and reliable solution for outbound internet access from private subnets compared to NAT instances. 

## Summary
![Summary](https://i.imgur.com/K2LsHSR.png)