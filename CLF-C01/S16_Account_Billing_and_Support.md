## S16: Account Management, Billing & Support

**Account Best Practices**

- Operate multiple accounts using organizations
- Use SCP (service control policies) to restrict account power
- Easily setup multiple accounts with best-practices with AWS Control Tower
- Use Tags & Cost Allocation Tags
- IAM guidelines: MFA, least-privilege, password policy, password rotation
- Config to record all resources configurations & compliance over time
- CloudFormation to deploy stacks across accounts and regions
- Trusted Advisor to get insights, Support Plan adapted to your needs
- Send Service Logs and Access Logs to S3 or CloudWatch Logs
- CloudTrail to record API calls made within account
- If account compromised
  - Change root password, delete and rotate all passwords / keys, contact AWS support





**Billing and Costing Tools - Summary**

- Compute Optimizer
  - Recommends resources' configurations to reduce cost
- Pricing Calculator
  - Cost of services on AWS
- Billing Dashboard
  - High level overview + free tier dashboard
- Cost allocation tags
  - tag resources to create detailed reports
- Cost and usage reports
  - most comprehensive billing dataset
- Cost explorer
  - View current usage and forecast usage
- Billing Alarms
  - us-east-1 - track overall and per-service billing
- Budgets
  - More advanced
  - Track usage, costs, RI, and get alerts
- Savings Plans
  - Easy way to save based on long-term usage (based on specific $ amounts)





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
- SCP does not affect service-linked roles
  - Enable other AWS services to integrate with organizations and can't be restricted
- SCP must have explicit Allow (does not allow anything by default)
  - If there is an explicit Deny, that takes precedence
- Use cases
  - Restrict access to certain services
  - Enforce PCI compliance



**AWS Organization - Consolidated Billing**

- When enabled
  - Combined Usage - combine usage across al AWS accounts in the AWS Organization to share volume pricing, Reserved Instances and Savings Plans discounts
  - One Bill - get one bill for all AWS accounts in the organization
- Management account can turn off Reserved Instances discount for any account



**AWS Control Tower**

- Easy way to set up and govern a secure and compliant multi-account AWS environment
- Benefits
  - Automate the setup of environment
  - Automate ongoing policy managemnt using guardrails
  - Detect policy violations and remediate them
  - Monitor compliance through dashboard
- Runs on top of AWS organizations
  - Automatically sets up Organizations and SCPs



**Pricing Models**

- 4 pricing models

  - Pay as you go: pay for what you use
  - Save when you reserve: minimize risks, predictable budgets
    - Available for EC2, DynamoDB, ElastiCache, RDS, Redshift
  - Pay less by using more: volume-based discounts
  - Pay less as AWS grows

- Free services + Free tier

  - IAM
  - VPC
  - Consolidated Billing
  - Elastic Beanstalk
  - CloudFormation
  - Auto Scaling Groupos
  - Free Tier
    - EC2 t2.micro
    - S3, EBS, ELB, AWS data transfer

  

Compute Pricing - EC2

- Only charge for what you use
- Number of instances
- Configuration
  - Capacity
  - Region
  - OS and software
  - Instance type
  - Instance Size
- ELB running time and amount of data
- Detailed monitoring
- *On-Demand Instances*
  - Min of 60s
  - Pay per second (Linux / Windows) or per hour (other)
- *Reserved Instances*
  - Up to 75% discount compared to On-demand on hourly rate
  - 1 or 3 year commitment
  - All upfront, partial, no
- *Spot instances*
  - 90% discount compared to On-demand on hourly rate
  - Bid for unused capacity
- *Dedicated Host*
  - On-demand
  - Reservation for 1 year or 3 years commitment
- Savings plans
  - Save on sustained usage



Lambda & ECS Pricing

- Lambda
  - Pay per call
  - Pay per duration
- ECS
  - No additional fees, pay for AWS resources stored and created
- Fargate
  - Pay for vCPU and memory resources

S3

- Tiers
- Number and size of objects (price can be tiered based on volume)
- Number and type of requests
- Data transfer OUT of the S3 region
- S3 Transfer Acceleration
- Lifecycle transitions
- EFS
  - Pay per use, has IA & lifecycle rules

EBS

- Volume type (based on performance)
- Storage volume in GB per month provisionned
- IOPS
  - General Purpose SSD: Included
  - Provisioned
  - Magnetic: Number of requests
- Snapshots
  - Added data cost per GB
- Data transfer
  - Outbound data transfer are tiered for volume discounts
  - Inbound is free



RDS

- Per hour billing
- Database characteristics
  - Engine
  - Size
  - Memory class
- Purchase type
  - On-demand
  - Reserved instances (1 or 3 years) with required up-front
- Backup Storage
  - No additional charge for backup storage up to 100% total database storage for a region
- Additional storage
- Number of I/O per month
- Deployment type
  - Single AZ
  - Multiple AZs
- Data transfer
  - Outbound data transfer are tiered
  - Inbound is free



CloudFront

- Pricing depends on geographic region
- Data Transfer out (volume discount)
- Number of HTTP/HTTPS requests



**Networking Costs**

- Free traffic in
- Free between instances same AZ
- \$0.01/GB if private IP, \$0.02/GB if public IP
- $0.02/GB iter-region



**Savings Plan**

- Commit a certain $ amount per hour for 1 or 3 years
- Easiest way to setup long-term commitments on AWS
- EC2 Savings Plan
  - Up to 72% discount compared to On-Demand
  - Commit to usage of individual instance families in a region
  - Regardless of AZ, size, OS, or tenancy
  - All upfront, partial upfront, no upfront
- Compute Savings Plan
  - Up to 66% discount compared to On-Demand
  - Regardless of Family, Region, size, OS, tenancy, compute options
  - Compute Options: EC2, Fargate, Lambda



**AWS Compute Optimizer**

- Reduce costs and improve performance by recommending optimal AWS resources for your workloads
- Helps choose optimal configurations and right-size your workloads
- Uses ML to analyze your resources' config and utilization CW metrics
- Supported
  - EC2, EC2 ASG, EBS, Lambda
- Lower by 25%



**Billing and Costing Tools**

- Estimating costs in the cloud

  - Pricing Calculator
    - Available at https://calculator.aws/
    - TCO Calculators to estimate cost savings to be used in executive presentations

- Tracking costs

  - Billing Dashboard
  - Cost allocation tags
    - Track AWS costs on a detailed level
    - AWS generated tags
      - Automatically applied to the resource you create
      - Starts with Prefix aws:
    - User-defined tags
      - Defined by the user
      - Starts with Prefix user:
      - Can be use for organizing resources
  - Cost and Usage reports
    - Dive deeper into costs and usage - most granular
    - Contains the most comprehensive set of AWS cost and usage data available, including mediate about AWS services, pricing and reservations
    - Can be integrated with Athena, Redshift
  - Cost Explorer
    - Visualize, understand and manage your AWS costs and usage over time
    - Analyze data a high level: total costs and usage across all accounts
    - Monthly, hourly, resource level granularity
    - Choose an optimal Savings plan 
    - Forecast usage up to 12 months based on previous usage

- Monitoring against costs plans

  - Billing Alarms
    - Billing data metric is stored in CW us-east-1
    - Billing data are for overall worldwide AWS costs
    - Not as powerful as AWS Budgets
  - Budgets
    - Create budget and send alarms when costs exceeds the budget
    - 3 types
      - Usage
      - Cost
      - Reservation
    - For Reserved Instances
      - Track utilization
      - Supports EC2, ElastiCache, RDS, Redshift
    - Up to 5 SNS notifications per budget
    - Can filter by
      - Service, Linked Account, Tag, Purchase Option, Instance Type, Region, Availability Zone, API Operation
      - Same options as Cost Explorer
      - 2 budgets are free, then $0.02/day/budget

  

  **Trusted Advisor**

  - No need to install anything
  - High level AWS account assessment
  - Analyze AWS accounts and provides recommendation on 5 categories
    - Cost Optimization
    - Performance
    - Security
    - Fault tolerance
    - Service limits
  - 7 core checks (Basic & Developer Support Plan)
    - S3 Bucket Permissions
    - Security Groups - Specific Ports Unrestricted
    - IAM User (one IAM user minimum)
    - MFA on Root Account
    - EBS Public Snapshots
    - RDS Public Snapshots
    - Service Limits
  - Full Checks (Business & Enterprise support plan)
    - Full checks available on the 5 categories
    - Ability to set CW alarms when reaching limits
    - Programmatic Access using AWS Support API

  

  **Support Plans Pricing**

  - Basic Support
    - Free
    - Customer Service & Communities - 24 x 7 access to customer service, documentation, whitepapers, and support forums
    - AWS Trusted Advisor - access to 7 core TA checks and guidance
    - Personal Health Dashboard
  - Developer
    - 29.00
    - Business hours email access to Cloud Support Associates
    - Unlimited cases / 1 primary contact
    - Case severity / response times
      - General guidance: < 24 business hours
      - System impaired: < 12 hours
  - Business
    - 100.00
    - Intended to be used if production workloads
    - Trusted Advisor - Full set of checks + API access
    - 24 x 7 phone, email, and chat access to Cloud Support Engineers
    - Unlimited cases / unlimited contacts
    - Access to Infrastructure Event Management for additional fee
    - Case severity / response times
      - Production system impaired: < 4 hours
      - Production system down: < 1 hour
  - Enterprise On-Ramp
    - 5,500.00+
    - Intended for production or business critical
    - Access to a pool of Technical Account Managers
    - Concierge Support Team (billing + account best practices)
    - Infrastructure Event Management, well-architected * operations reviews
    - Case Severity / response times
      - ...
      - Business-critical system down: < 30 min
  - Enterprise
    - 15,000.00
    - mission critical workloads
    - Access to designated Technical Account Manager
    - Case Severity / response times
      - ...
      - Business-critical system down: < 15 minutes

  





