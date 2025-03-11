
# AWS ELB & ASG 
## Elastic Load Balancer (ELB)
AWS **Elastic Load Balancer (ELB)** is a fully managed service that distributes incoming traffic across multiple targets (EC2 instances, containers, IPs) to improve application availability, fault tolerance, and scalability.

### 1. Vertical Scaling
- **Definition**: Increasing the capacity of a single instance (e.g., upgrading from a t2.micro to an m5.large).
- **Pros**: Simple, no need for architectural changes.
- **Cons**: Limited by hardware constraints, causes downtime during upgrades.

### 2. Horizontal Scaling
- **Definition**: Adding more instances to distribute the load across multiple resources.
- **Pros**: Better fault tolerance, improves availability, no downtime.
- **Cons**: Requires a load balancer to distribute traffic efficiently.

### 3. Load Balancing
- **Definition**: Evenly distributing incoming traffic across multiple backend resources.
- **Benefits**:
  - Prevents overload on a single resource.
  - Increases fault tolerance.
  - Improves response times by sending requests to the least loaded instances.

#### Types of AWS Load Balancers
1. **Application Load Balancer (ALB)**
   - Operates at **Layer 7** (Application Layer).
   - Routes requests based on content (host/path-based routing).
   - Best for microservices and container-based architectures.

2. **Network Load Balancer (NLB)**
   - Operates at **Layer 4** (Transport Layer).
   - Handles **millions of requests per second** with low latency.
   - Best for high-performance applications requiring TCP/UDP-based load balancing.

3. **Classic Load Balancer (CLB)**
   - Operates at both **Layer 4 & Layer 7**.
   - Legacy load balancer with limited functionality.
   - Not recommended for new applications.

4. **Gateway Load Balancer (GWLB)**
   - Designed for deploying **third-party virtual appliances** (firewalls, monitoring tools).
   - Routes traffic to security appliances before reaching the backend.

### 4. High Availability
- **Ensures application uptime** even if some instances fail.
- Load balancers and **multi-AZ deployments** help achieve high availability.
- Spreads traffic across multiple Availability Zones (AZs).

### 5. Elasticity
- **Dynamically scales resources** based on demand.
- Works with **Auto Scaling Groups (ASG)** to launch or terminate instances automatically.


## Auto Scaling Group (ASG)
AWS **Auto Scaling Group (ASG)** automatically manages EC2 instance scaling based on demand.

### How ASG Works
1. **Defines a group of EC2 instances** managed together.
2. **Monitors performance metrics** (CPU usage, memory, requests per second).
3. **Automatically adds or removes instances** based on scaling policies.

### Benefits of ASG
- **Cost Optimization**: Reduces costs by scaling down during low demand.
- **Improved Availability**: Ensures sufficient resources to handle traffic.
- **Fault Tolerance**: Replaces unhealthy instances automatically.

### Types of Scaling Policies
1. **Dynamic Scaling**  
   - Responds to real-time metrics (e.g., increases instances when CPU > 70%).  
   - Uses **CloudWatch alarms** to trigger scaling actions.

2. **Scheduled Scaling**  
   - Adds or removes instances at specific times (e.g., increase at peak hours).  
   - Useful for predictable traffic patterns.

3. **Predictive Scaling**  
   - Uses machine learning to **anticipate future demand** and scale accordingly.

## Flow Diagram of ELB and ASG
```markdown
    +----------------------+
    |      Users          |
    +----------------------+
               |
               v
    +----------------------+
    | Elastic Load Balancer|
    +----------------------+
       /        |        \
      v         v         v
+--------+  +--------+  +--------+
|  EC2   |  |  EC2   |  |  EC2   |  <= Auto Scaling Group
|Instance|  |Instance|  |Instance|
+--------+  +--------+  +--------+
```

- **ELB** distributes incoming traffic across **EC2 instances**.
- **ASG** ensures instances are automatically added or removed **based on demand**.


## Key Differences: ELB vs ASG
| Feature           | ELB (Elastic Load Balancer) | ASG (Auto Scaling Group) |
|------------------|---------------------------|---------------------------|
| **Purpose**      | Distributes traffic       | Adjusts the number of instances |
| **Scaling**      | Doesn’t scale instances   | Adds/removes instances dynamically |
| **Fault Tolerance** | Redirects traffic to healthy instances | Replaces unhealthy instances |
| **Traffic Handling** | Balances load across multiple instances | Ensures the right number of instances |
| **AWS Services Used** | ALB, NLB, CLB, GWLB | CloudWatch, EC2 |


## Conclusion
- **ELB ensures high availability** by distributing traffic among multiple instances.
- **ASG ensures elasticity** by adding/removing EC2 instances automatically.
- Together, **ELB and ASG provide a resilient, cost-effective, and scalable architecture** for AWS applications.
