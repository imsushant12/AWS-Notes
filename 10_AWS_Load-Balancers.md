## AWS Load Balancers: Distributing Traffic for Your Applications

### What is a Load Balancer?
An AWS load balancer is a service that automatically distributes incoming traffic across multiple targets, such as EC2 instances, containers, or IP addresses. It acts as a single point of contact for clients, ensuring high availability and scalability for your applications.

#### Benefits of Load Balancers
* **Increased Availability**: Distributes traffic across healthy targets, preventing a single point of failure.
* **Improved Scalability**: Easily add or remove resources to handle traffic fluctuations.
* **Enhanced Performance**: Reduces latency by distributing traffic efficiently.
* **Simplified Management**: Provides a single entry point for managing traffic flow.

#### Use Cases for Load Balancers
* **Web Applications**: Distribute traffic across multiple web servers for high availability and performance.
* **Microservices Architectures**: Route traffic to individual microservices based on specific rules.
* **API Gateways**: Provide a single entry point for APIs while managing traffic distribution.
* **Highly Available Applications**: Ensure continuous uptime by distributing traffic across healthy targets.

#### Limitations of Load Balancers
* **Added Complexity**: Requires additional configuration and management compared to directly accessing instances.
* **Cost**: Incurs additional charges for the load balancing service.
* **Limited Control**: You cannot directly control traffic routing to specific targets within the load balancer.

### Load Balancing Algorithm
AWS load balancers primarily use a round-robin algorithm to distribute traffic across healthy targets. This means requests are sent to each target in a sequential order. However, other health-based factors can also influence routing decisions.

### Health Checks
Health checks are automated mechanisms used by load balancers to monitor the health of target resources. These checks ensure only healthy targets receive incoming traffic. Common health check parameters include:

* **Interval**: Frequency of health checks.
* **Timeout**: Maximum time a target can take to respond before being considered unhealthy.
* **Port**: Port on which the health check is performed.
* **Path**: Specific path or URL used for the health check.
* **Expected Code**: HTTP status code expected from a healthy target.

### Types of Load Balancers in AWS
#### 1. Classic Load Balancer (CLB)
It provides basic load balancing across multiple EC2 instances. It is now deprecated by AWS.
* **Benefits**: Easy setup, suitable for simple applications.
* **Limitations**: Limited features compared to ALB and NLB.
* **Use Cases**: Basic HTTP and HTTPS load balancing.

#### 2. Application Load Balancer (ALB)
It routes traffic at the application layer (HTTP/HTTPS) based on URL path, headers, or other criteria. Ideal for modern web applications.
* **Benefits**: Advanced routing, support for containerized applications, and HTTP/2.
* **Limitations**: Higher cost compared to CLB, requires familiarity with advanced features.
* **Use Cases**: Microservices architectures, containerized applications, and routing based on request content.

#### 3. Network Load Balancer (NLB)
It routes traffic at the network layer (TCP/UDP) based on IP addresses and ports. Offers high performance and scalability for low-latency applications.

* **Benefits**: High throughput, low-latency, and support for static IP addresses.
* **Limitations**: Limited to TCP and UDP traffic, higher cost compared to CLB.
* **Use Cases**: High-performance applications, TCP/UDP-based protocols, and extreme scalability requirements.

#### Gateway Load Balancer (GLB)
It distributes traffic across geographically dispersed VPCs or on-premises data centers.

#### Benefits and Limitations by Load Balancer Type

| Type | Benefits | Limitations | Use Cases |
|---|---|---|---|
| ALB | Flexible routing, advanced health checks | Slightly higher latency compared to NLB | Modern web applications, microservices |
| NLB | High performance, low latency | Limited routing options | High-throughput backends, gaming servers |
| GLB | Spans across geographically distributed environments | More complex configuration | Scalable applications across multiple locations |

### Cross-Zone Load Balancing
Distributes traffic across healthy targets in different Availability Zones within the same region. This enhances fault tolerance and ensures your application remains available even if an entire AZ fails.

The Load Balancers with Default Cross-Zone Support are:
* Application Load Balancer (ALB)
* Network Load Balancer (NLB)

### Load Balancer DNS and IP Addresses
Load balancers provide DNS names instead of individual target IP addresses for several reasons:

* **Simplified Client Configuration**: Clients only need to know the load balancer's DNS name, not individual target IPs.
* **Scalability**: The load balancer can easily distribute traffic across new targets without requiring client-side configuration changes.
* **Fault Tolerance**: If a target becomes unhealthy, the load balancer automatically routes traffic to healthy targets.

### Obtaining Client IP Address
While the request you receive might contain the load balancer's IP address, there are ways to retrieve the client's IP address behind the load balancer:

* **ELB Headers**: AWS load balancers add headers to requests that contain the originating client's IP address (e.g., X-Forwarded-For).
* **Client-Side Detection**: You can implement logic within your application code to parse the headers and identify the client's IP address.

> **Note**: Choose the appropriate load balancer type based on your application's requirements (performance, routing complexity) and leverage health checks to ensure high availability.

### Summary
![](https://i.imgur.com/KcJY9F5.png)
