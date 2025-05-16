# AWS - CORS

- CORS (Cross-Origin Resource Sharing) is a security mechanism implemented in web browsers that restricts web pages from making requests to a different domain than the one that served the webpage
- Prevent malicious scripts from accessing sensitive data on other websites
- Can define exactly which websites are allowed to access AWS resources, providing granular control over access
- Enables communication between web applications hosted on different domains
- Without CORS, website would not be allowed to show images, videos, fetch data, upload files, etc., from another place as the browser would block it
- Implementing and configuring CORS requires additional development effort

### Enabling CORS
- CORS is not directly enabled or disabled within AWS itself
- Need to configure CORS settings on the server-side component that is responding to requests
- Ways to setup CORS:
  1. **Amazon API Gateway**: Can set CORS rules directly inside API Gateway by defining which websites (origins) are allowed to call APIs, what HTTP methods they can use (like GET, POST), and what headers they can send
  2. **Amazon S3 Buckets**: Can add a CORS policy to bucket to control which websites can read files, upload files, or fetch resources from bucket
  3. **AWS CloudFront**: Can set up CORS rules inside the "Behaviors" settings. This ensures the correct CORS headers are added when users request content through CloudFront