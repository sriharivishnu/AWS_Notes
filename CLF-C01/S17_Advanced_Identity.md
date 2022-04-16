## S17: Advanced Identity

**Summary**

- IAM
  - Identity and access management inside AWS account 
  - Users in company
- Organizations
  - Manage multiple AWS accounts
- STS (Security Token Service)
  - Temporary, limited-privileges credentials to access AWS resources
- Cognito
  - Create a database of users for mobile + web apps
- Directory Services 
  - Integrate Microsoft Active Directory
- Single Sign-On
  - One login for multiple AWS accounts / third-party apps



**STS (Security Token Service)**

- Enables you to create temporary, limited-privileges credentials to access your AWS resources
- Short-term credentials
  - you configure expiration period
- Use cases
  - Identity federation
    - Manage user identities in external systems and provide STS tokens to access AWS resources
    - IAM roles for cross/same account access
    - IAM Roles for EC2 
      - Provide temp creds for EC2 instances to access AWS resources



**Cognito**

- Provide identity for Web and Mobile app users (potentially millions)
- (Not IAM)
- Has a database of users (has a variety of login providers)



**Directory Services**

- Microsoft Active Directory
  - Found on Windows Server with AD Domain Services
  - Database of objects
    - User accounts, computers, printers, file shares, security groups
  - Centralized security management, create account, assign permissions
- AWS Directory Services
  - Managed Microsoft AD
    - Supports MFA
    - Establish trust connections with on-premise AD
  - AD Connector
    - Directory Gateway (proxy) to redirect to on-premise AD
    - Users are managed on the on-premise AD
  - Simple AD
    - AD-compatible managed directory on AWS
    - Cannot be joined with on-premise AD



**Single Sign-On (SSO)**

- Centrally managed Single Sign-On to access multiple accounts and 3rd -party business applications
- Integrated with AWS Organizations
- (Like Okta)
- Supports SAML 2.,9 markup
- Can be integrated with on-premises AD



