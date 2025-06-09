# AWS - Amplify

## AWS Amplify

- A set of tools and services that enables front-end developers to quickly build full-stack web and mobile applications on AWS
- Provides hosting, authentication, GraphQL/REST APIs, storage, and analytics — all without needing to manage infrastructure manually

### Advantages of AWS Amplify

1. **Rapid Development**
  - Simplifies frontend + backend integration
  - Easy scaffolding of auth, APIs, and DB
2. **Fully Managed Hosting**
  - Automatic CI/CD from GitHub/GitLab/Bitbucket
  - Serverless scaling and HTTPS included
3. **Built-in Authentication**
   - Powered by Amazon Cognito
   - Easy login/sign-up/social provider integration
4. **Backend-as-a-Service (BaaS)**
  - Configure GraphQL (AWS AppSync) or REST APIs
  - Add Storage (S3), Databases (DynamoDB), Functions (Lambda)
5. **Multiple Environments Support**
  - Seamlessly manage development, staging, and production
6. **Integration with Frontend Frameworks**
  - Supports React, Angular, Vue, Next.js, Flutter, iOS, Android, and more

### Disadvantages of AWS Amplify

1. **Limited Backend Flexibility** - Best suited for common use cases; advanced use cases may hit limits
2. **Cost Escalation** - Free tier is generous, but prices grow with traffic & usage
3. **Learning Curve for AWS Ecosystem** - IAM, Cognito, and CLI can be confusing to beginners
4. **Vendor Lock-in** - Apps are closely tied to AWS-specific services
5. **Slow Debugging for Some Services** - AppSync and Cognito errors can be cryptic without logging

### Use Cases
- Web/mobile app with user authentication
- MVPs and prototypes with quick backend setup
- Serverless CMS or blogs with GraphQL APIs
- Ecommerce frontends with Amplify + DynamoDB
- IoT dashboard frontends powered by serverless APIs

### When to Use AWS Amplify?

- You need **quick deployment** without managing infrastructure
- You’re building a **JAMstack** or single-page app
- You want **tight AWS integration** (Lambda, S3, DynamoDB)
- You don’t want to configure CI/CD and hosting separately
- You are working on **a serverless, scalable project**

## Difference from Other AWS Hosting Options
| Feature/Service | **Amplify**  | **S3 + CloudFront** | **Elastic Beanstalk**  | **EC2 Manual Setup** |
|---|---|---|---|---|
| Hosting Type  | Static & full-stack | Static only| Dynamic (Web App) | Any type |
| CI/CD Support | Yes (built-in) | No | Yes (limited) | No |
| Serverless Backend | Yes | No  | No  | Yes (manual setup) |
| DevOps Complexity  | Low  | Low | Medium  | High  |
| Scaling | Auto (managed) | Auto (CloudFront) | Auto with limits | Manual or custom  |
| Best Use Case | Modern full-stack apps | Static websites | Java/.NET monolithic apps | Total control / legacy |

## AWS Amplify Workflow (CLI)
1. **Initialize Amplify in Project Directory**

  ```bash
  amplify init
  ```

  - Sets up a backend environment
  - Connects with AWS account

2. **Add Backend Features**

  - Example commands:

    ```bash
    amplify add auth      # Adds Cognito-based auth
    amplify add api       # Adds GraphQL or REST API
    amplify add storage   # Adds S3 bucket
    amplify add function  # Adds Lambda function
    ```

3. **Push Configuration to AWS**

  ```bash
  amplify push
  ```

  - Provisions resources using CloudFormation

4. **Use Amplify Libraries in Frontend**

  - Example in React:

    ```javascript
    import { Auth } from 'aws-amplify';
    Auth.signIn(username, password);
    ```

5. **Host Frontend**

  ```bash
  amplify add hosting
  amplify publish
  ```

  - Or use **Amplify Console** to connect Git repo → auto-deploy on push

## Cloud Sandbox

A **Cloud Sandbox** is a secure, isolated AWS (or other cloud provider) environment used for:

- **Testing**, **developing**, or **experimenting** without affecting production
- **Training and demos** for teams or students
- **Trying new services** safely and temporarily

### Key Features

- Limited scope (IAM permissions or time-based)
- Often pre-configured with sample data
- Can be destroyed after testing

### Use Cases

- Internal team testing or POC builds
- Education platforms (like AWS Educate, Qwiklabs)
- Secure evaluation of 3rd party tools or packages

## AWS Amplify Gen 2

**Amplify Gen 2** is a new evolution of Amplify that introduces **Infrastructure-as-TypeScript**, more dev-friendly workflows, and increased customization

### Features of Amplify Gen 2

1. **TypeScript-based Backend Definition**
  -Define backend like auth, storage, APIs directly in code
  - Full code control over backend infra

2. **Pull Request Previews**
  - Auto-generated preview environments per PR
  - Great for team collaboration and QA

3. **Improved CI/CD**
  - Uses **GitHub Actions** or custom workflows
  - More flexibility than Amplify Console-only pipelines

4. **Testing Support**

  - Easily unit test backend logic and APIs before pushing

5. **Environment Awareness**

  - Scoped secrets, settings, and logic based on dev/stage/prod

6. **Next.js, Nuxt, Expo Support**

  - First-class support for fullstack JS/TS frameworks

### Amplify Gen 1 vs Gen 2

| Feature | **Amplify Gen 1** | **Amplify Gen 2** |
|---|---|---|
| Backend Definition | CLI + JSON/CloudFormation | TypeScript (IaC) |
| CI/CD | Amplify Console only | GitHub Actions / Custom |
| Testing | Minimal support | Unit and integration testing built-in |
| Pull Request Previews | Not supported | Supported |
| Code-first Experience | No | Yes |
| Flexibility | Limited to Amplify abstractions | High customization |
