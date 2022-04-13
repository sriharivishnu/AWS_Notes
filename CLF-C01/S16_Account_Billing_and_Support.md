## S16: Account Management, Billing & Support

**AWS Organizations**

- Global service
- Manage multiple AWS accounts
- Main account is the master account
- Cost benefits
  - Consolidated Billing - single payment method
  - Pricing benefits from aggregated usage
  - Pooling of reserved EC2 instances for optimal savings
- API is available to automate account creation

- Can restrict account privileges using Service Control Policies (SCP)



**Multi Account Strategies**

- Strategies
  - Create accounts per department
  - per cost center
  - per dev / test / prod
  - Regulatory restriction (using SCP)
  - Better resource isolation 
  - Separate per-account service limits
  - Isolated account for Logging
- Multi Account vs One Account Multi VPC
- Use tagging standards for billing
- Enable CloudTrail + CW and send logs to central S3 account



**Service Control Policy**

- Whitelist or blacklist IAM actions
- Applied at the OU or Account level
- Does not apply to the Master account
- SCP is applied to all the Users and Roles of the Account, including Root

