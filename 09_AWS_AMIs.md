# AWS - AMIs

## AMI (Amazon Machine Image)
- A template that captures the configuration of a running EC2 instance including OS, applications, configurations, and data (optional) that define how the instance will behave.
- It helps to launch new instances with identical configurations quickly and easily
- AMI contains:
  - Operating System (e.g. Linux, Windows)
  - Application Server (e.g. Apache, Nginx)
  - Pre-installed software and configurations
- **Types of AMIs**:
  1. Public (Share AMIs publicly on the AWS Marketplace for others to use)
  2. Private (Share AMIs within organization or account for controlled access)
  3. Paid AMIs or Market Place AMIs

### How are AMIs Created?
- AWS takes a snapshot of the entire root volume of the instance, essentially freezing its state
- This snapshot serves as the basis for the AMI

### Creating an Instance from an AMI
- When launching a new EC2 instance, there is an option to choose an existing AMI instead of manually configuring a new instance
- This launches a new instance with the configuration defined in the chosen AMI

### Behind the Scenes
- When an instance is launched from an AMI, AWS performs the following actions:
  1. **Copies the AMI**: A copy of the AMI's root volume snapshot is created
  2. **Creates a New EBS Volume**: A new EBS volume is created from the copied snapshot
  3. **Launches the Instance**: The EC2 instance is launched using the newly created EBS volume as its root volume

> **Note**: The AMI itself doesn't contain the actual instance data (by default); it captures the configuration that instructs how to set up a new instance
