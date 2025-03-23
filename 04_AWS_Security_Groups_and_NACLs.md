# AWS Security Groups and NACLs

## Security Group
- Acts as a virtual firewall, controlling the inbound and outbound traffic to and from EC2 instances. 
- It defines a set of rules that specify which network traffic can reach instances. 
- Security groups act at the **instance level**.
- Can create different security groups for various instances, controlling how they communicate with each other and the internet.
- They can be added or removed from running instances; the changes take effect immediately.
- Can attach **up to five security groups** to a single EC2 instance. 
- Can attach the same security group to multiple EC2 instances.
- Security group consists of security rules.

### Inbound and Outbound Traffic
- **Inbound traffic** refers to traffic that originates **outside** the VPC and attempts to reach instances. Security group rules control which inbound traffic is allowed (e.g., SSH, HTTP).
- **Outbound traffic** refers to traffic originating from instances and attempting to reach resources outside the VPC (e.g., the Internet and other VPCs). 
  - Security groups do not control outbound traffic by default. AWS **allows all outbound** traffic by default **except port 25** when we create an instance.

### Security Rules
- Security rules are the individual settings within security groups that dictate traffic permissions.
- They specify protocols, ports, and IP ranges allowed or denied for inbound or outbound traffic.



## NACLs (Network Access Control Lists)
- Control traffic coming into and going out of a subnet (a part of the VPC network). 
- NACLs have a list of rules that either allow or deny traffic based on IP addresses and port numbers. 
- NACLs do not track connections like security groups do. If you allow incoming traffic on a certain port, you must also create a rule to explicitly allow the outgoing response traffic.
- NACLs and security groups can be used together for better security. 
- **NACLs act at the subnet level**.

### How does NACL numbering work?
- Each rule in a NACL has a number. The lower the number, the higher the priority. AWS evaluates NACL rules starting with the lowest numbered rule. 
- If a packet matches a rule, the action specified in the rule (allow or deny) is applied, and the remaining rules are not evaluated.
- **Example**: In case of a rule allowing traffic and another denying the same traffic. In that case, the rule with the lower number will take precedence because NACL rules are evaluated in order from the lowest number to the highest number.

### Example Scenario

| Rule Number | Type       | Protocol | Port Range | Source CIDR       | Action |
|-------------|------------|----------|------------|-------------------|--------|
| 100         | HTTP       | TCP      | 80         | 0.0.0.0/0         | ALLOW  |
| 200         | HTTP       | TCP      | 80         | 0.0.0.0/0         | DENY   |
| *           | ALL Traffic| ALL      | ALL        | 0.0.0.0/0         | DENY   |

#### Evaluation Process
**Incoming HTTP Request**:
 - Source IP: 198.51.100.23
 - Destination Port: 80

**Step-by-Step Evaluation**:
- The request first matches **Rule 100**, which allows HTTP traffic from any IP address.
- Since the traffic is allowed by Rule 100, it is permitted, and no further rules are evaluated.


### Traffic Flow in AWS
#### Inbound Traffic (Coming to an EC2 Instance)
- Step 1: The traffic first hits the NACL (Subnet Level).
- Step 2: If the NACL allows the traffic, it moves to the Security Group (Instance Level).
- Step 3: If the Security Group also allows the traffic, it reaches the EC2 instance.

#### Outbound Traffic (Leaving an EC2 Instance)
- Step 1: The Security Group checks if the outgoing traffic is allowed.
- Step 2: If allowed, the traffic moves to the NACL.
- Step 3: If the NACL allows the traffic, it leaves the subnet.

> **Note**: 
    > - AWS primarily follows a default deny policy, allowing only explicitly permitted traffic.
    > - While it's possible to configure security groups to deny.
    > - NACLs are stateless (they treat each request independently), while security groups are stateful (they remember past traffic).