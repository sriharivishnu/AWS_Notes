## S01: Cloud Computing

Server

- Compute (CPU)
- Memory (RAM)
- Storage Data
- Database (structured data)
- Network (Router, switch, DNS server)



Network

- Cables, routers, and servers connected

Router

- Networking device that forwards data packets between networks
- Knows where to send packets on the internet

Switch

- Takes a packet and sends it to correct server / client



##### Problems with Traditional IT approach

- Pay for rent + power supply, cooling maintenance
- Adding + replacing hardware takes time
- Scaling is limited
- 24/7 team required to monitor infrastructure
- Disasters



##### Cloud Computing

- On-demand delivery of compute power, database storage, applications and other IT resources
- Pay-as-you-go pricing
- Can provision exactly right type and size of computing resources you need
- Access as many resources almost instantly
- Simple way to access servers, storage, databases, and application services
- AWS owns, you provision

So instead of data centres, use the cloud!



##### Deployment Models of the Cloud

Private Cloud

- Cloud services used by a single organization, not exposed to the public
- Complete control
- Security for sensitive applications
- Meets specific business needs



Public Cloud

- Cloud resources owned and operated by a third-party cloud service provider delivered over the Internet
- Six Advantages of Cloud Computing above



Hybrid Cloud

- Keep some servers on premises and some on cloud
- flexibility and cost-effectiveness of cloud
- control over sensitive assets in private infrastructure



##### Five Characteristics of Cloud Computing

1. On-demand self service
   - Users can provision resources and use them without human interaction from the service provider
2. Broad network access
   - Resources available over the network and can be accessed by diverse client platforms
3. Multi-tenancy and resource pooling
   - Multiple customers can share infrastructure and applications securely and privately
   - Multiple customers are services from same physical resources
4. Rapid elasticity and scalability
   - Automatically + quickly acquire and dispose resources
   - Quickly and easily scale 
5. Measure service
   - Usage is measure, users pay for what is used



##### Six Advantages of Cloud Computing

1. Trade capital expense (CAPEX) for operational expense (OPEX)
   - Pay On-Demand (don't own hardware)
   - Reduced Total Cost of Ownership (TCO) & Operational Expense
2. Benefit from massive economies of scale
   - Prices are reduced as AWS is more efficent due to large scale
3. Stop guessing capacity
   - Scale based on actual usage
4. Increase speed and agiility
5. Stop spending money running and maintaining data centers
6. Go global in minutes



**Problems Solved**

- Flexible: change when needed
- Cost-effective: pay as you go
- Scalable: large loads with better hardware + more nodes
- Elasticity: scale out and scale in
- High availablility and fault-tolerance: across data centres
- Agility: rapid development, test, launch



##### Types of Cloud Computing

- Infrastructure as a Service (IaaS)
  - Building blocks for cloud IT
  - Networking, computers, data storage space
  - High flexibility
  - Works with on-premises
  - e.g EC2 (AWS, Azure, Digital Ocean)
- Platform as a Service (PaaS)
  - Removes the need for you organization to manage infrastructure
  - Focus on deployment + management of apps
  - e.g Elastic Beanstalk
- Software as a Service (SaaS)
  - Completed product that is run and managed by the service provider
  - Many AWS services (e.g Rekognition machine learning)

![Screen Shot 2022-03-31 at 1.01.58 AM](/Users/sriharivishnu/Documents/Notes/AWS/CLF-C01/S01_Cloud-images/Screen Shot 2022-03-31 at 1.01.58 AM.png)



##### Pricing

3 Pricing Fundamentals (pay-as-you-go)

1. Compute
   - Compute time
2. Storage
   - Data stored in cloud
3. Data transfer OUT of the cloud
   - (Data transfer in is free)



##### History + Stats

(2002 - Present)

Leader in industry, #35 billion (47% of market in 2019)

1,000,000+ active users

**Use cases**

- Enterprise IT, backup, big data analytics
- Website hosting, mobile backend
- Gaming services



##### AWS Global Infrastructure

- Regions
  - All around the world
  - A cluster of data centers
  - Most services are region-scoped
  - How to choose? Factors
    - Compliance
      - With data governance and legal requirements (data never leaves region without permission)
    - Proximity
      - Reduced Latency
    - Available services
      - New services + features aren't available everywhere
    - Pricing
      - Pricing varies from region to region
  - e.g. us-east-1, eu-west-3
- Availability Zones
  - Each region has many AZs. (usually 3, min 2, max 6)
  - Each AZ is one or more discrete data centers with redundant power, networking and connectivity
  - Separate from each other, so isolated from disasters
  - Connected with high bandwidth, ultra-low latency networking
  - e.g. ap-southeast-2a, ap-southeast-2b, ap-souteast-2c
- Data Centers
- Edge Locations / Points of Presence
  - 216 Points of Presence (205 Edge Locations + 11 Regional Caches) in 84 cities across 42 countries
  - lower latency for end users

Global Resources

- IAM (Identity and Access Management)
- Route 53 (DNS)
- CloudFront (CDN)
- WAF (Web Application Firewall)

Region-Scoped

- ECS 
- Elastic Beanstalk
- Lambda
- Rekognition



##### Shared Responsiblity Model Diagram

![Screen Shot 2022-03-31 at 1.02.48 AM](/Users/sriharivishnu/Documents/Notes/AWS/CLF-C01/S01_Cloud-images/Screen Shot 2022-03-31 at 1.02.48 AM.png)

Customer = Responsibility for the security IN the cloud

AWS = Responsibility for the security OF the cloud



Acceptable Use Policy

- No illegal, harmful, offensive use or content
- NO Security Violations
- No abuse
