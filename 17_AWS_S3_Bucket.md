# S3 buckets

## Amazon S3 
An S3 bucket is a storage unit within Amazon Simple Storage Service (S3). It's like a virtual filing cabinet in the cloud, designed for storing and retrieving any amount of data, from a few kilobytes to petabytes. You can use S3 buckets for various purposes, including static website hosting, application data storage, backups, and archives.

Main characteristics of Amazon S3:
- Scalable
- Highly available
- Secure
- Cost effective
- Performance

### Important Points
- It stores data as objects and each object within a bucket is stored as a key-value pair
  - Key is the object's name (which can contain slashes/, mimicking directory structure)
  - Value is the content of the object
- It is region specific
- The name of the bucket should be globally unique

### Snow Family
- AWS Snowcone
- AWS Snowball
- AWS Snowmobile

### S3 Storage Gateway

### Benefits and Advantages of S3 Buckets
* **Scalability**: Easily scale storage up or down based on your needs, without worrying about infrastructure limitations.
* **Durability**: S3 stores your data redundantly across multiple facilities, ensuring high availability and data protection against hardware failures.
* **Security**: S3 offers various security features like access control lists (ACLs) and encryption to control who can access your data.
* **Cost-Effectiveness**: Pay only for the storage you use, with various storage classes catering to different access needs (frequent vs. infrequent access).
* **Ease of Use**: Simple API and web console for managing buckets and objects (data files) within them.

### Disadvantages and Limitations of S3 Buckets
* **Not optimized for frequent data updates**: While possible, S3 isn't ideal for applications requiring frequent data updates due to its object-based storage structure.
* **Costs associated with data retrieval**:  There are egress charges for transferring data out of S3 buckets.

### Use Cases for S3 Buckets
* **Static website hosting**: Store website content like HTML, CSS, and JavaScript files in an S3 bucket and configure it for website hosting.
* **Application data storage**: Store data used by your applications, such as user uploads, logs, and images.
* **Backups and archiving**: Archive essential data for disaster recovery or long-term retention purposes.
* **Data lakes**: Store large datasets for big data analytics.

## S3 Bucket Naming Conventions
* Bucket names must be unique across all AWS accounts.
* Must be 3 to 63 characters long.
* Can only contain lowercase letters, numbers, periods (.), and hyphens (``-``).
* Start with a letter or number. Cannot start with a hyphen.

## ARN (Amazon Resource Name) in S3
An ARN is a unique identifier for AWS resources, including S3 buckets. It follows a standard format specifying the AWS partition, service, region, account ID, and the bucket name. For example:

```
arn:aws:s3:<region>:<account-id>:<bucket-name>
```

## Entity Tag (`ETag`) in S3
An ETag is a unique identifier assigned to an object (file) in an S3 bucket. It reflects the object's content and acts as a validation check. ETags ensure data integrity; if you upload the same object twice, you'll receive the same ETag, confirming it's a duplicate.

## Making an S3 Object Public
By default, S3 objects are private. To make an object publicly accessible via a link:

1. Go to the S3 Management Console.
2. Select your bucket and the object you want to make public.
3. Click on ``Permissions``.
4. Set the ``Public Access`` option to ``Read``.
5. S3 will generate a public URL that you can use to share the object.

## S3 Folders vs. Key Prefixes
S3 doesn't support folders in the traditional sense. Instead, it uses key prefixes to organize objects hierarchically. When you create a key with a forward slash ``/``, it creates a virtual hierarchy within the bucket. For example, a key named ``documents/my-file.txt`` creates a virtual path ``documents/`` within the bucket.

## Minimum and Maximum Object Size
* Minimum object size: 0 bytes (empty file)
* Maximum object size: 5 TB

## S3 Versioning
S3 versioning allows you to maintain a history of every object uploaded to a bucket, including all changes made over time. This offers several advantages:

* **Rollback to Previous Versions**: In case of accidental modifications or deletions, you can easily restore an object to a previous version. This is crucial for ensuring data integrity and preventing accidental data loss.
* **Compliance**: Versioning can be helpful for meeting regulatory requirements that mandate data retention and auditability. For example, some industries need to maintain a history of financial transactions or customer records.
* **Improved Security**: Versioning provides an additional layer of security by offering a way to recover from ransomware attacks or unauthorized modifications.

**However, there are also some things to consider with S3 versioning**:

* **Increased Storage Costs**: Every version of an object is stored, leading to higher storage costs compared to non-versioned buckets.
* **Complexity**: Managing and keeping track of numerous object versions can add complexity, especially for frequently updated objects.

### Use Cases for S3 Versioning
* **Mission-critical data**: Versioning is essential for storing sensitive or critical data where recovering past versions might be necessary.
* **Regulatory compliance**: If your industry mandates data retention for audit purposes, versioning ensures you can meet those requirements.
* **Content management systems (CMS)**: Versioning allows you to revert to previous versions of website content or documents in case of errors.


## How to write permissions in a S3 bucket?
Writing permissions for an S3 bucket involves configuring policies and access control lists (ACLs). Here’s how you can do it:

### 1. Bucket Policies
Bucket policies are JSON-based access policy language statements that define who has access to the bucket and what actions they can perform.

#### Example: Bucket Policy to Allow Public Read Access

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::your-bucket-name/*"
    }
  ]
}
```

- **Effect**: `Allow` or `Deny`.
- **Principal**: Specifies the user, account, service, or other entity that is allowed or denied access to a resource.
- **Action**: List of actions that are allowed or denied (e.g., `s3:GetObject`).
- **Resource**: Specifies the bucket or object that the policy applies to.

### 2. Access Control Lists (ACLs)
ACLs are used to grant read and write permissions to specific AWS accounts and to predefined groups of users.

#### Example: Setting an ACL to Grant Full Control to Another AWS Account

```json
{
  "Grants": [
    {
      "Grantee": {
        "Type": "CanonicalUser",
        "ID": "another-aws-account-id"
      },
      "Permission": "FULL_CONTROL"
    }
  ],
  "Owner": {
    "DisplayName": "your-aws-account",
    "ID": "your-aws-account-id"
  }
}
```

### 3. IAM Policies
IAM policies can be attached to users, groups, or roles to specify permissions.

#### Example: IAM Policy to Allow a User to Upload Files to a Specific Bucket

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:PutObject",
      "Resource": "arn:aws:s3:::your-bucket-name/*"
    }
  ]
}
```

### Steps to Configure S3 Bucket Permissions:
#### Using the AWS Management Console:
1. **Go to the S3 Console**:
   - Navigate to the AWS Management Console.
   - Open the S3 service.
2. **Select Your Bucket**:
   - Click on the bucket you want to set permissions for.
3. **Permissions Tab**:
   - Go to the `Permissions` tab.
4. **Bucket Policy**:
   - Under `Bucket policy`, click on `Edit` and paste your JSON policy.
5. **Access Control List (ACL)**:
   - Under `Access Control List (ACL)`, you can set permissions for different AWS accounts and groups.
6. **IAM Policies**:
   - Go to the IAM service in the AWS Management Console.
   - Create a new policy or attach an existing policy to a user, group, or role.

### Best Practices while writing permissions
- **Least Privilege**: Always grant the minimum permissions required.
- **Use IAM Roles**: Prefer using IAM roles for applications running on EC2 instances.
- **Monitor and Audit**: Regularly review permissions and use AWS CloudTrail for logging API calls.
- **Bucket Policy vs IAM Policy**: Use bucket policies for cross-account access and IAM policies for permissions within the same account.


## Summary
![image](https://imgur.com/LVxnuoS.png)