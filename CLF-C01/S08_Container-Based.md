## ECS, Fargate, Lambda, Batch, LightSail

#### Summary

- Docker: Container tech to run application
- ECS: run Docker containers on EC2 instances (need to provision)
- Fargate: Run Docker containers without provisioning infrastructure (Serverless)
- ECR: Private Docker Images Repository
- Batch: run batch jobs on AWS across managed EC2 instances (on top of ECS service)
- Lightsail: predictable & low pricing for simple application + DB stacks
- Lambda
  - Serverless, FaaS, seamless scaling
  - Billing
    - time run x RAM provisioned
    - Number of invocations
  - Language Support: many programming languages except (arbitrary) Docker
  - Invocation time: up to 15 min
  - Use cases:
    - Serverless cron + create thumbnails for images uploaded to S3
- API Gateway: expose lambda functions as REST API

#### ECR

- Elastic Container Registry
- Private Docker Registry on AWS
- Store Docker images so they can be run by ECS or Fargate

#### ECS

- Elastic Container Service
- Launch Docker containers on AWS
- Must provision & maintain the infrastructure (EC2 instances)
- AWS takes care of starting / stopping containers
- Has integrations with Application Load Balancer



#### Fargate

- Launch Docker containers on AWS
- You do not provision the infrastructure (no EC2 instances to manage) - simpler!
- Serverless offering
- AWS just runs containers for you based on the CPU / RAM needed



#### Serverless

- Developers don't have to manage servers anymore
- Just deploy code (or functions)
- Initially FaaS
- Pioneered by AWS Lambda, but not includes databases, messaging, storage etc.
- Serverless does not mean there are no servers! (you just don't see them)
- Examples
  - S3
  - DynamoDB
  - Fargate
  - Lambda



#### Lambda

- Virtual Functions - no servers to manage
- Limited by time - short executions
- Run on-demand
- Scaling is automated!

Advantages

- Easy Pricing:
  - Pay per request + per compute time
  - Free tier: 1M Lamdba Requests + 400k GBs of compute time
- Integrated with whole AWS suite of services
- Event-Driven: functions get invoked when needed (Reactive)
- Integrated with many programming languages
  - Node.js, Python, Java, C#, Golang, C#, Ruby, Custom Runtime API
  - Lambda Container Image (must implement lambda Runtime API)
    - ECS / Fargate is preferred
- Easy monitoring through CloudWatch
- Easy to get more resources: Up to 10GB of RAM
- Increasing RAM -> Improves CPU + Network
- Very cheap to run AWS Lambda



#### API Gateway

- Building a serverless API
- Fully managed service to create, publish, maintain, monitor and secure APIs
- Serverless + Scalable
- Supports RESTful APIs and WebSocket APIs
- Support for security, user auth, API throttling, API keys, monitoring



#### AWS Batch

- Fully managed batch processing at any scale
- Run 100,000s of computing batch jobs on AWS
- Batch job with a start and an end (opposed to continuous)
- Batch will dynamically launch EC2 instances or Spot Instances
- Batch provisions the right amount of compute / memory
- You submit or schedule batch jobs and AWS batch does the rest
- Batch jobs are defined as Docker images and run on ECS
- Helpful cost optimizations and focus less on infrastructure

Difference than lambda

- No time limit
- Any runtime as long as Docker image
- Rely on EBS / instance store for disk space
- Relies on EC2 (can be managed by AWS)



#### Lightsail

- Virtual servers, storage, databases, and networking
- Low & predictable pricing
- Simpler alternative to using EC2, RDS, ELB, EBS, Route 53
- Great for people with little cloud experience
- Set up notifications and monitoring of your lightsail resources
- Use cases
  - Simple web apps (LAMP, Nginx, MEAN, Node.js)
  - Websites (WordPress, Magento)
  - Dev / Test environment
- High availability but no auto-scaling, limited AWS integrations





