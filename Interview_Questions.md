1. **Have you implemented the public-private infrastructure in AWS?**
2. **What is the difference between stateful and stateless, for example NACL and subnet?**
3. **How does the traffic flow in VPC?**
4. **You have been assigned to design a VPC architecture for a 2-tier application. The application needs to be highly available and scalable. How would you design the VPC architecture?**

    Answer: In this scenario, I would design a VPC architecture in the following way.

    I would create two subnets: public and private. The public subnet would contain the load balancers and be accessible from the Internet, while the private subnet would host the application servers. 

    I would distribute the subnets across multiple Availability Zones for high availability and configure auto-scaling groups for the application servers.

5. **Your organisation has a VPC with multiple subnets. You want to restrict outbound internet access for resources in one subnet but allow outbound access for resources in another. How would you achieve this?**

    Answer: We can modify the route table associated with that subnet to restrict outbound internet access for resources in one subnet. In the route table, we can remove the default route (0.0.0.0/0) that points to an internet gateway. 

    This would prevent resources in that subnet from accessing the internet. We can keep the default route pointing to the internet gateway for the subnet where outbound internet access is required.

    > Note: Security groups alone cannot directly restrict outbound internet access in this scenario. Security Groups are stateful, meaning if you allow outbound traffic, the return traffic for established connections is automatically allowed.

6. **You have a VPC with a public and private subnet. Instances in the private subnet need to access the internet for software updates. How would you allow internet access for instances in the private subnet?**

    Answer: We can use a NAT Gateway or a NAT instance to allow internet access for instances in the private subnet. 

    We would place the NAT Gateway/instance in the public subnet and configure the private subnet route table to send outbound traffic to it. This way, instances in the private subnet can access the Internet through the NAT Gateway/instance.

7. **You have launched EC2 instances in your VPC, and you want them to communicate with each other using private IP addresses. What steps would you take to enable this communication?**

    Answer: By default, instances within the same VPC can communicate with each other using private IP addresses. 

    To ensure this communication, we need to ensure that the instances are launched in the same VPC and placed in the same subnet or subnets that are connected through a peering connection or a VPC peering link. 

    Additionally, we should check the security groups associated with the instances to ensure that the necessary inbound and outbound rules are configured to allow communication between them.

8. **You want to implement strict network access control for your VPC resources. How would you achieve this?** [IMPORTANT]

    Answer: Network access control lists (ACLs) can be used to implement granular network access control for VPC resources. 

    NACLs are stateless and operate at the subnet level. We can define inbound and outbound rules in the NACLs to allow or deny traffic based on source and destination IP addresses, ports, and protocols. 

    By carefully configuring NACL rules, we can enforce fine-grained access control for traffic entering and leaving the subnets.

9. **Your organisation requires an isolated environment within the VPC for running sensitive workloads. How would you set up this isolated environment?**

    Answer: To set up an isolated environment within the VPC, we can create a subnet with no internet gateway attached. 

    This subnet, known as an "isolated subnet", will not have direct internet connectivity. We can place the sensitive workloads in this subnet, ensuring they are protected from inbound and outbound internet traffic. 

    However, suppose these workloads require outbound internet access. In that case, we can set up a NAT Gateway or NAT instance in a different subnet and configure the isolated subnet's route table to send outbound traffic through the NAT Gateway/instance.

10. **Your application must securely access AWS services, such as S3, within your VPC. How would you achieve this?**

    Answer: To securely access AWS services within the VPC, we can use VPC endpoints. VPC endpoints allow VPC instances to communicate privately with AWS services without requiring internet or NAT gateways. 

    We can create VPC endpoints for specific AWS services, such as S3 and DynamoDB, and associate them with the VPC. 

    This enables secure and efficient communication between the instances in the VPC and the AWS services.

11. **What is the difference between NACL and Security groups? Explain with a use case?**

    Answer: For example, if I want to design a security architecture, I would combine NACLs and security groups. I would configure NACLs at the subnet level to enforce inbound and outbound traffic restrictions based on source and destination IP addresses, ports, and protocols. NACLs are stateless and can provide an additional layer of defence by filtering traffic at the subnet boundary.

    I would leverage security groups to control inbound and outbound traffic at the instance level. Security groups are stateful and operate at the instance level. By carefully defining security group rules, I can allow or deny specific traffic to and from the instances based on the application's security requirements.

    By combining NACLs and security groups, I can achieve granular security controls at both the network and instance levels, providing defence-in-depth for sensitive applications.

12. **What is the difference between IAM users, groups, roles and policies?**

    Answer: **IAM User**: An IAM user is an identity within AWS representing an individual or application needing access to AWS resources. IAM users have permanent, long-term credentials, such as a username and password or access keys (Access Key ID and Secret Access Key). IAM users can be assigned directly to IAM policies or added to IAM groups for easier permissions management.
   
    **IAM Role**: An IAM role is similar to an IAM user but is not associated with a specific individual. Instead, it is assumed by entities such as IAM users, applications, or services to obtain temporary security credentials. IAM roles are helpful when you want to grant permissions to entities that are external to your AWS account or when you want to delegate access to AWS resources across accounts. IAM roles have policies attached to them that define the permissions granted when the role is assumed.

    **IAM Group**: An IAM group is a collection of IAM users. By organising IAM users into groups, you can manage permissions collectively. IAM groups make it easier to assign permissions to multiple users simultaneously. Users within an IAM group inherit the permissions assigned to that group. For example, you can create a "Developers" group and assign appropriate policies to grant permissions required for developers across your organisation.
   
    **IAM Policy**: An IAM policy is a document that defines permissions and access controls in AWS. IAM policies can be attached to IAM users, IAM roles, and IAM groups to determine what actions can be performed on which AWS resources. IAM policies use JSON (JavaScript Object Notation) syntax to specify permissions, which can be created and managed independently of the users, roles, or groups. IAM policies include statements that include the actions allowed or denied, the resources on which the actions can be performed, and any additional conditions.

13. **You have a private subnet in your VPC that contains several instances that should not have direct internet access. However, you still need to be able to access these instances securely for administrative purposes. How would you set up a bastion host to facilitate this access?**

    Answer: To securely access the instances in the private subnet, you can set up a bastion host (also known as a jump host or jump box). The bastion host acts as a secure entry point to your private subnet. 

    Here's how you can set up a bastion host:

    Create a new EC2 instance in a public subnet to serve as the bastion host. Ensure that this instance has a public IP address or is associated with an Elastic IP address for persistent access.
        
    Configure the security group for the bastion host to allow inbound SSH (or RDP for Windows) traffic from your IP address or a restricted range of trusted IP addresses. This limits authorized administrators' access to the bastion host only.

    Place the instances in the private subnet and configure their security groups to allow inbound SSH (or RDP) traffic from the bastion host security group.

    SSH (or RDP) into the bastion host using your private key or password. From the bastion host, you can SSH (or RDP) into the instances in the private subnet using their IP addresses.

