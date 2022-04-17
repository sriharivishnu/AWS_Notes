## S18: Other Services

**Amazon Workspaces**

- Managed Desktop as a Service solution to provision Windows or Linux desktops
- Eliminates management of on-premise Virtual Desktop Infrastructure
- Fast and quickly scalable
- Secured data
- Pay-as-you-go service (monthly/hourly rates)

- Multiple Regions
  - Deploy closest to users



**AppStream 2.0**

- Desktop Application Streaming Service
- Deliver to any computer without acquiring, provisioning infrastructure
- Application is delivered from within a web browser
- Differences with Workspaces
  - Workspaces
    - VDI and desktop available
    - Users connect to the VDI and open native or WAM apps
    - Workspaces are on-demand or always on
  - AppStream 2.0
    - Stream desktop app to web browsers (no VDI)
    - Works with any device
    - Can configure instance type per app type (CPU, RAM, GPU)



**Amazon Sumerian**

- Create VR, AR, and 3D apps
- Can be used to create 3D models
- Ready-to-use templates and assets
- Accessible from web browser



**IOT Core**

- Allows connection of IOT devices to the AWS Cloud



**Amazon Elastic Transcoder**

- Used to convert media files stored in S3 into media files in the formats required



**Device Farm**

- Fully-managed service that tests web + mobile apps agains desktop browsers, real mobile devices, and tablets
- Run tests concurrently on multiple devices (speed up execution)
- Ability to configure device settings



**AWS Backup**

- Fully Managed service to centrally manage and automate backups across services
- On-Demand + scheduled backups
- Supports Point-in-time Recovery
- Cross-Region + Cross-Account backup



**Disaster Recovery**

- Cheapest: Backup and Restore
- Pilot Light
  - Minimal setup of cloud 
  - Smaller database + app servers
- Warm Standby
  - Full version of the app, but at minimum size
- Multi-Site / Hot-Site
  - Full version of the app at full size



**AWS Elastic Disaster Recovery**

- Quickly and easily recover your physical, virtual, and cloud-based servers into AWS
- Protect most critical databases
- Continuous block-level replication



**AWS DataSync**

- move large amount of data from on-premises to AWS
- Synchronize to S3, EFS, FSx
- Replication can be hourly, daily, weekly
- Replication tasks are incremental after the first full load



**Fault Injection Simulator**

- Managed service for running fault injection experiments
- Chaos Engineering - stressing and application by creating disruptive events, observing how system responds, implementing improvements
- Helps uncover hidden bugs + performance bottlenecks
- 

