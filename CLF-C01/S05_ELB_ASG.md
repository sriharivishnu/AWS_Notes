## S05: Elastic Load Balancing & Auto Scaling Groups

#### Summary

- High Availability vs Scalability (vertical + horizontal) vs Elasticity vs Agility in the cloud
- Elastic Load Balancers (ELB)
  - Distribute traffic across backend EC2 instances (can be Multi AZ)
  - Supports health checks
  - 3 types: Application LB (HTTP/HTTPS-L7), Network LB (TCP - L4), Classic LB (old)
- Auto Scaling Groups (ASG)
  - Implement Elasticity for your application across multiple AZ
  - Scale EC2 instances based on the demand, replace unhealthy
  - Integrated with ELB

#### Scalabiliity and High Availability

- **Scalability**: ability to accommodate a larger load by making the hardware stronger (scale up) or by adding nodes (scale out)
  - Vertical Scalability
    - Increasing/decreasing size of instance
    - Common for non-distributed
    - Usually a limit (hardware limit)
  - Horizontal Scalability (= elasticity)
    - Increase number of instances / systems for application
    - Implies distributed systems
    - Common for web applications / modern applications
    - Auto Scaling Group + Load Balancer
- **Elasticity**: "auto-scaling" so that the system can scale based on the load. Cloud-friendly, pay-per-use, match demand, optimize cost
- **Agility**: (not related to scalability): time to make resources available to developers
- **High Availability**
  - Running application / system in at least 2 AZs
  - ASG multi AZ + Load Balancer multi AZ



#### Elastic Load Balancer

- Servers that forward internet traffic to multiple servers downstream
- Advantages
  - Spread load across multiple instances
  - Sing point of access to application
  - Handle failures of downstream instances
  - Regular health checks
  - SSL termination
  - High availability across zones
- Why use ELB
  - AWS guarantees it will be working, upgrades, maintenance, high availability
  - AWS provides only a few configuration knobs
- Costs less to setup your own, but it's a lot more effort
- 3 kinds of load balancers
  - Application Load Balancer (HTTP / HTTPS only) - Layer 7
    - standard for websites
  - Network Load Balancer (ultra-high performance, allows for TCP) - Layer 4
    - for gaming (lower level)
  - Classic Load Balancer (slowly retiring) - Layer 4 & 7



#### Auto Scaling Group

- Goal
  - Scale out (add EC2 isntances) to match a increased load
  - Scale in (remove EC2 instances) to match a decreased load
  - Ensure we have a minimum and a maximum number of machines running
  - Automatically register new instances to a load balancer
- Cost Saving: Only runs at an optimal capacity
- Minimum Size + Actual Size / Desired + Maximum Size
- Words with Load Balancer
- Scaling Strategies
  - Manual Scaling: Update size of ASG manually
  - Dynamic Scaling: Respond to changing demand
    - Simple / Step Scaling (CloudWatch Alarm is triggered e.g. CPU > 70%)
    - Target Tracking Scaling
      - Want average ASG CPU to stay at around 40%
    - Scheduled Scaling
      - Anticipate a scaling based on known usage patterns
      - e.g. increase the min capacity to 10 on 5 am on friday
    - Predictive Scaling
      - Uses machine learning to predict future traffic ahead of time
