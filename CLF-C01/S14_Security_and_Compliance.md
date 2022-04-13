## S14: Security and Compliance

##### Summary

- Shared Responsibility on AWS
- Shield
  - Automatic DDoS Protection + Advanced has 24/7 support
- WAF
  - Firewall to filter incoming requests based on rules
- KMS
  - Encryption keys managed by AWS
- CloudHSM
  - Hardware encryption, we manage encryption keys
- AWS Certificate Manager
  - Provision, manage and deploy SSL/TLS certificates
- Artifact
  - Get access to compliance reports such as PCI, ISO etc.
- GuardDuty
  - Find malicious behaviour with VPC, DNS & CloudTrail logs
- Inspector
  - For EC2 only, install agent and find vulnerabilities
- Config
  - Track config changes and compliance against rules
- Macie
  - Find sensitive data (e.g. PII) within S3 buckets
- CloudTrail
  - Track API calls made by users within account
- Security Hub
  - Gather security findings from multiple AWS accounts
- Amazon Detective
  - Find the root cause of security issues
- AWS Abuse
  - Report AWS resources used for abusinve or illegal purposes
- Root user privileges:
  - Change account settings 
  - Close your AWS account 
  - Change or cancel your AWS Support plan
  - Register as a seller in the Reserved Instance Marketplace

**AWS Shared Responsibility Model**

- AWS Responsibility is Security of the Cloud
  - Protecting infrastructure (hardware, software, facilities, networking)
  - Managed services like S3, DynamoDB, RDS
- Customer Responsibility is Security in the Cloud
  - For EC2 instance, customer is responsible for management of the guest OS (including security patches + updates), firewall & network configuration, IAM
  - Encrypting app data
- Shared Controls
  - Patch Management
  - Configuration Management
  - Awareness & Training

<img src="S14_Security_and_Compliance-images/Screen Shot 2022-04-09 at 10.00.57 PM.png" alt="Screen Shot 2022-04-09 at 10.00.57 PM" style="zoom:50%;" />



**DDOS Protection**

- DDOS
  - Distributed Denial-of-Service
- AWS Shield Standard
  - Protects against DDOS attack for website and apps
  - No additional costs
  - Free service activated for every AWS customer
  - Provides protection from attacks such as SYN/UDP Floods, Reflection, layer 3/layer 4 attacks (TCP)
- AWS Shield Advanced
  - 24/7 premium DDoS protection + access to DDOS response team
  - Optional - $3000 per moth per organization
  - EC2, ELB, CloudFront, Global Accelerator, Route 53
  - Protect against higher fees during spikes due to DDOS
- AWS WAF
  - Filters specific requests based on rules
  - Protects applications from common web exploits (layer 7 - HTTP)
  - Deploy on ALB, API Gateway, CloudFront
  - Define Web ACL
    - Rules: IP Addresses, HTTP headers, HTTP Body, URI Strings
    - Protects against SQL Injection + XSS
    - Size constraints, geo-match
    - Rate-based rules
- CloudFront and Route 53
  - Availability protection using global edge network
  - Combined with AWS Shield, provides attack mitigation at the edge
- Leverage AWS Auto Scaling Groups



**Penetration Testing**

- Allowed without prior approval for 8 services
  - EC2, RDS, CloudFront, Aurora, API Gateways, Lambda + Lambda Edge, Lightsail, Elastic Beanstalk
- Prohibited
  - DNS zone walking via Amazon Route 53 Hosted Zones
  - DDOS
  - Port, Protocol, Request flooding



**Encryption**

- At rest: data stored or archived on a device
  - Hard disk, RDS instance, S3 Glacier Deep Archive
- In Transit: Data being moved from one location to another
  - Transfer from on-premises to AWS, EC2 to DynamoDB
  - Transferred on the network
- Leverage encryption keys to have both

- **KMS - Key Management Service**
  - Encryption is KMS
  - AWS manages th encryption keys 
  - Opt-ins
    - EBS volumes
    - S3 Buckets
    - Redshift database
    - RDS database
    - EFS drives
  - Encryption Automatically Enabled
    - CloudTrail Logs
    - S3 Glacier
    - Storage Gateway
- **CloudHSM**
  - AWS provisions encryption hardware, but we manage keys ourselves
  - Dedicated hardware
  - HSM device is tamper resistant - FIPS Level 3 compliance

- **Customer Master Keys**
  - Customer Managed CMK
    - Create, manage and used by the customer
    - Rotation policy possible
    - Bring-your-own key possible
  - AWS managed CMK
    - Created, managed and used on the customer's behalf by AWS
    - Used by AWS services
  - AWS owned CMK
    - Collection of CMKs that an AWS service owns and maanges to use in multiple accounts
    - AWS can use to protect resources in your account, but you cannot view the keys
  - CloudHSM Keys
    - Generated from CloudHSM hardware device
    - Operations are performed within the CloudHSM Cluster



**AWS Certificate Manager**

- Easy provision, manage and deploy SSL/TLS Certificates
- In-flight encryption for websites (HTTPS)
- Supports public + Private Certs
- Free of charge for public
- Automatic TLS Cert renewal
- Integrations with
  - ELB
  - CloudFront Distributions
  - APIs on API Gateway



**Secrets Manager**

- Meant for storing secrets
- Force rotation of secrets every X days
- Automate generation of secrets on rotation (uses Lambda)
- Integration with Amazon RDS (MySQL etc.)
- Secrets are encrypted using KMS
- Mostly mean for RDS - Secret + rotated



**AWS Artifact**

- Portal providing on-demand access to AWS compliance docs + AWS agreements
- Artifact Reports
  - Download AWS security and compliance documents from thir-party auditors
- Artifact Agreements
  - Allows you to review, accept and track the status of AWS agreements for an individual account or in your organization
- Can be used to support internal audit or compliance



**GuardDuty**

- Intelligent Thread discovery to protect AWS account
- Use ML algos, anomaly detection, 3rd party data
- One click to enable (30 days trial), no need to install software
- Input data
  - CloudTrail Events Logs - unusual API calls, unautorized deployments
  - VPC Flow Logs - unusual internal traffic, unusal IP address
  - DNS Logs - compromised EC2 instances sending encoded data within DNS queries
  - Kubernetes Audit Logs
- Can setup CloudWatch Event rules to be notified of findings
- Can protect against CryptoCurrency attacks



**Amazon Inspector**

- Automated Security Assessments
  - Package vulnerabilities
  - Network reachability (EC2 only)
- *EC2 Instances*
  - AWS System Manager agent
  - Analyze agains unintended network accessibility
  - Analyze the running OS against known vulnerabilities 
- *Containers pushed to ECR*
  - Assessment of containers as they are pushed
- Reporting & integration with AWS Security Hub
- Send findings to Amazon Event Bridge



**Config**

- Auditing and recording compliance of AWS resources
- Helps record configurations and changes over time
  - can be stored into S3
- Questions
  - Is there unrestricted SSH access to my security groups?
  - Do my buckets have any public access?
  - How has my ALB configuration changed over time?
- Can receive alerts for changes
- Per-region service
- Can be aggregated across accounts and regions



**Amazon Macie**

- Amazon Macie is a fully managed data security and data privacy service that uses machine learning and pattern matching to discover and protect your sensitive data in AWS.
- Macie helps identify and alert you to sensitive data, such as PII
- Analyses S3 buckets



**AWS Security Hub**

- Central security tool to manage security across several AWS accounts and automate security checks
- Dashboards showing current security and compliance status
- Automatically aggregates alerts in predefined or personal findings formats
  - GuardDuty
  - Inspector
  - Macie
  - IAM Access Analyzer
  - AWS System Manager
- Must enable the AWS Config Service



**Amazon Detective**

- GuardDuty, Macie, and Security Hub are used to identify potential security issues, or findings
  - Sometimes require deeper analysis to isolate the root cause
- Amazon Detective analyzes, investigates, and identifies the root cause of security issues or suspicious activities (using ML and graphs)
- Automatically collects and processes events from VPC Flow Logs, CloudTrail, GuardDuty and create unified view
- Provides visualizations as well



**AWS Abuse**

- Report suspected AWS resources used for abusive or illegal purposes
  - Spam
  - Port scanning - sending packets to your ports to discover unsecured ones
  - DoS or DDoS attacks 
  - Intrusion attempts
  - Hosting objectionable or copyrighted content
  - Distributing malware
- Contact the AWS Abuse team using for or email `abuse@amazonaws.com`



**Root User Privileges**

- Account owner
- Has complete access to all AWS services and resources
- Lock away your AWS account root user access keys
- Do not use the root account for everyday tasks 
- Actions only done by root user
  - Change account settings (name, email, root user pswd)
  - View certain tax invoices
  - Close AWS account
  - Restore IAM user permissions
  - Change or cancel AWS Support plan
  - Register as a seller in Reserved Instance Marketplace
  - Configure S3 bucket to enable MFA
  - Edit or delete S3 bucket policy that includes invalid VPC ID or VPC endpoint ID
  - Sign up for GovCloud



