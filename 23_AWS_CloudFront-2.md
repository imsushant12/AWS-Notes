# AWS - CloudFront

## Geographic Restrictions
- A feature that allows restricting access to CloudFront content based on a user's geographic location
- **Benefits**:
  - Enforces compliance with regional regulations (e.g., data privacy laws)
  - Restricts access to specific countries for licensing or content distribution purposes
  - Reduces costs by limiting bandwidth usage in certain regions
- **Limitations**:
  - Requires careful configuration to avoid unintended access limitation
  - May introduce complexity for managing access across multiple regions
- **Use Cases**:
  - Restricting access to gambling or age-gated content in certain countries
  - Delivering geographically specific marketing campaigns
  - Controlling access to copyrighted material based on licensing agreements

## Other CloudFront Features
### Logging
- CloudFront logs user requests and responses, providing valuable insights into content delivery performance, user behavior, and potential errors
- Logs can be integrated with Amazon CloudWatch for analysis and visualization

### Restrictions
- Can restrict access to content based on factors beyond geography, such as HTTP methods (e.g., allow only GET requests) or specific query strings

### Custom Headers
- Modify or add custom headers to requests and responses for enhanced control over content delivery behavior

### Origin Field-Level Encryption
- Encrypt specific fields within objects stored in origin (like S3) before sending them to CloudFront, adding an extra layer of security for sensitive data

### Security Features
- CloudFront offers various security features beyond geographic restrictions, including:
  - **Signed URLs**: Grant temporary access to specific content with controlled expiration times
  - **Origin Access Identity (OAI)**: Define a secure identity for CloudFront to access origin server, restricting access from unauthorized sources
  - **AWS WAF integration**: Integrate AWS WAF web application firewall to filter requests and block malicious traffic before it reaches origin