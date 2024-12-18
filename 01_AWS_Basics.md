# AWS Basics
AWS stands for Amazon Web Services. It is a comprehensive and evolving cloud computing platform provided by `Amazon.com`. It offers a wide range of services, including computing power, storage options, networking, databases, machine learning, artificial intelligence, analytics, security, and more, all available over the Internet on a pay-as-you-go basis.
It mainly charges for three things:
1. Compute
2. Storage
3. Data Transfer (download/ upload from outside)

### AWS Account
An account that grants you access to various cloud computing services offered by Amazon Web Services (AWS). It allows you to create, manage, and deploy resources like computing, storage, and databases.

#### Free Tier Account
A particular type of AWS account that provides a limited set of AWS services for free for a specific period, usually 12 months. It allows you to experiment and learn about AWS without incurring any charges.

#### Benefits of Free Tier Account
* **Free access to various services:** Provides access to popular services like EC2 instances, S3 storage, and Lambda functions for a limited usage.
* **Hands-on learning:** Allows you to experiment and learn how to use AWS services without financial commitment.
* **Develop cloud skills:** Helps you build your cloud computing skills and knowledge base.

### How is AWS different from traditional services?
Traditional services typically involve setting up physical hardware infrastructure and managing it on-premises. On the other hand, AWS provides virtualised resources over the internet, enabling users to provision and access resources instantly without needing physical hardware. 

AWS offers:
- **On-demand resources**: Scale resources up or down as needed, eliminating the need for over-provisioning.
- **Pay-as-you-go model**: Only pay for the resources you use, reducing upfront costs.
- **Managed infrastructure**: AWS manages the underlying infrastructure, freeing you to focus on your applications.
- **Global reach**: Access your resources from anywhere in the world with AWS's extensive global network.

### What are the benefits of using AWS?
- **Scalability**: Easily scale resources up or down based on demand.
- **Cost-effectiveness**: Pay only for the resources you use on a pay-as-you-go basis.
- **Flexibility**: Choose from various services to meet various business needs.
- **Reliability**: AWS offers high availability and reliability through its global infrastructure.
- **Security**: AWS provides robust security measures and compliance certifications.
- **Innovation**: Constantly evolving platform with new features and services.

### What does AWS solve the problems?
- Costly upfront investments in hardware.
- Limited scalability and flexibility of on-premises infrastructure.
- Time-consuming infrastructure management tasks.
- Lack of geographic reach and redundancy.
- Difficulty in implementing robust security measures.

### Various cloud computing models
#### 1. Infrastructure as a Service (IaaS)
It provides virtualised computing resources over the internet. Rent virtual servers, storage, networking, and other basic infrastructure components. **Example**: Amazon EC2. IaaS on AWS offers businesses three key benefits:
- **Scalability**: Easily adjust resources up or down to meet changing demands, ensuring flexibility and optimising costs.
- **Control and Customization**: Have granular control over your infrastructure, allowing you to tailor virtual machines, networks, and storage to your specific needs.
- **Cost-Efficiency**: Pay only for the resources you use, eliminating upfront hardware costs and reducing overall IT expenses.

#### 2. Platform as a Service (PaaS)
It offers a platform allowing customers to develop, run, and manage applications without dealing with infrastructure. **Example**: AWS Elastic Beanstalk. PaaS provide these benefits:
- **Streamlined deployment**: PaaS automates setting up the infrastructure needed to run your applications, saving you time and effort.
- **Effortless scaling**: PaaS lets your applications automatically adjust to changing demands, ensuring smooth operation during peak usage.
- **Diverse development tools**: PaaS offers various tools and frameworks compatible with your preferred programming languages and environments, making development familiar and efficient.
- **Integrated services**: PaaS provides essential services like databases, messaging, and caching, eliminating the need for separate management.
- **Simplified collaboration**: PaaS facilitates teamwork by offering features that allow multiple developers to work on projects simultaneously.
- **Enhanced monitoring**: PaaS gives you insights into application performance, resource usage, and user behaviour, allowing for optimisation and troubleshooting.

#### 3. Software as a Service (SaaS)
It delivers software applications over the internet on a subscription basis. **Example**: Amazon WorkMail. SaaS provide these benefits:
- **Quick and easy access**: AWS Marketplace provides a collection of ready-to-use SaaS applications, eliminating complex setup and installation processes.
- **Reliable performance**: With built-in scalability and high availability, these applications offer consistent performance and minimise downtime.
- **Seamless integration**: They integrate smoothly with other AWS services, enabling businesses to build interconnected solutions tailored to their needs.

### Deployment models of cloud
- **Public Cloud**: Services are offered over the public internet and shared among multiple users. Example: Amazon EC2.
    - **Pros**: Cost-effective, scalable, and easy to use. - **Cons**: Security concerns and lack of control over infrastructure. 
- **Private Cloud**: Infrastructure is provisioned for exclusive use by a single organisation. An example is AWS Outposts.
    - **Pros**: Enhanced security control over resources. 
    - **Cons**: Higher costs, limited scalability. 
- **Hybrid Cloud**: Combination of public and private cloud resources. Example: AWS Direct Connect.
    - **Pros**: Flexibility, scalability, data residency. 
    - **Cons**: Complexity and integration challenges. 
- **Multi-cloud**: Organizations use multiple cloud computing services from different providers in a multi-cloud deployment. 
    - **Pros**: Flexibility, avoiding vendor lock-in, redundancy, leveraging specialised services from different providers.
    - **Cons**: Complexity in management, interoperability challenges, and the potential for increased costs.
- **Community Cloud**: In a community cloud deployment, infrastructure is shared among several organisations with similar requirements.
    - **Pros**: Shared costs among community members, tailored services to meet specific industry needs, shared security measures.
    - **Cons**: Limited scalability, potential conflicts among community members, dependency on community governance.

### How does AWS charge?
- **Pay-as-you-go**: Customers are charged based on actual usage of resources, such as compute instances, storage, data transfer, etc.
- **Reserved Instances**: Customers can commit to a certain level of usage for a period (1 or 3 years) in exchange for discounted pricing.
- **Spot Instances**: Customers bid for unused EC2 capacity, allowing them to use unused resources at reduced rates.
- **On-Demand Instances**: Customers can provision instances on-demand without long-term commitments, paying for the resources by the hour or second.

## Summary
[Summary](https://www.notion.so/AWS-Basics-c5585a1c959c4affb7618a26a6110651?pvs=4)