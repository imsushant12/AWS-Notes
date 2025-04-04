# AWS IAM

## IAM - Identity and Access Management
- A service that allows secure and controlled access to AWS resources
- Acts as a central hub for managing users, groups, and permissions that define who can access what in an AWS account
- Mitigates risks by enforcing the principle of least privilege, granting only the minimum permissions required for users to perform their tasks
- Grant specific permissions to users and groups for different AWS services and resources
- Securely share access to AWS account with others without giving them root user credentials
- Enhances security by restricting unauthorized access and prevents accidental resource deletion
- Optimizes cost by assigning permissions based on specific needs
- Centrally manage user access and permissions for better control
- **Limitations**:
  - Requires additional configuration compared to using the root user for everything
  - Incorrect permissions can lead to security vulnerabilities or restricted access for legitimate users
  - Requires attention for managing users, groups, policies, etc

## IAM Users
- Individual identities that represent a person or application needing access to AWS resources
- **Use Case**: Creating users for administrators, developers, operations personnel, etc., each with specific permissions
- **Benefits**: Enhances security by following the principle of least privilege and avoids sharing the root user credentials
- **Disadvantages**: Managing individual users can become complex for large teams
- **Limitations**: Users can only belong to a limited number of groups (typically 10)

### IAM Groups
- Collections of IAM users
- Simplifies the management of permissions and access for multiple users with similar roles or responsibilities
- Helps to organize related users with similar permission requirements
- **Use Cases**: Creating groups for developers, operations teams, finance departments, etc., and assign appropriate permissions to the group as a whole
- **Benefits**: Simplifies permission management by applying policies to groups instead of individual users
- **Disadvantages**: Requires additional overhead for managing groups and ensuring users are assigned to the correct ones
- **Limitations**: Permissions assigned to a group apply to all members, so individual user needs within the group requires additional configuration

## Root User vs IAM Administrator
### Root User
- The most powerful account with full, unrestricted access to all resources
- Use it carefully and only for critical tasks

### IAM Administrator
- An IAM user with permissions that grant administrative access to a large portion of AWS services and resources
- Provides lesser control than the root user but is still a powerful role that should be used cautiously

### Adding Users to Groups
- A single user can be added to multiple IAM groups
- The user's effective permissions are the **union** of all permissions from the groups they belong to and any policies attached directly to the user

### Conflicting Permissions Scenario
For an example, if a user belongs to a group with EC2 access and another group with ``Deny All`` access, the resulting permissions would be complex:
- The user would have **no permissions** for any AWS service
- The ``Deny All`` policy would override any permissive settings inherited from other groups

### Copying Policy vs. Adding User to Group
- Copying the policy of an existing group user only copies the permissions
- It does not automatically add the new user to the same group
- Need to explicitly add the new user to the group for them to inherit the group's permissions