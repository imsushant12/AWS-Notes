# AWS - VPC Components

### CIDR Block (Classless Inter-Domain Routing)
CIDR (Classless Inter-Domain Routing) block is a range of IP addresses specified using CIDR notation, which combines the IP address and subnet mask into a single expression. It resembles traditional IP address ranges but allows for more efficient allocation of IP addresses by specifying a network address and a variable-length subnet mask.

* Similar to a postal code, a CIDR block defines a range of IP addresses allocated to your VPC. Imagine it as a zip code for your virtual neighborhood within AWS.
* **Use Case**: When creating a VPC, you specify a CIDR block (e.g., 10.0.0.0/16) that determines the available IP addresses for resources within that VPC.

### Subnet
A subnet is a logical subdivision within your VPC, similar to a neighborhood within your gated community (VPC). You can create multiple subnets to further segment your network based on function or security needs.

#### Benefits of Subnet
* **Enhanced Security**: By isolating resources within subnets, you can create additional security boundaries within your VPC.
* **Improved Manageability**: Grouping resources with similar needs (e.g., web servers in a public subnet, databases in a private subnet) simplifies network management.

#### Scope and Limitations of Subnet
* Subnets are created within a VPC and inherit the VPC's overall security settings.
* You can further define security using security groups at the subnet or instance level.

#### Use Cases of Subnet
* **Deploying multi-tier applications**: You can separate front-end, back-end, and database resources into different subnets for better security and performance isolation.
* **Implementing high availability**: Distribute resources across multiple Availability Zones (AZs) by creating subnets in each AZ.


### Public vs. Private Subnets
* **Public Subnet**: Resources requiring internet access (e.g., web servers) should reside in a public subnet. These resources will have public IP addresses.
* **Private Subnet**: Resources that don't need direct internet access but need to communicate with other resources within the VPC (e.g., databases) should reside in a private subnet. These resources won't have public IP addresses by default.

### Communication with Private Subnet
* Resources within the same subnet can communicate directly.
* Private subnets cannot directly access the internet or public subnets by default. 

#### Via Public Subnet
* Set up a NAT gateway or NAT instance in the public subnet to allow outbound internet access for resources in the private subnet. This enables the private subnet resources to communicate with the internet while maintaining security by not exposing them directly.
#### Other Ways
* Establish a VPN connection or AWS Direct Connect to extend an on-premises network to the private subnet.
* Use VPC peering to connect multiple VPCs and allow communication between private subnets in different VPCs.


### NAT Gateway (Recommended)
* A NAT gateway acts as an intermediary, enabling outbound internet access for resources in private subnets. It translates private IP addresses to its public IP for internet traffic.
* **Benefits of NAT Gateway**
    * Managed service by AWS, eliminating instance management overhead.
    * Highly available and scalable.
    * Simpler and more reliable solution compared to NAT instances.
* **Limitations of NAT Gateway**
    * Less granular control over outbound traffic compared to a NAT instance.
* **Use Case of NAT Gateway**
    * Production environments with high outbound traffic requirements, where simplicity and scalability are priorities.

### NAT Instance (Less Common)
* A virtual machine running within a public subnet that translates private IP addresses to its public IP for outbound internet traffic.
* **Benefits of NAT Instance**
    * Offers more granular control over outbound traffic compared to a NAT gateway.
* **Limitations of NAT Instance**
    * Requires additional management and maintenance of the EC2 instance.
    * Single point of failure if the NAT instance fails.
* **Use Cases of NAT Instance**
    * Legacy applications requiring more control over outbound connections.
    * Scenarios where you need to inspect or modify outbound traffic.


### Route Table
* A virtual routing table acts like a traffic map for your VPC. Each subnet is associated with a route table that defines how traffic is directed within the VPC and to the internet.

#### Benefits of Route Table
* Control the flow of traffic within your VPC and to the internet.
* Route traffic to the appropriate gateway (internet gateway or NAT gateway) for outbound connections.

#### Scope and Limitations of Route Table
* Route tables apply to the subnets they are associated with.
* A route table can have multiple routes, with the most specific route (longest prefix match) being used for traffic forwarding.


### Internet Gateway
* The internet gateway acts as the exit point for your VPC to access the public internet. Resources in public subnets with public IP addresses can directly communicate with the internet through the internet gateway.

#### Benefits of Internet Gateway
* Enables resources in public subnets to communicate with the internet.


#### Scope and Limitations of Internet Gateway
* An internet gateway is required for any public-facing resources within your VPC.
* Cannot be used by private subnets to directly access the internet.

#### Working Together
* Route tables tell VPC where to send traffic based on the destination IP address.
* If the destination is on the internet and the subnet is public, the route table directs traffic to the internet gateway.
* If the destination is on the internet and the subnet is private, the route table directs traffic to the NAT gateway (assuming one is configured).

### Internet Gateway vs. NAT Gateway
* An internet gateway provides direct internet access for resources in public subnets.
* A NAT gateway enables outbound internet access for resources in private subnets by translating their private IP addresses