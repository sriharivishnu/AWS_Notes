## Architecture

**Well Architected Framework General Guiding Principles**

- Stop guessing your capacity needs
- Test systems at production scale
- Automate to make architectural experimentation easier
- Allow for evolutionary architectures
  - Design based on changing requirements
- Drive architectures using data
- Improve through game days
  - Simulate applications for flash sale days



**AWS Cloud Best Practices - Design Principles**

- Scalability
  - Vertical and horizontal
- Disposable Resources
  - servers should be disposable & easily configured
- Automation
  - Serverless, IaaS, Auto Scaling
- Loose Coupling
  - Break it down into smaller loosely coupled components
  - A change or a failure in one component should not cascade to other components
- Services, not servers
  - Don't just use EC2; use managed services



**Well Architected Framework (6 pillars)**

1. Operational Excellence
2. Security
3. Reliability
4. Performance Efficiency
5. Cost Optimization
6. Sustainability

---



**Operational Excellence**

- Includes the ability to run and monitor systems to deliver business value and to continually improve supporting processes and procedures
- Design Principles
  - Perform operations as code - Infra as code
  - Annotate documentation (automate create of documentation after build)
  - Make frequent, small, reversible changes
  - Refine operations procedures frequently
  - Learn and anticipate failures



**Security**

- Includes the ability to protect information, systems, and assets while delivering business value through risk assessments and mitigation strategies
- Design Principles
  - Implement a strong identity foundation
  - Enable traceability
  - Apply security at all layers
  - Automate security best practices
  - Protect data in transit and at rest
  - Keep people away from data
  - Prepare for security events



**Reliability**

- Ability of a system to recover from infrastructure or service disruptions, dynamically acquire computing resources to meet demand, and mitigate disruptions such as misconfigurations or transient network issues
- Design Principles
  - Test recovery procedures
  - Automatically recover from failure
  - Scale horizontally to increase aggregate system availability
  - Stop guessing capacity
  - Manage change in automation



**Performance Efficiency**

- Includes the ability to use computing resources efficiently to meet system requirements, and to maintain that efficiency as demand changes and technologies evolve
- Design Principles
  - Deocratize advanced technologies
  - Go global in minutes
  - Use serverless architectures
  - Experiment more often
  - Mechanical sympathy



**Cost Optimization**

- Includes the ability to run systems to deliver business value at the lowest price point
- Design Principles
  - Adopt a consumption mode
  - Measure overall efficiency
  - Stop spending money on data center operations
  - Analyze and attribute expenditure
  - Use managed and application level services to reduce cost of ownership



**Sustainability**

- Focuses on minimizing the environmental impacts of running cloud workloads
- Design Principles
  - Understand your impact
  - Establish sustainability goals
  - Maximize utilization
  - Anticipate and adopt new, more efficient hardware and software
  - Use managed services
  - Reduce the downstream impact (reduce energy or resources)



**AWS Well-Architected Tool**

- Free tool to review your architectures against the 6 pillars and adopt best practices



**Right Sizing**

- Matching instance types and sizes to your workload performance and capacity requirements at the lowest possible cost
- Scaling up is easy so start small
- Important
  - Before a cloud migration
  - continuously after cloud onboarding process



**Ecosystem**

- Whitepapers, AWS blogs, news, support



**Developer**

- Business hours email access to Cloud Support Associates
- General guidence: < 24 hours
- System impaired: < 12 hours



**Business**

- 24x7 phone, email and chat access to Cloud Support Engineers
- Production system impaired: < 4 hours
- Production system down: < 1 hour



**Enterprise**

- Access to a Technical Account Manager (TAM)
- Concierge Support Team (billing and account best practices)
- Business-critical system down: < 15 minutes



**AWS Professional Services & Partner Network**

- Global team of experts
- Work alongside your team and a chosen member of APN
- Technology Partners
  - Providing hardware, connectivity, and software
- Consulting Partners
  - Professional services firm
- Training Partners
  - Who can help you learn 
- Competency Program
  - Granted APN who have demonstrated technical proficiency and proven customer succcess in specialized solution areas
- Navigate Program
  - Partners become better Partners



**AWS Knowledge Center**

- Contains FAQ and requests



