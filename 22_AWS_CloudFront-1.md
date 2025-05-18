# AWS - CloudFront

- CloudFront is a content delivery network (CDN) service offered by AWS
- It distributes static content (like images, videos, JavaScript, CSS) from a global network of edge locations, bringing content closer to users for faster loading times and improved user experience
- **Benefits**:
  - Faster content delivery for users worldwide due to edge caching
  - CloudFront automatically scales to handle traffic spikes
  - CloudFront helps mitigate DDoS attacks by distributing traffic across multiple edge locations
- **Limitations**:
  - Incurs additional charges for data transfer, storage, and requests
  - While configuring caching behavior is possible but it is not as granular as some self-managed CDNs
  - Primarily designed for static content; dynamic content may require additional configurations
- **Use Cases**:
  - Deliver website content for faster loading times
  - Distribute video and audio content with lower latency and improved playback experience
  - Can be used to cache API responses for faster performance, though caching behavior needs careful consideration for dynamic APIs

## How CloudFront Works?
1. **Origin Creation**: Specify the origin of content, such as an S3 bucket, web server, or another CloudFront distribution
2. **Edge Locations**: CloudFront caches content at geographically distributed edge locations. When a user requests content, CloudFront delivers it from the nearest edge location, reducing latency
3. **Request Routing**: CloudFront routes user requests to the appropriate origin server based on factors like location and availability

## Setting Up CloudFront
1. **Create a Distribution**: In the AWS Management Console, specify origin (e.g., S3 bucket) and configure settings like behavior policies and caching behavior
2. **Behavior Policies**: Define how CloudFront handles requests based on URL patterns (e.g., redirecting HTTP to HTTPS)
3. **Caching Behavior**: Configure how CloudFront caches content, including TTL (Time To Live) settings and invalidation options
4. **Distribution Deployment**: CloudFront automatically provisions resources and deploys distribution globally

## TTL Settings
- TTL (Time To Live) defines how long CloudFront caches content at the edge locations before fetching a fresh copy from the origin
- A shorter TTL ensures users receive the latest content, while a longer TTL improves performance but might lead to serving slightly outdated content

## Invalidation
- Invalidation instructs CloudFront to remove outdated content from its edge caches
- This is necessary when content is updated on the origin server and want users to access the latest version

## Security with CloudFront, Load Balancers, and Security Groups
- **CloudFront**: Offers security features like signed URLs and origin access identities to control access to origin content
- **Load Balancers**: Distribute traffic across multiple EC2 instances or containerized applications for high availability and scalability
- **Security Groups**: Define firewall rules to control inbound and outbound traffic at the instance level or VPC subnet level

### How They Work Together?
- CloudFront sits in front of origin server (e.g., behind a load balancer) and delivers cached content
- Security groups control traffic flow to origin server or load balancer, ensuring only authorized requests reach application
- Load balancers distribute traffic across instances for scalability and fault tolerance