# Scaling, Auto Scaling Group, and Launch Templates in AWS

## Scaling
- Adjusting the resources allocated to application up or down to meet changing demands
- This helps to optimize costs by using only the resources needed
- Pay only for the resources application uses, reducing idle resource costs
- Ensures enough resources to handle traffic spikes, preventing slowdowns
- **Use Cases**:
  - In web applications to automatically scale up during peak traffic hours and down during off-peak times
  - In batch processing jobs to allocate more resources when processing large datasets and fewer resources during idle period
  - For development and Testing**: Use smaller instances for development and testing environments, scaling up for production
- **Limitations**:
  - Scaling can take time, impacting application responsiveness during sudden spikes
  - Requires monitoring application performance and resource utilization for effective scaling decisions
  - Setting up and managing auto-scaling policies might require additional effort

## Types of Scaling
![image](https://d1tcczg8b21j1t.cloudfront.net/strapi-assets/23_Horizontal_vs_vertical_scaling_2_bf6d292ef7.png)

### 1. Vertical Scaling (Scale Up/Down)
- Changing the capacity of a single resource (e.g., switching to a larger EC2 instance type)
- **Benefits**: Simpler to implement, as it uses existing configurations of instance
- **Use Case**: Suitable for applications with limited scalability requirements or where horizontal scaling is not feasible
- **Limitations**: Limited scaling range, may not be cost-effective for significant changes

### 2. Horizontal Scaling (In/Out)
- Adding or removing resources (e.g., launching or terminating EC2 instances)
- **Benefits**: More flexible scaling for large fluctuations in demand
- **Use Case**: Ideal for applications with unpredictable traffic patterns or high scalability requirements
- **Limitations**: Requires managing multiple resources, potential configuration overhead


## AWS Launch Templates
- A blueprint that defines the configuration for launching EC2 instances
- Helps to ensure consistency and repeatability when launching multiple instances for scaling


## Auto Scaling Groups (ASG)
- A collection of EC2 instances that AWS automatically scales based on predefined policies
- Simplifies horizontal scaling by managing the provisioning, launching, and termination of instances. So, it reduces manual intervention in scaling decisions
- Ensures enough healthy instances to handle traffic
- Setting up scaling policies and monitoring metrics requires careful planning

> **Note**: 
> 1. Auto Scaling in AWS is primarily designed for horizontal scaling, but vertical scaling can be achieved with some manual interventions or additional services
> 2. Unexpected scaling events can lead to higher costs if not properly managed


## Automatic Scaling under Auto Scaling Groups
- It allows defining policies that trigger scaling actions based on various metrics like CPU utilization, network traffic, or custom application metrics

### Types of Automatic Scaling
- **Target Tracking Scaling**: Adjusts the number of instances to maintain a specified target metric, such as CPU utilization or request count per instance
- **Simple Scaling**: Adds or removes instances based on a predefined schedule or specific metrics thresholds

> **Note**: Target Tracking Scaling is suitable for maintaining a specific level of performance or resource utilization, while Simple Scaling is useful for scheduled events or predictable workload patterns


### Automatic Scaling Policies
#### 1. Dynamic Scaling Policies
- These policies react to real-time changes in cloudwatch metrics like CPU utilization, network traffic, or custom application health metrics
- When a metric exceeds (scale out) or falls below (scale in) a predefined threshold for a sustained period, the policy triggers the addition or removal of instances from the Auto Scaling group

#### 2. Predictive Scaling Policies
- Uses machine learning to forecast future demand based on historical data and trends
- It allows the Auto Scaling group to proactively add or remove instances before traffic spikes or dips occur, ensuring smooth performance and resource optimization

#### 3. Scheduled Scaling Actions
- Allows defining scaling actions based on a pre-defined schedule
- For example, one might choose to scale up the application instances before daily peak traffic hours and scale them back down during off-peak times. This is helpful for predictable traffic patterns


### Cool Down Time in Auto Scaling
- It is the waiting period configured in the scaling policy
- Prevents instances from being immediately terminated after the scaling metric falls below the threshold
- It helps in avoiding unnecessary scaling in and out due to short-lived fluctuations


### Base Period in Auto Scaling
- It is the minimum time that the scaling metric must stay above or below the threshold before a scaling action is triggered
- This helps prevent scaling actions due to brief spikes or dips in the metric, ensuring smoother scaling behavior