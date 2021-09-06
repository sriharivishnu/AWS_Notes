## S07: Databases

#### Summary

- **Relational Databases - OLTP**: RDS + Aurora (SQL)
- Differences between Multi-AZ, Read Replicas, Multi-Region
- **ElastiCache**: In-memory Database
- **DynamoDB** (serverless) & **DAX** (cache for DynamoDB): Key/Value Database + cache
- **Redshift**: Warehouse - OLAP (SQL)
- **EMR**: Hadoop Cluster
- **Athena**: query data on Amazon S3 (serverless + SQL)
- **Quicksight**: dashboards on your data (serverless)
- **DocumentDB**: "Aurora for MongoDB" (JSON - NoSQL database)
- **Amazon QLDB**: Financial Transactions Ledger (immutable journal, cryptographically verifiable)
- **Amazon Managed Blockchain**: managed HyperLedger Fabric & Ethereum blockchains
- **Glue**: Managed ETL (Extract Transform Load) and Data Catalog service
- **DMS**: Database Migration
- **Neptune**: Graph database





- Storing data on disk has its limits
- Storing data in database
  - Structure the data
  - Build indexes to efficiently query
  - Define relationships between datasets



Relational Databases

- Define relationships, structure data, use SQL to query

NoSQL

- non relational databases
- Flexible, Scalable (distributed clusters), High-performance, highly functional
- e.g. Key-value, document, graph, in-memory, JSON



Shared Responsiblity

- AWS
  - Quick Provisioning, High availability, Vertical and Horizontal Scaling
  - Automated Backup & Restore, Operations, Upgrades
  - Operating System Patching handled by AWS
  - Monitoring, alerting
- Could run on EC2, but must handle resiliency, backup, patching, high availability, fault tolerance, scaling



#### AWS RDS

- RDS - Relational Database Service
- Managed DB service for DB use SQL as query language
- Create databases in the cloud that are managed by AWS
  - Postgres
  - MySQL
  - MariaDB
  - Aurora (AWS Proprietary database)
- Advantages of RDS over DB on EC2
  - RDS is managed
    - Automated provisioning, OS patching
    - Continuous backups and restore to specific timestamp
    - Monitoring dashboards
    - Read replicas for improved read performance
    - Multi AZ setup DR
    - Maintenance windows for upgrades
    - Scaling capability (vertical and horizontal)
    - Storage backed by EBS (gp2 or io1)
- Cannot SSH into instance



RDS Solution Architecture

- load balancer -> EC2 instances <-> database



Amazon Aurora

- Proprietary technology from AWS (not open-source)
- PostgreSQL and MySQL are both supported as Aurora DB
- Aurora is AWS cloud optimized
  - 5x improvement over MySQL on RDS, 3x postgres on RDS
- Storage grows in increments of 10 GB up to 64 TB
- Aurora costs more than RDS (20% more) but is more efficient
- Not in the free tier :(



#### RDS Deployment Options

- Read Replicas
  - Scale the read workload of your DB
  - Can create up to 5 read replicas
  - Data is only written to the main DB
- Multi-AZ
  - Failover in case of AZ outage (high availability)
  - Can only have 1 other AZ as failover
- Multi-Region
  - Multi-Region (Read Replicas, single writable)
  - Disaster recovery in case of region issue
  - Local performance for global reads
  - Replication cost



#### Amazon ElastiCache

- Get managed Redis or Memcached
- In-memory databases with high performance, low latency
- Helps reduce load off databases for read intensive workloads
- AWS takes care of OS maintenance / patching, optimizations, setup, configuration, monitoring, failure recovery and backups

- Architecture
  - ELB -> EC2 -> either RDS (slow) or ElastiCache (fast)



#### DynamoDB

- Fully Managed Highly available with replication across 3 AZ
- NoSQL database - not a relational database
- Scales to massive workloads, distributed "serverless" database
- Millions of requests per seconds, trillions of rows, 100s of TB of storage
- Fast and consisten in performance
- Single-digit millisecond latency - low latency retrieval
- Integrated with IAM for security, authorization, and administration
- Low cost and auto scaling capabilities

Key-value database

- Primary Key

  - Partition Key
  - Sort Key

- Attributes

  - Schema defined per item

  ![Screen Shot 2021-09-05 at 10.58.22 PM](/Users/sriharivishnu/Library/Application Support/typora-user-images/Screen Shot 2021-09-05 at 10.58.22 PM.png)



DynamoDB Accelerator - DAX

- Fully Managed in-memory cache for DynamoDB
- 10x performance improvement - single-digit millisecond latency to microseconds latency 
- Secure, highly scalable & highly available
- DAX is only used for and is integrated with DynamoDB (while ElastiCache can be used for other databases)



#### Redshift

- Based on PostgreSQL, but not used for OLTP
- It's OLAP - online analytical processing (analytics and data warehousing)
- Load data once every hour, not every second
- 10x better performance than other data warehouses, scale to PBs of data
- **Columnar** storage of data (instead of rows!)
- Massively Parallel Query Execution (MPP), highly available
- Pay as you go based on the instances provisioned
- Has a SQL interface for performing the queries
- BI tools such as AWS Quicksight or tablet integrate with it



#### Amazon EMR

- Elastic MapReduce
- EMR helps creating Hadoop clusters (Big Data) to analyze and process vast amount of data
- The clusters can be made of hundreds of EC2 instances
- Supports Apache Spark, HBase, Presto
- EMR takes care of all provisioning and configuration
- Auto-scaling and integrated with Spot instances
- Use cases: data processing, machine learning, web indexing, big data



#### Amazon Athena

- Fully Serverless database with SQL capabilities
- Used to query data in S3
- Pay per query
- Output results back to S3
- Secured through IAM
- Use Case: on-time SQL queries, serverless queries on S3, log analytics



#### Amazon QuickSight

- Serverless machine learning-powered BI service to create interactive dashboards
- Fast, automatically scalable, embeddable, per-session pricing
- Use cases:
  - Business Analytics
  - Building visualizations
  - Ad-hoc analysis
- Integrated with: RDS, Aurora, Athena, Redshift, S3



#### DocumentDB

- AWS-implementation of MongoDB (NoSQL)
- Used to store, query and index JSON data
- Similar deployment concepts as Aurora
- Fully Managed, highly available with replication across 3 AZ
- Like Aurora, storage automatically grows in increments of 10GB, up to 64 TB
- Automatically scales to workloads with millions of requests per second



#### Neptune

- Fully managed graph database
  - e.g. social network
    - Users ahve friends
    - Posts have comments
    - Comments have likes from users
    - Users share and like posts
- Highly available across 3 AZ, with up to 15 read replicas
- Build and run applications working with highly connected datasets = optimized for complex and hard queries
- Store up to billions of relations and query the graph will millisecond latency
- Great for knowledge graphs (Wikipedia), fraud detection, recommendation engines, social networking



#### QLDB

- Quantum Ledger Database
- Ledger is a book recording financial transations
- Fully managed, Serverless, High Available, Replication across 3 AZ
- Used to review history of all the changes made to your application data over time
- Immutable system: no entry can be removed or modified, cryptographically verifiable
- 2-3x better performance for than common ledger blockchain frameworks
- manipulate data using SQL
- No decentralization component (Managed Blockchain has decentralization component)



#### Amazon Managed Blockchain

- Blockchain makes it possible to build applications where multiple parties can execute transactions without the need for a trusted, central authority
- Managed Service
  - Join public blockchain networks
  - Create own scalable private network
- Compatible with Hyperledger Fabric & Ethereum



#### DMS - Database Migration Service

Source DB -> EC2 instance Running DMS -> Target DB

- Quickly and securely migrate databases to AWS, resilient, self healing
- Source database remains available
- Homogeneous migrations + Heterogeneous migrations (diff dbs)



#### AWS Glue

- Managed extract, transform, load (ETL) service
- Useful to prepare and transform data for analytics
- Fully serverless service
- e.g. take data from S3, RDS -> Glue (Transform) -> load to Redshift
- Glue Data Catalog
  - Catalog of datasets in AWS infrastructure
  - Columns, field types
  - Can be used by Athena, Redshift, EMR to build proper schemas for them

