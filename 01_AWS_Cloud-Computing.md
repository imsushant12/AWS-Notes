# Cloud Computing and AWS

## AWS (Amazon Web Service)
- A cloud computing platform that provides services over the Internet on a pay-as-you-go basis like:
  - computing power, 
  - storage options, 
  - networking, 
  - databases,
  - machine learning and artificial intelligence, 
  - analytics, 
  - security, and more, all available .
- It mainly charges for three things:
  1. Compute
  2. Storage
  3. Data Transfer (download/ upload from outside)
- It also provides a limited set of AWS services for free for a specific period, usually 12 months (**Amazon Free-Tier Account**).
- Main Features of AWS:
  - **On-demand resources**: We can scale resources up or down as needed, eliminating the need for over-provisioning.
  - **Pay-as-you-go model**: We only need to pay for the resources we use which reduces the upfront costs.
  - **Managed infrastructure**: AWS manages the underlying infrastructure so we only need to focus on our applications.
  - **Global reach**: We can access our resources from anywhere in the world with AWS's extensive global network.

### How is AWS different from traditional services?
Traditional services typically involve setting up physical hardware infrastructure and managing it on-premises. On the other hand, AWS provides virtualized resources over the internet, enabling users to provision and access resources instantly without needing physical hardware. 

### Benefits of using AWS
- **Scalability**
- **Cost-effectiveness** (Pay-as-you-go model)
- **Flexibility**
- **Reliability**
- **Security**
- **Innovation**

### Problems solved by AWS
- Costly upfront investments in hardware.
- Limited scalability and flexibility of on-premises infrastructure.
- Time-consuming infrastructure management tasks.
- Lack of geographic reach and redundancy.
- Difficulty in implementing robust security measures.

## Various cloud computing models
![IaaS Vs PaaS vs Saas](https://www.redhat.com/rhdc/managed-files/iaas-paas-saas-diagram5.1-1638x1046.png)

### 1. Infrastructure as a Service (IaaS)
It provides virtualized computing resources over the internet. Rent virtual servers, storage, networking, and other basic infrastructure components. 
- **Example**: Amazon EC2. 

### 2. Platform as a Service (PaaS)
It offers a platform allowing customers to develop, run, and manage applications without dealing with infrastructure. PaaS automates setting up the infrastructure needed to run your applications, saving you time and effort. It provides essential services like databases, messaging, and caching, eliminating the need for separate management. It also gives you insights into application performance, resource usage, and user behavior, allowing for optimization and troubleshooting.
- **Example**: AWS Elastic Beanstalk. PaaS provide these benefits:

### 3. Software as a Service (SaaS)
It delivers software applications over the internet on a subscription basis. SaaS applications have built-in scalability and high availability, so it is consistent with performance and offers minimized downtime. SaaS applications can be integrated smoothly with other AWS services, enabling businesses to build interconnected solutions according to their needs.
- **Example**: Amazon WorkMail. 

### Deployment Models of Cloud
- **Public Cloud**: Services are offered over the public internet and shared among multiple users.
  - **Example**: Amazon EC2.
  - **Pros**: Cost-effective, scalable, and easy to use. 
  - **Cons**: Security concerns and lack of control over infrastructure. 
- **Private Cloud**: Infrastructure is provisioned for exclusive use by a single organization. 
  - **Example**: AWS Outposts.
  - **Pros**: Enhanced security control over resources. 
  - **Cons**: Higher costs, limited scalability. 
- **Hybrid Cloud**: Combination of public and private cloud resources. 
  - **Example**: AWS Direct Connect.
  - **Pros**: Flexibility, scalability, data residency. 
  - **Cons**: Complexity and integration challenges.

We have 2 more types of cloud: 
- **Multi-cloud**: Organizations use multiple cloud computing services from different providers in a multi-cloud deployment. 
  - **Pros**: Flexibility, avoiding vendor lock-in, redundancy, leveraging specialized services from different providers.
  - **Cons**: Complexity in management, interoperability challenges, and the potential for increased costs.
- **Community Cloud**: In a community cloud deployment, infrastructure is shared among several organizations with similar requirements.
  - **Pros**: Shared costs among community members, tailored services to meet specific industry needs, shared security measures.
  - **Cons**: Limited scalability, potential conflicts among community members, dependency on community governance.