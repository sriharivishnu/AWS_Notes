## S13: VPC

##### Summary

- Virtual Private Cloud
- Subnets
  - Tied to an AZ, network partition of VPC
- Internet Gateway
  - VPC Level, provides Internet access for public subnets
- NAT Gateway / Instances
  - Give internet access to private subnets
- NACL
  - Stateless, subnet rules for inbound and outbound
- Security Groups
  - Stateful, operate at the EC2 instance level or ENI
- VPC Peering
  - Connect two VPC with non overlapping IP ranges, nontransitive
- VPC Endpoints
  - Provide private access to AWS services within VPC
- VPC Flow Logs
  - network traffic logs
- Site to Site VPN
  - VPN over public internet between on-premises DC and AWS
- Direct Connect
  - Direct private connection to AWS
- Transit Gateway
  - Connect thousands of VPC and on-premises networks together



**VPC (Virtual Private Cloud)**

- Private network to deploy your resources (regional resource)
- **Subnets** 
  - allow you to partition your network inside your VPC (AZ resource)
  - Public is a subnet that is accessible from the internet
  - Private is a subnet that is not accessible from the internet
- To define access to the internet and between subnets, we use Route Tables

<img src="S13_VPC-images/Screen Shot 2022-04-09 at 5.44.31 PM.png" alt="Screen Shot 2022-04-09 at 5.44.31 PM" style="zoom:50%;" />



**Internet Gateway**

- Helps VPC instances connect with the internet
- Public subnets have a route to the internet gateway



**NAT Gateway**

- NAT Gateway (AWS-managed)
- NAT Instances (self-managed)
- Allow instances in private subnets to access the internet while remaining private



**Network ACL & Security Groups**

- NACL (Network ACL)
  - A firewall which controls traffic from and to subnet
  - Can have ALLOW and DENY rules
  - Are attached at the Subnet level
  - Rules only include IP addresses
- Security Groups
  - A firewall that controls traffic to and from ENI/EC2
  - Can have allow rules
  - Rules can include IP Addresses and other security groups

<img src="S13_VPC-images/Screen Shot 2022-04-09 at 5.57.58 PM.png" alt="Screen Shot 2022-04-09 at 5.57.58 PM" style="zoom:50%;" />



**VPC Flow Logs**

- Capture information about IP traffic going into interfaces
  - VPC Flow Logs
  - Subnet Flow Logs
  - Elastic Network Interface Flow logs
- Helps monitor & troubleshoot connectivity issues
  - Subnets to internet
  - Subnets to subnets
  - Internet to subnets
- Captures network information from AWS managed interfaces too
- Can export to S3 or CW Logs



**VPC Peering**

- Connect two VPC privately using AWS' network
- Behaves as if they were in the same network
- MUST not have overlapping CIDR (IP address range)
- Peering connection is NOT transitive 



**VPC Endpoints**

- Endpoints allow you to connect to AWS Services using a private network instead of public www network
- Enhanced security and lower latency to access AWS services
- VPC Endpoint Gateway
  - For S3 and Dynamo DB only!
- VPC Endpoint Interface
  - For all other services

<img src="S13_VPC-images/Screen Shot 2022-04-09 at 7.22.57 PM.png" alt="Screen Shot 2022-04-09 at 7.22.57 PM" style="zoom:50%;" />



**Site to Site VPN & Direct Connect**

- Site to Site VPN
  - Connect on-premises VPN to AWS
    - On-Premises: Must use a Customer Gateway (CGW)
    - AWS: Must use a Virtual Private Gateway (VGW)
  - Connection is encrypted
  - Uses public internet
  - Very quick to set up, but limited bandwidth, takes 5 min

<img src="S13_VPC-images/Screen Shot 2022-04-09 at 7.28.53 PM.png" alt="Screen Shot 2022-04-09 at 7.28.53 PM" style="zoom:50%;" />



- Direct Connect (DX)
  - Establish a physical connection between on-premises and AWS
  - Connection is private, secure and fast
  - Goese over private network
  - More expensive to set up, takes a month to establish

<img src="S13_VPC-images/Screen Shot 2022-04-09 at 7.30.41 PM.png" alt="Screen Shot 2022-04-09 at 7.30.41 PM" style="zoom:50%;" />



**Transit Gateway**

- For transitive peering between thousands of VPC and on-premises, hub-and-spoke (star) connection

<img src="S13_VPC-images/Screen Shot 2022-04-09 at 7.32.55 PM.png" alt="Screen Shot 2022-04-09 at 7.32.55 PM" style="zoom:30%;" />

- One single Gateway to provide this functionality
- Works with Direct Connect Gateway, VPN connections



