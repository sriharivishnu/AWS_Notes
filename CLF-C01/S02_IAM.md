## S02 IAM - Identity and Access Management

#### Summary

- Users: mapped to a physical user, has a password for AWS Console
- Groups: contains users only
- Policies: JSON document that outlines permissions for users or groups
- Roles: for EC2 instances or AWS services
- Security: MFA + Password policy
- AWS CLI: manage your AWS services using the command-line
- AWS SDK: manage your AWS services using a programming language
- Access Keys: access AWS using the CLI or SDK
- Audit: IAM Credential Reports & IAM Access Advisor



- Global Service

#### Users & Groups

- Root Account is created by default (shouldn't be used or shared)

- Users are people within you organization and can be grouped
- Groups only contain users, not other groups
- Users don't have to belong to a group, and a user can belong to multiple groups



- Users or groups can be assigned JSON documents called policies

<img src="/Users/sriharivishnu/Documents/Notes/AWS/CLF-C01/S02_IAM-images/Screen Shot 2022-03-31 at 1.34.36 AM.png" alt="Screen Shot 2022-03-31 at 1.34.36 AM" style="zoom:30%;" />

- Policies define the permissions of the users
- Don't give more permissions than a user needs (least privilege principle)

#### IAM Policies Inheritance

- All users inherit policies from group(s) they belong to
- Users without groups can have policies called **inline policies**

![Screen Shot 2022-03-31 at 1.33.11 AM](/Users/sriharivishnu/Documents/Notes/AWS/CLF-C01/S02_IAM-images/Screen Shot 2022-03-31 at 1.33.11 AM.png)

Policies Structure

- Version
- Id (identifier for policy) (optional)
- Statement (one or more individual statements) (required)
  - Sid (Identifier for statement)
  - Effect (whether statement allows or denies) 
  - Principal (account/user/role to which this policy applied to)
  - Action: list of action sthis policy allows or denies
  - Condition: conditions for when this policiy is in effect



IAM Password Policy

- You can set strong passwords
- Set minimum password length
- Require specific character types (lowercase, symbols, etc.)
- Allow IAM users to change their own passwords
- Require change password after sometime
- Prevent password re-use



Multi factor Authentication - MFA

- Users have access to your account and can pssible change configurations or delete resources in your AWS account
- Protect Root Accounts and IAM users
- MFA = password you know + security device you own
- (if password is stolen, hacker needs device as well)
- You can use
  - Virtual MFA device
    - Authy (multi-device)
    - Google Authenticator
  - Universal 2nd Factor (U2F) Security Key
    - YubiKey (support for multiple root and IAM users using single security key)
  - Hardware key Fob MFA device
  - Hardware Key Fob MFA Device for AWS GovCloud



##### How Can users access AWS

1. AWS Management Console (Password + MFA)
2. AWS Command Line Interface (CLI): (Access keys)
   - Open-source, direct access to AWS services, develop scripts to manage resources
3. AWS Software Developer Kit (SDK) - for code (Access keys)
   - Language-specific APIs (set of libraries)
   - Access and manage AWS services programmatically
   - Embedded within application
   - JavaScript, Python, PHP, .NET, Ruby, Java, Go, Node.js, C++
   - Mobile SDKs (android, Its)
   - IoT Device SDKs (Embedded C, Arduino)

Access keys are generated through the AWS Console

Users manage their own access keys

- Access Key ID ~= username
- Secret Access Key ~= password



##### IAM Roles for Services

- Services need to perform actions on you behalf
- We will assign permissions to AWS services with IAM Roles
- Common Roles
  - EC2 Instance Roles
  - Lambda Function Roles
  - Roles for CloudFormation



IAM Security Tools

- IAM Credentials Report (account-level)

  - report that lists all you account' users and the status of their various credentials

- IAM Access Advisor (user-level)

  - Shows the service permissions granted to a user and when last accessed

  - Use information to revise policies

    

#### IAM Best Practices

- Don't use root account except for AWS account setup
- One physical user = One AWS user
- Assign users to groups and assign permissions to groups
- Create a strong password policy
- Use MFA
- Crate and use roles for permissions to AWS services
- Use access keys for CLI + SDK
- Audit permissions management using Credentials Report



#### Shared Responsibility Model for IAM

- AWS
  - Infrastructure (global network security)
  - Configuration and vulnerability analysis
  - Compliance validation
- You
  - Users, Groups, Roles, Policies management and monitoring
  - Enable MFA on all accounts
  - Rotate all keys often
  - Use IAM tools to apply appropriate permissions
  - Analyze access patterns & review permissions







