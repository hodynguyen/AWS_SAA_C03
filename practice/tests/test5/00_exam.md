# Practice Test 5

## Instructions
- Time: 130 minutes
- Questions: 65
- Passing score: 72%

---

## Question 1
What is the default encryption configuration when logging is enabled in AWS CloudTrail?

A. SSE-C  
B. SSE-S3  
C. SSE-KMS  
D. No encryption by default

---

## Question 2
A company has infrequently accessed data that needs to be available immediately upon request.

Which S3 storage class is most cost-effective?

A. S3 Standard-IA  
B. S3 Glacier  
C. S3 One Zone-IA  
D. S3 Standard

---

## Question 3
A company needs to inspect and filter traffic entering and leaving its VPC.

Which AWS service provides this capability?

A. AWS Shield  
B. AWS WAF  
C. AWS Network Firewall  
D. Security Groups

---

## Question 4
A company needs to run serverless ETL jobs to transform data from multiple sources into a data lake.

Which service is most suitable?

A. AWS Glue  
B. AWS Lambda  
C. Amazon EMR  
D. AWS Batch

---

## Question 5
A hybrid architecture needs to provide on-premises applications with low-latency access to frequently accessed data stored in AWS.

Which Storage Gateway mode is most appropriate?

A. Stored Volumes  
B. File Gateway  
C. Tape Gateway  
D. Cached Volumes

---

## Question 6
An SQS consumer application polls for messages but often receives empty responses.

How can costs be optimized while maintaining performance?

A. Increase visibility timeout  
B. Use FIFO queues  
C. Decrease message size  
D. Enable long polling

---

## Question 7
An IAM policy allows all S3 actions, but a condition restricts access to requests from IP 192.168.1.0/24. A user tries to access S3 from IP 10.0.0.5.

What is the result?

A. Access is allowed  
B. Access depends on bucket policy  
C. Access is denied  
D. An error occurs

---

## Question 8
A developer takes an EBS snapshot while the volume is in use.

What happens to the data?

A. The snapshot includes all data written up to when the snapshot was initiated  
B. The snapshot fails  
C. The snapshot only includes data from before the volume was attached  
D. The volume is temporarily paused

---

## Question 9
A company wants to build a serverless GraphQL API with real-time data synchronization.

Which service should be used?

A. Amazon API Gateway  
B. AWS AppSync  
C. AWS Lambda  
D. Amazon EventBridge

---

## Question 10
An Auto Scaling group needs to add more capacity based on different levels of CPU utilization.

Which scaling policy should be used?

A. Simple scaling  
B. Target tracking  
C. Scheduled scaling  
D. Step scaling

---

## Question 11
A web application will receive over 2000 PUT and 3500 GET requests per second to S3 at peak hour.

What should be done to ensure optimal performance?

A. Use predictable naming with sequential numbers or dates  
B. Do nothing. S3 automatically manages performance at this scale  
C. Use Byte-Range Fetches for multiple ranges per GET request  
D. Add random prefix to key names

---

## Question 12
A company needs a dedicated private connection from VPC to on-premises with high bandwidth and consistent network experience.

Which service should be used?

A. AWS Direct Connect  
B. AWS Site-to-Site VPN  
C. Transit Gateway with ECMP  
D. Transit VPC

---

## Question 13
An Auto Scaling group is scaling up and down multiple times per hour.

What design change optimizes cost while preserving elasticity?

A. Upgrade instance type in launch template  
B. Add provisioned IOPS to instances  
C. Increase base number of Auto Scaling instances  
D. Change cooldown period and set CloudWatch metric to higher threshold

---

## Question 14
A Docker-based batch application processes both mission-critical and non-essential jobs.

What is the most cost-effective implementation?

A. ECS with Reserved EC2 for both workloads  
B. ECS with Spot EC2 for both workloads  
C. ECS with Reserved EC2 for mission-critical, Spot for non-essential  
D. ECS with On-Demand EC2 for both workloads

---

## Question 15
Windows-based applications require scalable file storage for HPC with SMB protocol, NTFS, Active Directory integration, and DFS support.

Which storage service is most suitable?

A. Amazon FSx for Lustre  
B. Amazon FSx for Windows File Server  
C. Amazon S3 Glacier Deep Archive  
D. AWS DataSync

---

## Question 16
A company has UAT and production EC2 instances. Employees responsible for UAT should not access production instances.

What is the best way to achieve this?

A. Launch in different AZs and use MFA  
B. Use AWS RAM to provide permissions  
C. Define tags on servers and add IAM policy condition for specific tags  
D. Launch in separate VPCs with VPC peering

---

## Question 17
An EC2 application uses AWS SDK to communicate with AWS services. All API calls must be logged and durably stored for IT audit.

Which service is most suitable?

A. Amazon CloudWatch  
B. Amazon API Gateway  
C. AWS CloudTrail  
D. AWS X-Ray

---

## Question 18
1000 Linux servers in multiple AZs need simultaneous access to storage using NFSv4.

Which is the most cost-effective service?

A. Amazon FSx for Windows File Server  
B. Amazon EFS  
C. Amazon S3  
D. Amazon EBS

---

## Question 19
Multiple applications need secure access to RDS MySQL. Each IAM user must use short-lived authentication tokens.

Which solution is most suitable?

A. Use IAM DB Authentication with AWSAuthenticationPlugin  
B. Use AWS Secrets Manager for short-lived tokens  
C. Use AWS IAM Identity Center to access RDS  
D. Use MFA token to connect to database

---

## Question 20
EC2 instances in private subnet process sensitive data and deliver to S3. The data should not pass through public Internet.

How should this be designed?

A. Create Internet gateway in public subnet with route to S3  
B. Configure Transit Gateway with route to S3  
C. Provision NAT gateway in private subnet with route to S3  
D. Configure VPC Endpoint with route to S3

---

## Question 21
EC2 in private subnet accesses financial data in S3 via pre-signed URLs. Security team is concerned about Internet connectivity to S3.

What is the most cost-effective solution?

A. Access S3 through Interface VPC Endpoint (PrivateLink)  
B. Access S3 through VPN connection  
C. Access S3 through Gateway VPC Endpoint  
D. Create custom VPC endpoint service

---

## Question 22
NACL allows all inbound, denies all outbound. Security group allows inbound SSH from any IP, no outbound rules.

What changes are needed to allow SSH connection?

A. Modify outbound security group to allow outbound traffic  
B. No action needed  
C. Modify both outbound security group and NACL  
D. Modify NACL to allow outbound traffic

---

## Question 23
A microservices application needs efficient read/write from multiple DynamoDB tables without impacting baseline performance.

Which is the most operationally efficient solution?

A. Use AWS AppSync pipeline resolvers  
B. Use CloudFront functions  
C. Set up DynamoDB connector for Athena Federated Query  
D. Use Lambda with edge-optimized API Gateway

---

## Question 24
A company migrates an on-premises app to AWS with zero downtime. They want to divert 50% traffic to AWS, 50% to on-premises.

Which solutions work? (Select TWO.)

A. Route 53 with Weighted routing policy  
B. Route 53 with Failover routing policy  
C. ALB with Weighted Target Groups  
D. NLB with Weighted Target Groups  
E. AWS Global Accelerator with Direct Connect Gateway

---

## Question 25
A CloudHSM was zeroized after 3 failed admin login attempts. No backup copy of keys exists.

How can you obtain a new copy of the keys?

A. Contact AWS Support for a copy  
B. Restore a snapshot of the HSM  
C. Keys are permanently lost without a copy  
D. Use Amazon CLI to get a copy

---

## Question 26
Microservices send messages to SQS; backend EC2 processes them. The company has an SLA for response time, but I/O-intensive operations and growing messages cause missed SLAs.

Which solution improves processing time?

A. ASG with target tracking on CPUUtilization at 80%  
B. Launch EC2 to cluster placement group  
C. Replace with larger instance size  
D. ASG with target tracking on ApproximateAgeOfOldestMessage

---

## Question 27
EC2 instances in two custom VPCs (Ohio and N.Virginia) need to transfer data without traversing the public Internet.

Which combination achieves this? (Select TWO.)

A. Deploy VPC endpoint in each region  
B. Re-configure route table target and destination  
C. Launch NAT Gateway in public subnet of each VPC  
D. Create Egress-only Internet Gateway  
E. Set up VPC peering connection

---

## Question 28
Customer PII was mistakenly uploaded to S3. The company wants to detect sensitive data and be notified if it happens again.

Which combination should be implemented? (Select TWO.)

A. Set up SQS as EventBridge target  
B. Use Amazon Macie with EventBridge rule for SensitiveData events  
C. Use AWS IoT Message Broker as EventBridge target  
D. Set up SNS topic as EventBridge target  
E. Use GuardDuty with EventBridge for CRITICAL events

---

## Question 29
A Windows-based HPC cluster on t3a.medium EC2 instances needs higher bandwidth, higher PPS, and lower inter-instance latencies.

Which is the most suitable and cost-effective solution?

A. Enable Enhanced Networking with EFA on Windows instances  
B. Use AWS ParallelCluster  
C. Enable Enhanced Networking with Intel 82599 VF interface  
D. Enable Enhanced Networking with ENA on Windows instances

---

## Question 30
EC2 instances with Systems Manager need configuration without RDP or SSH connections.

What can be used?

A. AWS CodePipeline  
B. Run Command  
C. AWS Config  
D. EC2Config

---

## Question 31
A heterogeneous database migration from on-premises Oracle to AWS PostgreSQL requires schema and code transformation.

Which is the most suitable approach?

A. Use Amazon Neptune then AWS Batch for migration  
B. Use Launch Template for conversion then DMS  
C. Heterogeneous migrations not supported in AWS  
D. Use AWS Schema Conversion Tool then AWS DMS

---

## Question 32
EC2 instances in private subnet access S3 via NAT Instance. How to reduce costs most effectively?

A. Use smaller instance type for NAT  
B. Replace NAT instance with NAT Gateway  
C. Remove NAT instance and use S3 Gateway endpoint  
D. Remove NAT instance and use S3 Interface endpoint

---

## Question 33
Multiple Site-to-Site VPN connections have slow connectivity during peak hours.

How to scale VPN throughput?

A. Increase number of tunnels per VPN  
B. Add secondary customer gateway device  
C. Associate VPCs to ECMP-enabled Transit Gateway with additional VPN tunnels  
D. Add more virtual private gateways to VPC with ECMP

---

## Question 34
Route 53 is used instead of ELB to distribute traffic. You want specific percentage of traffic to each of two EC2 instances.

Which routing policy should be used?

A. Latency  
B. Failover  
C. Geolocation  
D. Weighted

---

## Question 35
EC2 in private subnet fetches from S3 via NAT Gateway. How to reduce costs without risking availability?

A. Remove NAT Gateway and use Gateway VPC endpoint  
B. Replace NAT Gateway with NAT instance on burstable type  
C. Re-assign NAT Gateway to lower EC2 type  
D. Deploy Transit Gateway for S3 peering

---

## Question 36
A research institute has simulation software requiring significant compute power (32 vCPUs, 256 GiB). They want to run simulations in parallel on AWS.

Which solution has LEAST operational overhead?

A. Use EC2 Spot Instances  
B. Use Lambda functions  
C. Use AWS Fargate  
D. Use AWS Batch

---

## Question 37
A company wants to store data in S3 but keep frequently accessed data locally on-premises without extending local storage.

What is the best solution?

A. Use Amazon Glacier  
B. Use EC2 with EBS volumes  
C. Use ElastiCache and S3  
D. Use AWS Storage Gateway - Cached Volumes

---

## Question 38
Multiple departments deploy resources to AWS. The company wants to track service quota usage to avoid unexpected limits.

Which combination should be implemented? (Select TWO.)

A. EventBridge with SNS topic as notification target  
B. Query Trusted Advisor every 24 hours with Developer support plan  
C. Create SNS topic as target for notifications  
D. Use AWS Config managed rule with Lambda  
E. Lambda function to refresh Trusted Advisor Service Limits every 24 hours

---

## Question 39
ALB with two target groups. Port 80 is allowed in security group, but instances show "out of service."

What could be the root cause?

A. Wrong subnet was used  
B. Wrong AMI was used  
C. Health check configuration is not properly defined  
D. Wrong instance type was used

---

## Question 40
An AI medical app needs single-digit millisecond latency on 5G edge with EKS and RBAC for IAM authentication.

Which solution should be implemented?

A. EKS on Fargate with Wavelength node groups and Fargate execution role  
B. EKS with Wavelength node groups and aws-auth ConfigMap  
C. EKS with Wavelength node groups, EKS connector agent, and Control Tower  
D. EKS with VPC CNI in Wavelength and aws-iam-authenticator

---

## Question 41
10 TB of infrequently accessed financial data for audits. Retrieval can take up to 24 hours.

Which is the most cost-effective solution?

A. S3 with lifecycle to S3 One Zone-IA  
B. S3 with lifecycle to Glacier after 0 days  
C. S3 with lifecycle to S3-IA  
D. Amazon FSx for Windows with SMB

---

## Question 42
Web application on EC2 fleet behind ALB in two AZs. Need to add health check configuration.

Which health checks should be implemented?

A. HTTP or HTTPS health check  
B. TCP health check  
C. ICMP health check  
D. FTP health check

---

## Question 43
EC2 with encrypted EBS volumes.

Which statements are true about encrypted EBS? (Select TWO.)

A. Snapshots from encrypted volumes are not encrypted  
B. Snapshots are automatically encrypted  
C. Only data at rest is encrypted, not data in transit  
D. All data moving between volume and instance are encrypted  
E. Snapshots are not automatically encrypted

---

## Question 44
A single Aurora instance is used for a trading platform. What happens during failover with no replicas?

A. Aurora flips A record to healthy replica  
B. Aurora creates new instance in same AZ on best-effort basis  
C. Aurora flips CNAME to healthy replica  
D. Aurora creates new instance in different AZ first

---

## Question 45
Kinesis Data Streams processes stock data. Where can consumers store results? (Select TWO.)

A. Amazon Athena  
B. Amazon S3  
C. Amazon EMR  
D. AWS Glue  
E. Amazon Redshift

---

## Question 46
SQS queue is used for batch processing. What prevents other consumers from receiving a message being processed?

A. Visibility Timeout  
B. Component Timeout  
C. Processing Timeout  
D. Receiving Timeout

---

## Question 47
SNS fanout to SQS queues. EC2 Spot instance terminated while processing. What happens to the message?

A. Message deleted and duplicated when instance comes online  
B. Message sent to Dead Letter Queue in DataSync  
C. Message assigned to same instance when it comes back  
D. Message becomes available for other instances after visibility timeout expires

---

## Question 48
Dedicated physical server (no virtualization) needs NFS storage with cloud backup to S3.

Which is the most suitable solution?

A. Storage Gateway VM appliance with File Gateway  
B. Storage Gateway hardware appliance with File Gateway and S3 backup  
C. Storage Gateway hardware appliance with Volume Gateway and S3 backup  
D. Storage Gateway hardware appliance with Volume Gateway

---

## Question 49
Web application behind ALB needs geo-blocking but should allow specific IPs from blocked country.

Which combination should be implemented? (Select TWO.)

A. Create ALB listener rule for approved IPs  
B. Create WAF web ACL with IP Set rule for approved IPs  
C. Use Transit Gateway with NACLs for geo-blocking  
D. Set up geo match in ALB  
E. Add WAF rule with geo match to block specific country

---

## Question 50
Wearable device sends 1 MB/day to S3. Processing needs 512 MB memory and must complete in 10 seconds.

Which is the most cost-effective solution?

A. Lambda with Python library  
B. AWS Glue PySpark job  
C. Redshift with Lambda processing  
D. Firehose to S3, then EC2 processing

---

## Question 51
Web servers behind ALB with Route 53. How to configure zone apex to point to ALB?

A. Create CNAME record pointing to ALB DNS name  
B. Create alias for CNAME record to ALB  
C. Create A record pointing to ALB IP address  
D. Create A record aliased to ALB DNS name

---

## Question 52
Multi-region application must block a specific country per government policy.

Which is the recommended action?

A. Update NACLs on EC2 subnets to deny country IPs  
B. Create WAF web ACL with geo match to block country. Associate with ALBs  
C. Update NACLs on ALB subnets to deny country IPs  
D. Use Network Firewall with domain list rule to block country

---

## Question 53
EBS volumes must be encrypted for HIPAA compliance.

What does AWS use to secure EBS data at rest? (Select TWO.)

A. S3 Server-Side Encryption  
B. Your own keys in KMS  
C. Amazon-managed keys in KMS  
D. SSL certificates from ACM  
E. Password in CloudHSM  
F. S3 Client-Side Encryption

---

## Question 54
EC2 instances under SSH brute force attack. IP addresses identified. Need quickest fix while setting up WAF/GuardDuty/Shield.

Which provides the quickest way to stop attacks?

A. Place instances in private subnets  
B. Assign static Anycast IP addresses  
C. Block IP addresses in Network ACL  
D. Remove Internet Gateway from VPC

---

## Question 55
Web application needs NoSQL database with no storage limit, fully managed and scalable.

Which is the most suitable service?

A. SimpleDB  
B. DynamoDB  
C. Amazon Aurora  
D. Amazon Neptune

---

## Question 56
.NET Windows EC2 app needs shared file system with high throughput/IOPS and Active Directory integration.

Which is the most suitable service?

A. Amazon FSx for Windows File Server  
B. AWS Storage Gateway - File Gateway  
C. Amazon EBS Provisioned IOPS SSD  
D. Amazon EFS

---

## Question 57
ALB needs HTTP request logging including client IP and latencies. ECS Anywhere apps need troubleshooting.

Which solution has LEAST overhead?

A. Enable CloudTrail for ALB. Use CloudTrail Lake for analysis  
B. Enable ALB access logs. Use CloudWatch Application Insights for ECS  
C. Use EventBridge metrics for client IP. Use CloudWatch GetMetricData  
D. Run X-Ray daemon on ECS. Use CloudWatch ServiceLens

---

## Question 58
Consolidate access, application, and security logs for real-time analysis. Need to validate heuristics from last 12 hours.

Which is the best approach?

A. Send logs to SQS, use EC2 ASG to apply heuristics  
B. Configure CloudTrail for custom logs, use EMR for heuristics  
C. Send logs to Kinesis, develop client to apply heuristics  
D. Use EC2 ASG with S3 storage, use EMR for heuristics

---

## Question 59
EKS e-commerce app has holiday traffic surges. Need auto-scaling with LEAST operational overhead. (Select TWO.)

A. Metrics Server + Horizontal Pod Autoscaler  
B. Metrics Server + Vertical Pod Autoscaler  
C. CloudWatch Alarms for scaling  
D. Cluster Autoscaler  
E. Karpenter for node scaling

---

## Question 60
Startup with on-premises AD and 10 computers needs virtual desktops in VPC connected to on-premises.

Which AWS services should be used?

A. Directory Services, VPN, S3  
B. Directory Services, VPN, WorkSpaces  
C. Directory Services, VPN, IAM  
D. Directory Services, VPN, ClassicLink

---

## Question 61
Healthcare company needs to migrate on-premises patient records to AWS. Records must be WORM, audited at all levels.

Which is the most suitable solution?

A. DataSync to S3, CloudTrail Data Events, S3 Object Lock  
B. Storage Gateway to S3, CloudTrail Management Events, S3 Object Lock  
C. DataSync to S3, CloudTrail Management Events, S3 Object Lock  
D. Storage Gateway to EBS, server access logging, Object Lock

---

## Question 62
ASG app has morning traffic bursts with timeouts. EC2 takes 1 minute to boot.

How should the architecture be redesigned?

A. Create step scaling with instance warm-up time  
B. Create NLB with slow-start mode  
C. Create CloudFront with EC2 origin  
D. Create new launch template with larger instance

---

## Question 63
ASG terminates instances on health check failure, losing ephemeral logs. Need to collect logs before termination.

What is the EASIEST automation approach?

A. Lifecycle hook to Terminating:Wait, CloudWatch Events with Lambda, Systems Manager Run Command  
B. Lifecycle hook to Terminating:Wait, Step Functions, CloudWatch Logs  
C. Lifecycle hook to Pending:Wait, CloudWatch Events with Lambda, Systems Manager Automation  
D. Lifecycle hook to Terminating:Wait, CloudWatch Events with Lambda, trigger CloudWatch agent

---

## Question 64
Batch job processes SQS messages weekly. After 2 weeks, not all messages are processed.

What is the root cause?

A. Long polling configured  
B. Missing SQS permissions  
C. Messages exceeded retention period (auto-deleted)  
D. Short polling configured

---

## Question 65
50 TB OLTP database migration. Must be ACID-compliant, handle complex queries, and scale to grow.

Which database service should be used?

A. Amazon Redshift  
B. Amazon DynamoDB  
C. Amazon RDS  
D. Amazon Aurora
