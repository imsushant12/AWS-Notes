## Network Access Control Lists (NACLs) in AWS

A NACL (Network Access Control List) acts as a firewall within your VPC, controlling inbound and outbound traffic at the subnet level. It allows you to define rules that specify which network traffic can enter or leave your subnets.

#### Use Cases of NACL
* **Security**:  Refine security by restricting access to specific ports, protocols, and IP address ranges.
* **Subnet Segmentation**:  Further isolate subnets within your VPC by controlling traffic flow between them.
* **Compliance**:  Meet specific security requirements by implementing granular access controls.


#### Benefits of NACL
* **Enhanced Security**:  Provides an additional layer of security alongside security groups.
* **Subnet Level Control**:  Offers granular control over traffic flow at the subnet level.
* **Flexibility**:  You can create and manage multiple NACLs for different security needs.

#### Limitations of NACL
* **State**: NACLs are stateless, meaning they don't track connection states. They only evaluate individual packets based on the defined rules.
* **Subnet Level**:  NACLs apply to entire subnets, not individual instances.
* **Limited Rule Set**:  There's a maximum of 32766 rules per NACL, which might be insufficient for complex setups.

#### Role Numbers in NACL Rules
* Role numbers in NACL rules define the order in which the rules are evaluated. Lower numbered rules are evaluated first.
* The first matching rule determines whether to allow or deny the traffic.

#### NACL Attachment
* NACLs are attached to subnets within a VPC. Traffic entering or leaving a subnet is evaluated against the rules in the attached NACL.

### Default NACL vs. User-Created NACL
* **Default NACL**: Every VPC comes with a default NACL that allows all inbound and outbound traffic. It's recommended to create and use custom NACLs for better security.
* **User-Created NACL**: You can create custom NACLs with specific rules to restrict traffic flow according to your security needs.

### NACL vs. Security Groups
Both NACLs and security groups control traffic within your VPC, but they differ in scope and functionality:

* **Scope**:
    * **NACLs**: Apply to entire subnets.
    * **Security Groups**: Apply to individual ENIs (Elastic Network Interfaces) attached to your EC2 instances or other VPC resources.
* **Functionality**:
    * **NACLs**: Stateless, allow/deny rules based on source/destination IP, port, and protocol.
    * **Security Groups**: Stateful, allow/deny rules based on source/destination IP, port, protocol, and security group ID (enabling communication between instances with specific security groups).

In essence, NACLs provide broader subnet-level control, while security groups offer more granular control for individual resources. You can leverage both together for a comprehensive security strategy within your VPC.


### Summary
![image](https://imgur.com/q54msFj.png)
