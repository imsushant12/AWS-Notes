# AWS - Load Balancers

## Load Balancer
- A service that automatically distributes incoming traffic across multiple targets, such as EC2 instances, containers, or IP addresses
- Acts as a single point of contact for clients and ensures high availability and scalability for applications
- Distributes traffic across healthy targets, preventing a single point of failure
- Easily add or remove resources to handle traffic fluctuations
- Reduces latency by distributing traffic efficiently
- **Use Cases**:
  - In Web Applications to distribute traffic across multiple web servers for high availability and performance
  - Route traffic to individual microservices based on specific rules
  - Can direct users to the nearest or fastest edge server to minimize latency
- **Limitations**:
  - Requires additional configuration and management compared to directly accessing instances
  - Additional charges are applied for the load balancing service
  - Cannot directly control traffic routing to specific targets within the load balancer

## Types of Load Balancers in AWS
### 1. Classic Load Balancer (CLB)
- Provides basic load balancing across multiple EC2 instances
- Operates at both the application (HTTP/HTTPS) and transport (TCP) layers
- It is **now deprecated by AWS**
- **Benefits**: Easy setup, suitable for simple applications
- **Limitations**: Limited features compared to Application LB and Network LB
- **Use Cases**: 
    - Legacy applications that don’t require advanced load balancing features 
    - Basic HTTP and HTTPS load balancing

### 2. Application Load Balancer (ALB)
- Routes traffic at the application layer (HTTP/HTTPS) based on URL path, host headers, HTTP methods, and query parameters
- Supports features like WebSockets, HTTP/2, and container-based architectures
- Ideal for modern web applications
- **Benefits**: 
    - Advanced request routing (content-based routing)
    - Support for containerized applications, and HTTP/2
    - Provides detailed request-level metrics in AWS CloudWatch
    - Has **HTTP/2** and **gRPC** support which means improves performance for modern applications
    - Supports **SSL/TLS termination** so it offloads encryption/decryption from backend servers
    - Has **WebSockets support** to handle real-time communication
    - Can check the health of the application itself
- **Limitations**: Higher cost compared to Classic LB, and requires familiarity with advanced features
- **Use Cases**: Microservices architectures, containerized applications, and routing based on request content
- **Listeners**: Configured for HTTP/HTTPS on ports 80/443 (or custom ports)

### 3. Network Load Balancer (NLB)
- Routes traffic at the network layer (TCP/UDP/TLS) based on IP addresses and ports
- Offers high performance and scalability for low-latency applications
- **Benefits**: 
    - Handles millions of requests per second with ultra-low latency
    - Supports static IP addresses for predictable client access
    - Provides TCP, UDP, and TLS termination
- **Limitations**: Limited routing flexibility (IP address and port only) and it has slightly higher cost than CLB
- **Use Cases**: 
    - High-performance applications (gaming servers, real-time data streaming)
    - TCP/UDP-based applications (VoIP, messaging services)
    - Extreme scalability requirements (financial transactions, stock trading)
- **Listeners**: Configured for TCP/UDP/TLS on specific ports
- **Target Groups**: Targets are IP addresses or instances. Health checks are TCP/UDP based

### Gateway Load Balancer (GLB)
- Operates at Layer 3 (Network Layer) and Layer 4 (Transport Layer) and is designed for security and network services
- Primarily used to distribute traffic across third-party virtual appliances (e.g., firewalls, intrusion detection systems)
- **Benefits**: Provides transparent traffic inspection and security enforcement. It works across multiple VPCs and on-premises environments
- **Limitations**: More complex to configure compared to ALB/NLB and it has higher cost due to its specialized security use cases
- **Use Cases**: Deploying and scaling firewalls, intrusion detection/prevention systems, deep packet inspection, and other network appliances
- **Listeners**: Configured for GENEVE protocol
- **Target Groups**: Targets are virtual appliances

> **Note**:
>- All AWS load balancers are designed to scale automatically based on traffic demands
>- Load balancers work with security groups to control inbound and outbound traffic
>- ALB and NLB can maintain session stickiness for stateful applications
>- Load balancers use the X-Forwarded-For header to pass client IP addresses to backend instances
>- ALB can route requests to lambda functions, which is important for serverless architecture

## Selection of Load Balancer
- **Use ALB when**: Need advanced request routing, content-based routing, or working with microservices and APIs
- **Use NLB when**: Need ultra-low latency, high performance, and handling TCP/UDP traffic at scale
- **Use GWLB when**: Require security appliances for traffic inspection in multi-VPC or hybrid environments
- **Use CLB when**: Maintaining legacy applications (but consider migrating to ALB/NLB)

## Summary of Load Balancers
| Type | Benefits | Limitations | Use Cases | Key Points |
|------|----------|-------------|-----------|------------|
| ALB  | Flexible routing, content-based routing, container support, SSL/TLS termination, HTTP/2 & gRPC, advanced health checks | Slightly higher latency than NLB, higher cost than CLB | Modern web applications, microservices, APIs | Content-based routing, container integration, application-level health checks, SSL offloading |
| NLB  | High performance, low latency, static IPs, handles extreme traffic | Limited routing options, higher cost | High-throughput backends, gaming servers, TCP/UDP applications | Static IPs, low-latency, TCP/UDP focus, used when performance is critical |
| GLB  | Centralized appliance deployment, scalability, GENEVE protocol, third-party integration | Complex configuration | Firewalls, IDS/IPS, network appliances | Virtual appliance integration, GENEVE protocol, network traffic inspection |
| CLB  | Simple setup (legacy) | Deprecated, limited features | Legacy applications (avoid) | Deprecated, understand why ALB/NLB are preferred |

## Load Balancing Algorithm
- Uses round-robin algorithm to distribute traffic across healthy targets. So, requests are sent to each target in a sequential order
- Other health-based factors can also influence routing decisions

## Health Checks in Load Balancers
- Automated mechanisms used by load balancers to monitor the health of target resources
- These checks ensure only healthy targets receive incoming traffic
- Health check parameters:
  - **Interval**: Frequency of health checks
  - **Timeout**: Maximum time a target can take to respond before being considered unhealthy
  - **Port**: Port on which the health check is performed
  - **Path**: Specific path or URL used for the health check
  - **Expected Code**: HTTP status code expected from a healthy target

## Cross-Zone Load Balancing
- Distributes traffic across healthy targets in different Availability Zones within the same region
- Enhances fault tolerance and ensures application remains available even if an entire AZ fails
- Load Balancers with Default Cross-Zone Support:
  - Application Load Balancer (ALB)
  - Network Load Balancer (NLB)

## Load Balancer DNS and IP Addresses
- Load balancers provide DNS names instead of individual target IP addresses because:
  - Clients only need to know the load balancer's DNS name, not individual target IPs
  - Load balancer can easily distribute traffic across new targets without requiring client-side configuration changes
  - If a target becomes unhealthy, the load balancer automatically routes traffic to healthy targets

## Obtaining Client IP Address
- The received request contains the load balancer's IP address but there are ways to retrieve the client's IP address behind the load balancer:
    - **ELB Headers**: AWS load balancers add headers to requests that contain the originating client's IP address (e.g., X-Forwarded-For)
    - **Client-Side Detection**: Can implement logic within application code to parse the headers and identify the client's IP address