# AWS - CLI (Command Line Interface)

- A Python utility (program) and which can be used to pass commands to the AWS directly from terminal
- An alternative to the web-based AWS Management Console, and offers benefits for automation, scripting, and efficient management of resources
- Useful for automating repetitive tasks, so scripts can be used to automate deployments, configuration changes, and other resource management operations
- Performing actions through the CLI can often be faster than navigating the web console, especially for bulk operations or complex workflows
- Can also integrate the AWS CLI into existing scripts and tools to automate complex workflows and deployments
- **Features**:
  - Manage multiple AWS accounts with different configurations
  - Uses access keys or IAM roles for authentication, providing secure access to AWS resources
  - Based on AWS SDKs, providing consistency and compatibility with programming languages and development frameworks
  - Support various output formats such as JSON, text, or table, allowing flexibility in displaying results
  - Provides detailed error messages and debugging options for troubleshooting and problem resolution
- **Benefits over GUI**:
  - Faster command execution
  - More scalable and suitable for managing large-scale deployments or complex architectures, where manual operations via GUI become impractical
  - CLI commands can be version-controlled and integrated into CI/CD pipelines

## Working with AWS CLI
### Installation
Can be installed using OS specific package managers, Python pip, or as standalone binaries

### Configuration
Post installation, ``aws configure`` command is used to configure AWS CLI with access key ID, secret access key, default region, and output format

### Command Structure
``aws <service> <operation> <parameters>``. For example, ``aws ec2 describe-instances`` lists all EC2 instances in the default region

## Important AWS CLI Commands
- **EC2**:
  - Get information about running EC2 instances: `ec2 describe-instances`
  - Launch a new EC2 instance: `ec2 run-instances`
  - Terminate a running EC2 instance: `ec2 terminate-instances`
- **S3**:
  - List objects in an S3 bucket: `s3 ls`
  - Upload or download files to/from an S3 bucket: `s3 cp`
  - Delete objects from an S3 bucket: `s3 rm`
- **IAM**:
  - List all IAM users in account: `iam list-users`
  - Create a new IAM user: `iam create-user`
  - Attach a policy to an IAM user: `iam attach-user-policy`
- **CloudWatch**:
  - Get logs from a CloudWatch log group: `aws logs get-log-events`
  - Get information about CloudWatch alarms: `aws cloudwatch describe-alarms`