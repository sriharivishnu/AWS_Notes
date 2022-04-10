## S10: AWS Global Infrastructure



##### Summary

- Global DNS: Route 53
  - To route users to the closest deployment
  - Disaster recovery strategies
- Global Content Delivery Network (CDN): CloudFront
  - Replicate part of application to AWS Edge Locations - decrease latency
  - Cache common requests
- S3 Transfer Acceleration
  - Acceleration of uploads and downloads into S3
- AWS Global Accelerator
  - Improve global application availablility and performance using the AWS network
- AWS Outposts
  - Deploy Racks in own data centers to extend AWS services

- AWS WaveLength
  - Use 5G networks to bring services to the edge
  - Ultra-low latency applications

- AWS Local Zones
  - Bring AWS resources close to users
  - latency-sensitive applications




**Background**

- Global application is an application deployed in multiple geographies
- Could be Regions and/or Edge Locations
- Why make a global application?
  - Decreased Latency: Time to access server
  - Disaster Recovery: Earthquakes, Politics etc.
  - Attack protection: distributed infrastructure is harder to attack



**Global AWS Infrastructure**

- Regions
  - For deploying applications and infrastructure
- Availability Zones
  - Made of multiple data centers
- Edge Locations (Points of Presence)
  - Content delivery as close as possible to users



**Route 53**

- Managed DNS (Domain Name System)
  - Collection of rules and records which helps clients understand how to reach a server
  - A Record: host to IPV4
  - AAAA Record: host to IPV6
  - CNAME: Hostname to hostname
  - Alias: Hostname to AWS resource
- Routing Policies
  - Simple Routing Policy
    - No Health Checks
  - Weighted Routing Policy
    - Distribute the traffic across multiple EC2 instances
    - Can assign weights to each EC2 instance
  - Latency Routing Policy
    - Make users connect to the server that is closest to them
  - Failover Routing Policy
    - Disaster Recover; connect to failover if primary has failed



**AWS CloudFront**

- Content Delivery Network (CDN)
- Improves read performance, content is cached at the edge
- 216 Point of Presence (edge locations)
- DDoS protection (worldwide), integration with Shield, AWS Web Application Firewall
- **Origins**
  - S3 Bucket
    - Distributing files and caching them
    - Enhanced security with CloudFront Origin Access Identity (OAI)
    - CF can be used as ingress to upload files
  - Custom Origin (HTTP)
    - Application Load balancer, EC2 Instance, S3 website

![Screen Shot 2022-04-01 at 3.15.48 AM](/Users/sriharivishnu/Documents/Notes/AWS/CLF-C01/S10_Global_Scale-images/Screen Shot 2022-04-01 at 3.15.48 AM.png)



**S3 Transfer Acceleration**

- Increase transfer speed by transferring to edge location, which forwards data to the S3 bucket in target region



**AWS Global Accelerator**

- Improve global application availability and performance using the AWS global network
- Optimize route to your application (~60% improvement)
- 2 Static Anycast IP are created for your application and traffic is sent through Edge Locations

<img src="/Users/sriharivishnu/Documents/Notes/AWS/CLF-C01/S10_Global_Scale-images/Screen Shot 2022-04-01 at 3.34.05 AM.png" alt="Screen Shot 2022-04-01 at 3.34.05 AM" style="zoom:30%;" />

![Screen Shot 2022-04-01 at 3.35.09 AM](/Users/sriharivishnu/Documents/Notes/AWS/CLF-C01/S10_Global_Scale-images/Screen Shot 2022-04-01 at 3.35.09 AM.png)



**AWS Outposts**

- **Hybrid Cloud**
  - Keeps an on-premises infrastructure alongside a cloud infrastructure
- Two ways of dealing IT systems
  - One for AWS cloud, and one for on-premises infra
- AWS Outposts
  - Server racks that offers the same AWS infra, services, APIs & tools to build applications on-premises just like cloud
  - AWS will setup and manage
- You are responsible for the physical security of the Outposts rack
- Benefits
  - Low-latency access to on-premises systems
  - Local data processing
  - Data residency
  - Easier migration from on-premises to the lcoud
  - Fully managed
  - Services: EC2, EBS, S3, EKS, ECS, RDS, EMR



**AWS WaveLength**

- Infrastructure deployments embedded within the telecommunications providers' datacetners
- Brings AWS services to the edge of 5G networks
- Ex. EC2, EBS, VPC
- Low latency through 5G networks
- No additional charges
- Smart Cities, AR/VR, Real-time gaming



**AWS Local Zones**

- Places AWS compute, storage, database and other selected AWS services closer to end users to run latency-sensitive applications
- Compatible with:
  - EC2, RDS, ECS, EBS...
- Ex: 
  - Region: N. Virginia (us-east-1)
  - Local Zones: Boston, Chicago, Dallas...



**Applications Architecture**

- Single Region, Single AZ
- Single Region, Multi AZ
  - High Availability
- Multi Region, Active Passive
  - 2 regions, each regions has 1+ AZ
  - 1 region - application is active
  - Other region is passive (only reads), and replicate data
  - Read latency 
- Multi Region, Active-Active
  - Each EC2 instance has reads, and write capabilities
  - Read Latency and Write latency are good
- 
