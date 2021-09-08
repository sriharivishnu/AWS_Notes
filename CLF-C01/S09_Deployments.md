## S09: Deployments at Scale

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

CDK