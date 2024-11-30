## Connecting VPCs: VPC Peering Explained

VPC peering allows you to establish private network connections between VPCs within the same AWS account, or even between VPCs in different accounts and regions. This enables resources in peered VPCs to communicate with each other directly over a private and secure connection, without needing to traverse the public internet.

#### Use Cases of VPC Peering
* **Shared Resources**: Securely access resources in a separate VPC, such as a database in a private VPC from a web application in a public VPC.
* **Hybrid Cloud**:  Extend your on-premises network to a VPC using a VPN connection, and then VPC peering to connect the extended VPC to other VPCs in your AWS environment.
* **Multi-Tier Applications**:  Deploy different tiers of your application (e.g., web servers, databases) across separate VPCs for improved security and scalability, while allowing them to communicate privately.

#### Benefits of VPC Peering
* **Security**: Keeps communication private within the AWS network, minimizing the attack surface.
* **Performance**:  Provides a lower latency and more reliable connection compared to using the internet.
* **Scalability**:  Easily scales to accommodate growing network traffic between peered VPCs.
* **Cost-Effective**:  Data transfer within the same Availability Zone (AZ) is free for peered VPCs.

#### Limitations of VPC Peering
* **Transitive Peering Not Supported**: You cannot establish a transitive connection where VPC A peers with VPC B, and VPC B peers with VPC C, and expect traffic to flow between VPC A and C. Each VPC peering connection is a direct one-to-one connection.
* **Region Limitation**: VPC peering can only be established between VPCs in the same region by default. Inter-region peering requires additional configuration using AWS Transit Gateway.
* **Account Management**: Peering between VPCs in different accounts requires approval from both account owners.


### Types of VPC Peering
* **Intra-Region Peering**: Connects VPCs within the same region. This is the most common type of VPC peering.
* **Inter-Region Peering**: Connects VPCs across different AWS regions using AWS Transit Gateway.

### Ways to Establish VPC Peering
* **VPC Console**: Use the AWS Management Console to initiate and manage VPC peering connections.
* **AWS CLI**:  Use the AWS Command Line Interface to automate VPC peering configuration through scripts.
* **SDKs**: Leverage AWS SDKs for programmatic creation and management of VPC peering connections from your development environment.


### When VPC Peering Cannot Take Place
* **VPCs in Different Partitions**: VPCs cannot be peered if they are located in different AWS partitions (e.g., GovCloud).
* **Resource Limits**:  There are limitations on the number of peering connections a VPC can have.
* **Outstanding Peering Requests**: A VPC peering request cannot be initiated if there are pending requests for that VPC.
* When the CIDR blocks of the VPCs overlap.


By understanding VPC peering and its limitations, you can design secure and scalable network architectures within your AWS environment.


### Summary
![image](https://imgur.com/MXAhBEV.png)
