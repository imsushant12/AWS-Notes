# AWS - Infrastructure: Region, Zone, AZ, PoP, Edge Location, and Local Zone

## Regions
- A separate geographic location with isolated physical data centres
- Each region typically consists of 3 Availability Zones and physically separated data centres
- There are 33 launched AWS regions worldwide (March-2024)
- **Purpose**: 
  - Deploy resources closer to target audience or specific geographic locations
  - Provides low-latency access and compliance with data residency requirements
  - Provides redundance, disaster recovery, minimizes outages area
- **Connection**: Connected to other regions via high-bandwidth backbones (network) for data transfer between regions

## Availability Zones (AZs)
- Region is further divided into multiple Availability Zones (AZs)
- AZ are geographically separate data centres (hardware, software, and networking infrastructure) within a single area, isolated from each other to prevent failures from affecting other zones
- If one AZ fails, resources in other AZs remain operational
- AZ contains hardware, software, and networking infrastructure to run different AWS services
- Each AZ has its infrastructure and resources, including power, cooling, and networking
- **Purpose**: 
  - Provide fault tolerance and high availability
  - Allows users to deploy applications across multiple isolated locations
  - Provide redundancy within a region
- **Connection**: Connected within a region through high-throughput, low-latency connections for data transfer between AZs

## Points of Presence (PoPs)
- Geographically distributed infrastructure points around the world that bring AWS services closer to end-users
- PoPs do not contain all AWS services but it contains service-specific things like CloudFront, Route 53, and Global Accelerator
- Contain networking equipment and caching servers to optimize content delivery and reduce latency
- Currently over 600 PoPs spread across the globe
- Supports content delivery through AWS CloudFront CDN 
- **Purpose**: 
  - Improves performance by caching content closer to end-users
- **Connection**: PoPs connect to regional edge locations or directly to regional backbones for data transfer

## Edge Locations
- Specialized PoPs located in significant cities or metro areas
- They are the endpoints for AWS's content delivery network (CDN) service, Amazon CloudFront
- Offers lower latency than traditional PoPs, making them ideal for applications requiring real-time or near-real-time interactions
- Edge locations are a subset of PoPs, currently consisting of over 400+ locations
- **Purpose**: 
  - Host specific services like CloudFront caches and AWS Lambda@Edge functions to reduce latency further
  - Improve performance for latency-sensitive applications
- **Connection**: They connect directly to the nearest regional backbones or other edge locations

## Local Zones
- Specialized deployments of AWS infrastructure housed within major metropolitan areas
- Bring selected AWS services closer to end-users, like EC2 and EBS, and offer ultra-low latency for specific applications
- Local Zones are smaller in scale compared to full regions
- Designed to support workloads that require single-digit millisecond latency to end-users
- **Purpose**:
  - To serve the workloads requiring extremely low latency, such as high-frequency trading, virtual reality, and real-time gaming
- **Connection**: They connect to the parent region through a dedicated, high-bandwidth private network

## Key Differences and Connectivity Summary
### Differences
- **Regions**: Largest geographical unit, containing multiple AZs and offering a complete range of AWS services
- **AZs**: Subdivisions within a region, providing redundancy and fault tolerance within an area
- **PoPs**: Distributed infrastructure points offering specific services closer to users, reducing latency
- **Edge Locations**: A subset of PoPs located in strategic locations, offering even lower latency for specific services
- **Local Zones**: Specialized deployments within metro areas, providing ultra-low latency for select services

### Connectivity
- **Regions**: Connected via high-bandwidth backbones
- **AZs**: Connected within a region through high-throughput, low-latency connections
- **PoPs**: Connected to regional edge locations or directly to regional backbone
- **Edge Location**: Connected directly to the nearest regional backbones or other edge locations
- **Local Zones**: Connected to the parent region through a dedicated, high-bandwidth private network