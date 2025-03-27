# AWS Instance Metadata and Elastic IPs

## Instance Metadata
- Provides information about EC2 instance and are accessible from within the instance. 
- It includes:
  - **Instance ID**
  - **Instance Type**
  - **Public IP Address**
  - **Private IP Address**
  - **Availability Zone**
  - **Security Groups**
  - **User Data**
  - **AMI ID**

### Accessing Instance Metadata
- **Linux**: Using `curl` or `wget` command to fetch metadata from a specific URL (e.g., `curl http://169.254.169.254/latest/meta-data`).
- **Windows**: Using the `PowerShell` command `Get-MetadataService -Path <metadata-key>`.
- **Others**: Using AWS SDKs.


### IP Address and Stopping/Starting Instances
- **Public IP**: By default, the public IP address can change when instance is stopped and restarted in a public subnet.
- **Retaining IP (Elastic IP)**: To maintain a static IP, allocate an Elastic IP or Static IP address and associate it with instance. 

### Elastic IP
- Elastic IPs remain independent of the instance state. 
- AWS provides a certain number of EIPs for free, and additional ones incur charges based on usage.
- Can allocate a maximum of 5 Elastic IPs per AWS account by default.
- Charged a fixed hourly rate for each Elastic IP address allocated, regardless of whether it's associated with a running instance.
- There are no charges for data transfer associated with Elastic IPs.