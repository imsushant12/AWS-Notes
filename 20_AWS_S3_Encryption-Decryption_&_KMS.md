# AWS - S3 Encryption-Decryption and KMS

## S3 Encryption
- Refers to the process of encrypting data stored in Amazon S3 to ensure confidentiality and data protection
- Offers various encryption options to secure S3 data at rest
- Encryption operations may introduce additional processing overhead, potentially impacting performance
- Managing encryption keys securely and ensuring key availability can be complex and require additional resources

## Types of S3 Encryption
### 1. Server-Side Encryption with Amazon S3 Managed Keys (SSE-S3)
- Simplest form of encryption where Amazon S3 handles everything — it encrypts data at rest using **AES-256** encryption keys that Amazon manages
- User does not have direct access or control over the encryption keys
- If the organization requires custom key management policies, this may not be sufficient
- **Benefits**:
  - No need to write any code or set up encryption manually
  - No extra cost as it is managed by AWS
  - Works automatically when upload objects via the S3 console or API
- **Use Cases**:
  - In case of basic data protection
  - Suitable for internal data storage, logs, or backups that don’t require strict key management
  - Ideal when compliance doesn’t mandate custom key control

### 2. Server-Side Encryption with Customer Managed Keys (SSE-C/KMS)
- Often referred to as SSE-KMS because it integrates with AWS Key Management Service (KMS)
- Encrypts data on the server-side, but user can control the keys via AWS KMS
- Allows access control and detailed audit trails (tracks every use of encryption keys using AWS CloudTrail)
- Requires additional setup and configuration
- There is a costs for each key used and for each encryption/decryption request via KMS
- **Use Cases**:
  - In case of need of strict control
  - Ideal for sensitive data such as financial records, PII (personally identifiable information), or healthcare data
  - When auditing and compliance reporting is essential

### 3. Client-Side Encryption
- Data is encrypted on the client’s end (application or system) before it’s even uploaded to Amazon S3
- Can either use:
  - AWS SDKs with KMS integration
  - Own encryption libraries and key management
- Provides maximum control (can manage both encryption and decryption)
- Provides end-to-end encryption (AWS only sees encrypted blobs, not the raw data)
- More complex as code is need to be written which handles encryption/decryption
- Has risk of key mismanagement if it is not implemented carefully
- Can impact performance, especially with large files
- **Use Cases**:
  - When data privacy is extremely sensitive (e.g., defense, legal, or medical data)
  - When company policy dictates that AWS should not have access to unencrypted data — even temporarily
  - For cross-region applications that need encryption consistent with internal security tools

## AWS Key Management Service (KMS)
- A managed service for creating, managing, and using encryption keys
- Provides secure storage and control over encryption keys used for S3 objects and other AWS services
- Enhances security and granular control over encryption keys
- Provides a centralized management of keys for various AWS services
- It has additional configuration and cost considerations compared to SSE-S3
- **Working**:
  1. Create a KMS key, which serves as the master key for encrypting and decrypting data
  2. Configure S3 to use the KMS key for server-side encryption (SSE-C/KMS)
  3. When data is uploaded or downloaded from S3, KMS encrypts or decrypts it using the designated KMS key