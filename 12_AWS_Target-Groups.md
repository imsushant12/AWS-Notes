# Target Groups

## Target Group in AWS
- Acts as a load balancer's distribution point, directing incoming traffic to healthy target resources within application infrastructure
- Creates a pool of potential destinations for load balancer
- Monitors the health of targets to ensure only healthy resources receive traffic
- Define rules to distribute traffic based on factors like URL path, headers, or custom attributes. This allows for granular control over how traffic is sent to different targets within the group
- Helps to manage targets from a central location instead of configuring them individually within the load balancer
- **Limitations**:
  - Introduces an additional layer of configuration compared to directly connecting targets to the load balancer
  - Requires monitoring both the target group and individual targets for comprehensive health checks

## Types of Target Groups
### 1. Instance Target Group
- Routes traffic to EC2 instances within VPC
- Can specify targets by their unique Instance ID or IP address 
- This is the most common type used with load balancers for applications running on EC2 instances. It targets Amazon EC2 instances by instance ID or IP address
- **Target Selection**: Instance ID and IP Address
  - The targets are EC2 instances identified by their unique Instance IDs within the VPC
  - Can also define targets by their private or public IP addresses
- **Use Case**: 
  - Ideal for applications running on EC2 instances
  - It's the most common type used with load balancers like Application Load Balancer (ALB) and Network Load Balancer (NLB)
- **Benefits**: 
  - Straightforward setup for existing EC2 instances
  - Integrates well with features like Auto Scaling groups for dynamic scaling based on traffic
- **Limitations**:
  - Limited to EC2 instances within the same VPC (unless using Elastic IPs)

### 2. IP Target Group
- Routes traffic to resources identified by their IP addresses
- This flexibility allows targeting resources beyond EC2 instances in VPC, including on-premises servers, EC2 instances in different VPCs (with proper network connectivity), or any publicly accessible resource with a static IP address
- **Target Selection**: Targets are defined by their IP addresses
- **Use Case**: Suitable for targeting resources beyond EC2 instances within VPC. This could include:
  - On-premises servers
  - EC2 instances in a different VPC with appropriate network connectivity established
  - Publicly accessible resources with static IP addresses
- **Benefits**: Provides flexibility to include resources outside of VPC in the load balancing configuration
- **Limitations**:
  - Requires manual management of IP addresses for scaling or changes
  - In terms of security, need to ensure proper firewall rules are in place to restrict access from the load balancer to only the intended targets

### 3. Lambda Target Group
- A group specifically designed to route traffic to AWS Lambda functions
- Can define targets by their function name.
- Allows integration of serverless applications into load balancing architecture
- **Target Selection**: Targets specific Lambda functions by their function name
- **Use Case**: For serverless applications built on AWS Lambda functions
- **Benefits**:
  - Simplifies traffic routing for serverless applications
  - Scales automatically based on incoming traffic without managing individual instances
- **Limitations**:
  - Limited to Lambda functions within the same AWS region
  - Consider cold start times for Lambda functions when designing your application for optimal performance under high traffic.


### Related Terminologies
#### Target Registration
- The process of adding targets (EC2 instances, Lambdas, etc.) to a target group
- This can be done manually or through automation tools like AWS CloudFormation

#### Target Group Stickiness
- Configure a target group to maintain user sessions with specific targets for a defined duration
- This is useful for applications where user experience benefits from maintaining a connection with the same target during a session
