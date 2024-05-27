# AWS Security Groups and NACLs

A security group in AWS acts as a virtual firewall, controlling the inbound and outbound traffic to and from your EC2 instances. It defines a set of rules that specify which network traffic can reach your instances. 

**Security groups act at the instance level**.

### Need and Use Case
Security groups are essential for securing your EC2 instances by:
* **Restricting unauthorised access**: You can define rules to allow only specific traffic (e.g., SSH access from your IP address) and block all other attempts.
* **Segmenting your network**: You can create different security groups for various instances, controlling how they communicate with each other and the internet.
* **Complying with security regulations**: Security groups can help you meet security compliance requirements by restricting access to sensitive data.

### Adding/Deleting Security Groups to Running Instances
Security groups can be added or removed from running instances; the changes take effect immediately.

#### Important Points
* **Multiple Security Groups to One Instance**: Yes, you can attach **up to five security groups** to a single EC2 instance. This allows you to combine different security rules for more granular control.
* **Multiple Instances to One Security Group**: You can attach the same security group to multiple EC2 instances. If the instances have similar access requirements, this simplifies management.

### Inbound and Outbound Traffic
* **Inbound traffic** refers to traffic that originates **outside** the VPC and attempts to reach your instances. Security group rules control which inbound traffic is allowed (e.g., SSH, HTTP).
* **Outbound traffic**: This refers to traffic originating from your instances and attempting to reach resources outside your VPC (e.g., the Internet and other VPCs). Security groups do not control outbound traffic by default. AWS allows all outbound traffic by default except port 25 when we create an instance.

### Security Rules
- Security rules are the individual settings within security groups that dictate traffic permissions.
- They specify protocols, ports, and IP ranges allowed or denied for inbound or outbound traffic.

A security rule defines a specific allowance or denial of traffic based on various criteria:
* **Protocol**: Specifies the type of communication (e.g., TCP, UDP, ICMP).
* **Port range**: Defines the ports on which the traffic is allowed or denied.
* **Source**: Specifies the IP address or security group of the source of the traffic.
* **Need**: Security rules define granular traffic control, ensuring only authorised communication.
* **Use Case**: They are vital for specifying which types of traffic are permitted or denied based on specific requirements.

### Free Tier vs Paid: Security Groups and Rules
* **Free Tier**: Free tier accounts have the same functionalities as paid accounts for creating and managing security groups and rules.
* **Paid**: Paid accounts offer additional features like:
    * **VPC Flow Logs**: Record network traffic information for further analysis.
    * **Network Access Control Lists (NACLs)**: Provide additional control over traffic flow at the subnet level.

### How do security groups operate in terms of denying traffic?
This statement explains how security groups operate by denying traffic. Here's a breakdown:

1. **Implicit Deny**: In security groups, there is an implicit deny rule, which means that by default, all traffic is denied unless it is explicitly allowed by a rule.
2. **Deny All Rules**: Unlike some firewall configurations where you can explicitly define a "deny all" rule to block all traffic, security groups in AWS don't have a built-in option for such regulations.
3. **Achieving Denial**: To achieve a similar effect as a "deny all" rule, you can create specific allow rules for the desired types of traffic and leave all other traffic implicitly denied. Unless you specifically allow traffic through a rule, it will be blocked due to the implicit deny default behaviour.

> **Note**: 
> - AWS primarily follows a default deny policy, allowing only explicitly permitted traffic.
> - While it's possible to configure security groups to deny.

### Creating Security Groups and Rules
You can create security groups and rules using various methods:
* **AWS Management Console**: This is a user-friendly web interface for managing your AWS resources.
* **AWS CLI (Command Line Interface)**: Offers a powerful command-line tool for managing AWS resources through scripts.
* **SDKs (Software Development Kits)**: Provide programmatic access to AWS services from various programming languages.

### Creating a Security Group and Rule in an EC2 Instance
While you cannot directly create a security group or rule **within** a running EC2 instance, you can manage them using the abovementioned methods. Here's a general process using the Management Console:

1. Go to the Amazon EC2 service in the Management Console.
2. Select "Security Groups" from the navigation pane.
3. Click on "Create Security Group."
4. Enter a name and description for the security group.
5. Click "Add Rule" to define inbound and outbound rules as needed.
6. Specify each rule's protocol, port range, source, and action (Allow or Deny).
7. Review and create the security group.
8. Once created, go back to your EC2 instance and edit its security group configuration to attach the newly created security group.


## NACLs
NACLs are like security guards at the entrance to your neighbourhood. They control traffic coming into and going out of a subnet (a part of your network). NACLs have a list of rules that either allow or deny traffic based on IP addresses and port numbers. NACLs don't remember past traffic. If you allow incoming traffic, you must also separate outgoing responses.

> **Note**: NACLs are stateless (they treat each request independently), while security groups are stateful (they remember past traffic).

You can use both NACLs and security groups together for better security. NACLs can provide a broad level of security, while security groups can provide more detailed control.

**NACLs act at the subnet level**. Even if the Security group allows a specific traffic and NACL does not, the traffic will not reach the instance.

### How does NACL numbering work?
Each rule in a NACL has a number. The lower the number, the higher the priority. AWS evaluates NACL rules starting with the lowest numbered rule. If a packet matches a rule, the action specified in the rule (allow or deny) is applied, and the remaining rules are not evaluated.

Example: If you have a rule that allows traffic (e.g., rule 100) and a later rule (e.g., rule 200) that denies the same traffic, the traffic will ultimately be allowed because the first matching rule (rule 100) will apply.

Suppose you have a rule allowing traffic and another denying the same traffic. In that case, the rule with the lower number will take precedence because NACL rules are evaluated in order from the lowest number to the highest number.

### Example Scenario
Let's say you have the following NACL rules:

| Rule Number | Type       | Protocol | Port Range | Source CIDR       | Action |
|-------------|------------|----------|------------|-------------------|--------|
| 100         | HTTP       | TCP      | 80         | 0.0.0.0/0         | ALLOW  |
| 200         | HTTP       | TCP      | 80         | 0.0.0.0/0         | DENY   |
| *           | ALL Traffic| ALL      | ALL        | 0.0.0.0/0         | DENY   |

### Evaluation Process
1. **Incoming HTTP Request**:
   - Source IP: 198.51.100.23
   - Destination Port: 80

**Step-by-Step Evaluation**:
- The request first matches **Rule 100**, which allows HTTP traffic from any IP address.
- Since the traffic is allowed by Rule 100, it is permitted, and no further rules are evaluated.

## Summary
![Summary1](https://i.imgur.com/n281Edt.png)
![Summary2](https://i.imgur.com/5C48mTR.png)