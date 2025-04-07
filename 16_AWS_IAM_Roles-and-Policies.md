# IAM - Roles, Policies, and Identity Providers

- IAM is the AWS service which handles the authorization and authentication
- For ensuring secure and controlled access, IAM has:
  - IAM Roles
  - IAM Policies
  - IAM Identity Providers

## IAM Roles
- Temporary identities that can be used by trusted entities, such as users, applications, or services, to perform specific tasks (provide temporary access based on defined permissions)
- Unlike users, roles don't have long-term credentials
- Role usage and permissions are logged in AWS CloudTrail which enables audit trails and compliance monitoring
- Permissions assigned to a role depend on the policies attached to it
  
### Types of IAM Roles
1. **AWS Service Roles**: Used by AWS services to access other AWS resources on behalf of users or services
2. **Cross-Account Roles**: Allow users or resources in one AWS account to use a role in another AWS account
3. **Federated Roles**: Enable federated users to access AWS resources through identity providers such as SAML or OpenID Connect

## IAM Policies
- JSON documents that define the actions a user or role can perform on AWS services and resources
- Specify what resources can be accessed, what actions can be taken (e.g., read, write, delete), and under what conditions
- Helps to define precise permissions for users and roles, to ensure that they only have the access required for their tasks
- A policy can be reused across different users or roles with similar needs

### Types of IAM Policies
1. **Managed Policies**: Predefined policies provided and created by AWS that can be attached to IAM users, groups, or roles. They are maintained and updated by AWS
- **Inline Policies**: Policies that are embedded directly into an IAM user, group, or role, providing more granular control and customization

## IAM Identity Providers
- IAM Identity Providers (IdPs) are external identity services that allow to use existing authentication mechanisms for accessing AWS resources
- Instead of creating separate IAM users for external users, IdP can be trusted to verify the identity and provide temporary access through IAM roles
- Can use existing corporate login system (e.g., Active Directory, Okta) for access to AWS resources. This simplifies user management
- But, it introduces an additional layer of complexity into authentication process
- **Use Cases**:
  - Granting employees access to AWS resources based on their existing corporate credentials
  - Allowing external collaborators to access specific AWS resources for project work, without creating IAM users for them

### Types of IdPs
1. **AWS Directory Service**: Managed directory service compatible with various IdPs like Microsoft Active Directory
2. **SAML-based IdPs**: Third-party IdPs that support the SAML (Security Assertion Markup Language) protocol for federated authentication
3. **Web Identity Federation**: Allows users to sign in to web application using existing social identities (e.g., Google, Facebook)

## Use Case - User, Group, Policy, Role
- **User**: To grant long-term access to specific individuals or services
- **Group**: For multiple users who need the same set of permissions
- **Policy**: To define specific permissions for users, groups, or roles
- **Role**: To grant temporary access or provide cross-service permissions without compromising security