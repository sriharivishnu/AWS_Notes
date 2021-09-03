## S04: EC2 Instance Storage

#### Summary

- **EBS Volumes**
  - network drives attached to one EC2 instance at a time
  - Mapped to an AZ
  - can use EBS snapshots for backups + transferring EBS volumes across AZ
- **AMI**: create ready-to-use EC2 instances with our customizations
- **EC2 Image Builder**: automatically build, test and distribute AMIs
- **EC2 Instance Store**
  - High performance Hardware disk attached to EC2
  - Lost if instance is stopped + terminated
- **EFS**: network file system, can be attached to 100s of instances in a region
- **EFS-IA**: cost-optimized storage class for infrequent accessed files
- **FSx for Windows**: Network File System for Windows Servers
- **FSx for Lustre**: High Performance Computing Linux file system

#### EBS Volume

- EBS (Elastic Block Store) volume is a network drive you can attach to your instances while they run
- Allows instances to persist data, even after their termination
- Can only be mounted to one instance at a time (CCP level) (not true for io1 and io2 volume types though (EBS Multi-Attach))
  - But an instance can have multiple EBS
  - Does not need to attached anywhere
- Bound to a specific AZ
- (like a USB stick)
- Free tier: 30 GB of free EBS storage of General Purpose (SSD) or Magetic per month
- **Network drive (not a physical drive)**
  - Might be a bit of latency
  - Can be detached from an EC2 instance and attached to another one quickly
- **Locked to an AZ**
  - EBS volume in us-east-1a cannot be attached to us-east-1b
  - Move volume across, need to snapshot it
- **Have a provisioned capacity (size in GBs and IOPS)**
  - Get billed for all the provisioned capacity
  - Can increase the capacity of the drive



**Delete on Termination**

- Controls the EBS behaviour when an EC2 instance terminates
- Default
  - deletes root volume
  - any other EBS is not deleted
- Can be controlled by AWS console / AWS CLI
- Use case: preserve root volume when instance is terminated



#### EBS Snapshots

- Make a backup (snapshot) of your EBS volume at a point in time
- Not necessary to detach volume to do snapshot but recommended
- Attached to region but can copy snapshots across AZ or region
- Can create a volume from snapshot



#### AMI Overview

- AMI = Amazon Machine Image
- AMI are a customization of an EC2 instance
  - You add your own software configuration, operating system, monitoring
  - Faster boot / configuration time because all software is pre-packaged
  - Build for a specific region (and can be copied across regions)
- You can launch EC2 instances from:
  - A Public AMI: AWS provided
  - Your own AMI: you make and maintain them yourself
  - An AWS Marketplace AMI: AMI someone else made (potentially sells)
- AMI Process (from EC2 instance)
  - Start an EC2 instance and customize it
  - Stop the instance
  - Build an AMI - this will also create EBS snapshots
  - Launc instances from other AMIs



#### EC2 Image Builder

- Used to automate the creation of Virtual Machines or Container Images
- => Automate the creation, maintain, validate and test EC2 AMIs
- Can be run on a schedule (weekly, whenever packages are updated)
- Free service (only pay for underlying resources e.g. EC2, storage)



#### EC2 Instance Store (Local)

- High-performance hardware disk, use EC2 instance store
- Better I/O performance
- EC2 Instance Store lose their storage if they're stopped (ephemeral (not durable, long-term))
- Good for buffer / cache /scratch data / temporary content
- Risk of data loss if hardware fails
- Backups and replication are your responsibility



#### EFS - Elastic File System

- Managed NFS (network file system) that can be mounted on 100s of EC2 instances
- EFS works with Linux EC2 instances in Multi-AZ
- Highly available, scalable, expensive (3x gp2), pay per use, no capacity planning
- **Infrequent Access**
  - Cost-optimized for files not accessed every day
  - Up to 92% lower cost compared to EFS Standard
  - EFS will automatically move your files to EFS-IA based on the alst time they were accessed
  - Enable EFS-IA with a lifecyle Policy
  - Example: move files that are not accessed for 60 days to EFS-IA
  - Transparent to the applications accessing EFS



#### Shared Responsibility Model for EC2 Storage

- AWS
  - Infrastructure
  - Replication for data for EBS volumes & EFS drives
  - Replacing faulty hardware
  - Ensuring their employees cannot access your data
- You
  - Setting up backup / snapshot procedures
  - Setting up data encryption
  - Responsibility of any data on the drives
  - Understanding the risk of using EC2 Instance Store

#### Amazon FSx

- **Amazon FSx for Windows File Server**
  - Fully managed highly reliable and scalable Windows nativ shared file system
  - Build on Windows File Server
  - Supports SMB protocol & Windows NTFS
  - Integrated with Microsoft Active Directory
  - Can be accessed from AWS or on-premise

- **Amazon FSx for Lustre**
  - Fully managed, high-performance, scalable file storage for High Performance Computing (HPC)
  - Lustre = Linux + Cluster
  - Machine Learning, Analytics, Video Processing, Financial Modeling
  - Scales up to 100s GB/s, millions of IOPS, sub-ms latencies
  - Maybe stores in S3

