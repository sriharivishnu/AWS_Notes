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
  - Iimplement a strong identity foundation
  - Enable traceability
  - Apply security at all layers
  - Automate security best practices
  - Protect data in transit and at rest
  - Keep people away from data
  - Prepare for security events

