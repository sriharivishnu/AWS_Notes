## S09: Deployments at Scale

#### Summary

- Cloud Formation
  - Infrastructure as Code, works with most AWS resources
  - Repeat across Regions + Accounts
- Beanstalk
  - Platform as a Service (limited to certain languages)
  - Deploy code consistenly with known architecture
- CodeDeploy (hybrid): deploy & upgrade any application onto servers
- Systems Manager (hybrid): patch, configure and run commands at scale
- OpsWorks (hybrid): managed Chef and Puppet in AWS



- CodeCommit: Store code in private git repository (version controlled)
- CodeBuild: Build & test code in AWS
- CodeDeploy: Deploy code onto servers
- CodePipeline: Orchestration of pipeline (from code to build to deploy)
- CodeArtifact: Store software packages / dependencies on AWS
- CodeStar: Unified view for allowing developers to do CI/CD and code
- Cloud9: Cloud IDE with colab
- AWS CDK: Define cloud infrastructure with programming language

#### CloudFormation

- Declarative way of outlining your AWS Infrastructure, for any resources (most are supported)
- e.g.
  - Security Group
  - 2 EC2 instances
  - S3 Bucket
  - With ELB in front of machines
- Creates for you in the right order with the exact configuration specified by you
- Benefits
  - Infrastructure as code
    - No manual resource creation (good for control)
    - Changes to the infrastructure are reviewed through code
  - Cost
    - Each resource within a stack is tagged with an identifier so you can see how much a stack costs
    - Estimate the costs of your resources using CloudFormation template
    - Savings strategy: In dev, could automate deletion of templates at 5 PM and recreated at 8 AM (safely)
  - Productivity
    - Ability to destroy and recreate an infrastructure on the cloud on the fly
    - Automated generation of diagram for templates
    - Declarative programming (no need to figure out ordering and orchestration)
  - No need to re-invent the wheel
    - There are existing templates on the web
    - Leverage docs
  - Supports almost all AWS resources
    - Can use custom resources otherwise
  - Stack Designer
    - Can see all the resources
    - Can see the relations between components

#### CDK

- Can use programming language (Python, JavaScript) to define infrastruture
- Compiled into CloudFormation template



#### Elastic Beanstalk

- Developer centric view of deploying an application on AWS
- Uses all same components: EC2, ASG, ELB, RDS etc
- All in one view
- Still have full control over the configuration
- PaaS = Platform as a Service
- Managed Service
  - Instance configuration / OS is handled by Beanstalk
  - Deployment strategy is configurable but performed by Elastic Beanstalk
  - Capacity provisioning
  - Load balancing & auto-scaling
  - Application health-monitoring & responsiveness
- Application code is developer responsibility
- Three architecture models
  - Single Instance deployment: good for dev
  - LB + ASG: production
  - ASG only: non-web apps in production
- Fully health monitored (part of the service) pushes logs to CloudWatch



#### CodeDeploy

- Deploy application automatically
- Works with EC2 Instances + On-Premises Servers (hybrid service)
- Servers must be provisioned and configured ahead of time with the CodeDeploy Agent



#### CodeCommit

- Stores code within AWS
- Source-control service that hosts Git-based repositories
- Automatically versioned
- Benefits
  - Private, secured, integrated
  - Scalable and available
  - Fully managed



#### CodeBuild

- Builds service in the cloud
- Compiles source code, run tests, and produces packages that are ready to be deployed

- Benefits
  - Fully managed, serverless
  - Continuously scalable & highly available
  - Secure
  - Pay-as-you-go pricing - pay for build time



#### CodePipeline

- Orchestrate the different steps to have code automatically pushed to production
- Code => Build => Test => Provision => Deploy
- CI/CD

CodeCommit -> CodeBuild -> CodeDeploy -> Elastic Beanstalk

- Benefits
  - Fully managed, compatible with AWS services + GitHub
  - Fast delivery & rapid updates



#### CodeArtifact

- Packages depend on each other to be built
- Storing and retrieving these dependencies is called artifact management
- Works with Gradle, npm, yarn, pip etc.
- Developers and CodeBuild can then retrieve dependencies straight from CodeArtifact
- Team needs artifact management system / place to store code dependencies



#### CodeStar

- Unified UI to manage software development activities in one place
- Quick way to get started to correctly set-up CodeCommit, CodePipeline, CodeBuild, CodeDeploy, EB, EC2 etc.
- Edit code in the cloud using AWS Cloud9



#### AWS Cloud9

- Cloud IDE for writing, running, and debugging code
- Cloud IDE can be used within a web browser meaning you can work on projects from anywhere
- Code collaboration in real-time



#### AWS Systems Manager (SSM)

- Helps manage EC2 and On-Premises systems 
- Hybrid AWS Service
- Get operational insights about state of infrastructure
- Suite of 10+ products
- Features
  - Patching automation for enhanced compliance
  - Run commands across entire fleet of servers
  - Store parameter configuration with SSM Parameter Store
- Windows + Linux OS
- Need to install SSM agent onto systems
- Can run commands, patch and configure servers



#### AWS OpsWorks

- Chef & Puppet (Non-AWS) help perform server configuration automatically, or repetitive actions
- Work great with EC2 & On-Premises VM
- AWS OpsWorks = Managed Chef & Puppet
- Alternative to AWS SSM
- Only provision **standard AWS resources**
  - EC2 instances, databases, load balancers







