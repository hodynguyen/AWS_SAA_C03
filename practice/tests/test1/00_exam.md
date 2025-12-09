# AWS SAA-C03 Practice Test 1

**Total Questions:** 65
**Time Limit:** 130 minutes

---

# Question 1

A cryptocurrency trading platform is using an API built in AWS Lambda and API Gateway. Due to the recent news and rumors about the upcoming price surge of Bitcoin, Ethereum and other cryptocurrencies, it is expected that the trading platform would have a significant increase in site visitors and new users in the coming days ahead.

In this scenario, how can you protect the backend systems of the platform from traffic spikes?

## Options

A. Use CloudFront in front of the API Gateway to act as a cache.

B. Switch from using AWS Lambda and API Gateway to a more scalable and highly available architecture using EC2 instances, ELB, and Auto Scaling.

C. Move the Lambda function in a VPC.

D. Enable throttling limits and result caching in API Gateway.


---

# Question 2

A company is using AWS Fargate to run a batch job whenever an object is uploaded to an Amazon S3 bucket. The minimum ECS task count is initially set to 1 to save on costs and should only be increased based on new objects uploaded to the S3 bucket.

Which is the most suitable option to implement with the LEAST amount of effort?

## Options

A. Set up an Amazon EventBridge (Amazon CloudWatch Events) rule to detect S3 object PUT operations and set the target to a Lambda function that will run the StartTask API command.

B. Set up an alarm in CloudWatch to monitor S3 object-level operations recorded on CloudTrail. Set two alarm actions to update the ECS task count to scale-out/scale-in depending on the S3 event.

C. Set up an Amazon EventBridge (Amazon CloudWatch Events) rule to detect S3 object PUT operations and set the target to the ECS cluster to run a new ECS task.

D. Set up an alarm in Amazon CloudWatch to monitor S3 object-level operations that are recorded on CloudTrail. Create an Amazon EventBridge (Amazon CloudWatch Events) rule that triggers the ECS cluster when new CloudTrail events are detected.


---

# Question 3

A popular social network is hosted in AWS and is using a Amazon DynamoDB table as its database. There is a requirement to implement a 'follow' feature where users can subscribe to certain updates made by a particular user and be notified via email.

Which of the following is the most suitable solution to implement to meet the requirement?

## Options

A. Enable DynamoDB Stream and create an AWS Lambda trigger, as well as the IAM role which contains all of the permissions that the Lambda function will need at runtime. The data from the stream record will be processed by the Lambda function which will then publish a message to Amazon SNS Topic that will notify the subscribers via email.

B. Set up a DAX cluster to access the source DynamoDB table. Create a new DynamoDB trigger and an AWS Lambda function. For every update made in the user data, the trigger will send data to the Lambda function which will then notify the subscribers via email using Amazon SNS.

C. Using the Amazon Kinesis Client Library (KCL), write an application that leverages on DynamoDB Streams Kinesis Adapter that will fetch data from the DynamoDB Streams endpoint. When there are updates made by a particular user, notify the subscribers via email using Amazon SNS.

D. Create an AWS Lambda function that uses DynamoDB Streams Amazon Kinesis Adapter which will fetch data from the DynamoDB Streams endpoint. Set up an Amazon SNS Topic that will notify the subscribers via email when there is an update made by a particular user.


---

# Question 4

An online shopping platform is hosted on an Auto Scaling group of Amazon EC2 Spot instances and utilizes Amazon Aurora PostgreSQL as its database. It is required to optimize database workloads in the cluster by directing the production traffic to high-capacity instances and routing the reporting queries from the internal staff to the low-capacity instances.

Which is the most suitable configuration for the application as well as the Aurora database cluster to achieve this requirement?

## Options

A. Do nothing since by default, Aurora will automatically direct the production traffic to your high-capacity instances and the reporting queries to your low-capacity instances.

B. In your application, use the instance endpoint of your Aurora database to handle the incoming production traffic and use the cluster endpoint to handle reporting queries.

C. Configure your application to use the reader endpoint for both production traffic and reporting queries, which will enable your Aurora database to automatically perform load-balancing among all the Aurora Replicas.

D. Create a custom endpoint in Aurora based on the specified criteria for the production traffic and another custom endpoint to handle the reporting queries.


---

# Question 5

A company plans to host a web application in an Auto Scaling group of Amazon EC2 instances. The application will be used globally by users to upload and store several types of files. Based on user trends, files that are older than 2 years must be stored in a different storage class. The Solutions Architect of the company needs to create a cost-effective and scalable solution to store the old files yet still provide durability and high availability.

Which of the following approach can be used to fulfill this requirement? (Select TWO.)

## Options

A. Use a RAID 0 storage configuration that stripes multiple Amazon EBS volumes together to store the files. Configure the Amazon Data Lifecycle Manager (DLM) to schedule snapshots of the volumes after 2 years.

B. Use Amazon EBS volumes to store the files. Configure the Amazon Data Lifecycle Manager (DLM) to schedule snapshots of the volumes after 2 years.

C. Use Amazon S3 and create a lifecycle policy that will move the objects to S3 Standard-IA after 2 years.

D. Use Amazon S3 and create a lifecycle policy that will move the objects to S3 Glacier after 2 years.

E. Use Amazon EFS and create a lifecycle policy that will move the objects to EFS-IA after 2 years.


---

# Question 6

An organization requires a persistent block storage volume to support its mission-critical workloads. The backup data will be stored in an object storage service and, after 30 days, transitioned to an archival storage service for long-term retention.

What should be done to meet the above requirement?

## Options

A. Attach an instance store volume in your Amazon EC2 instance. Use Amazon S3 to store your backup data and configure a lifecycle policy to transition your objects to S3 One Zone-IA.

B. Attach an Amazon EBS volume in your Amazon EC2 instance. Use Amazon S3 to store your backup data and configure a lifecycle policy to transition your objects to S3 Glacier Flexible Retrieval.

C. Attach an instance store volume in your existing Amazon EC2 instance. Use Amazon S3 to store your backup data and configure a lifecycle policy to transition your objects to S3 Glacier Flexible Retrieval.

D. Attach an Amazon EBS volume in your Amazon EC2 instance. Use Amazon S3 to store your backup data and configure a lifecycle policy to transition your objects to S3 One Zone-IA.


---

# Question 7

A Solutions Architect is designing a highly available relational database solution to mitigate the risk of a multi-region failure. The database must meet a Recovery Point Objective (RPO) of 1 second and a Recovery Time Objective (RTO) of less than 1 minute. The architect needs a disaster recovery plan that enables automatic cross-region replication with minimal data loss and rapid recovery in the event of a failure.

Which AWS feature best fulfills this requirement?

## Options

A. Amazon Aurora Global Database

B. Amazon DynamoDB Global table

C. Amazon Timestream for Analytics

D. Amazon RDS for PostgreSQL with cross-region read replicas


---

# Question 8

A Solutions Architect is hosting a website in an Amazon S3 bucket named tutorialsdojo. The users load the website using the following URL: http://tutorialsdojo.s3-website-us-east-1.amazonaws.com. A new requirement has been introduced to add JavaScript on the webpages to make authenticated HTTP GET requests against the same bucket using the S3 API endpoint (tutorialsdojo.s3.amazonaws.com). However, upon testing, the web browser blocks JavaScript from allowing those requests.

Which of the following options is the MOST suitable solution to implement for this scenario?

## Options

A. Enable Cross-Region Replication (CRR).

B. Enable Cross-origin resource sharing (CORS) configuration in the bucket.

C. Enable Cross-Zone Load Balancing.

D. Enable cross-account access.


---

# Question 9

A Solutions Architect identified a series of DDoS attacks while monitoring the Amazon VPC. The Architect needs to fortify the current cloud infrastructure to protect the data of the clients.

Which of the following is the most suitable solution to mitigate these kinds of attacks?

## Options

A. Set up a web application firewall using AWS WAF to filter, monitor, and block HTTP traffic.

B. Using the AWS Firewall Manager, set up a security layer that will prevent SYN floods, UDP reflection attacks, and other DDoS attacks.

C. Use AWS Shield Advanced to detect and mitigate DDoS attacks.

D. A combination of Security Groups and Network Access Control Lists to only allow authorized traffic to access your VPC.


---

# Question 10

A company is experiencing repeated outages in the Availability Zone where its Amazon RDS database instance is deployed, resulting in a complete loss of access to the database during each incident.

Which solution should be implemented to prevent losing database access if this occurs again?

## Options

A. Enable Multi-AZ failover

B. Create a read replica

C. Make a snapshot of the database

D. Increase the database instance size


---

# Question 11

A software development company is using serverless computing with AWS Lambda to build and run applications without having to set up or manage servers. The company has a Lambda function that connects to a MongoDB Atlas, which is a popular Database as a Service (DBaaS) platform, and also uses a third-party API to fetch certain data for its application. One of the developers was instructed to create the environment variables for the MongoDB database hostname, username, and password, as well as the API credentials that will be used by the Lambda function for DEV, SIT, UAT, and PROD environments.

Considering that the Lambda function is storing sensitive database and API credentials, how can this information be secured to prevent other developers on the team, or anyone, from seeing these credentials in plain text? Select the best option that provides maximum security.

## Options

A. There is no need to do anything because, by default, Lambda already encrypts the environment variables using the AWS Key Management Service.

B. Lambda does not provide encryption for the environment variables. Deploy your code to an Amazon EC2 instance instead.

C. Create a new AWS KMS key and use it to enable encryption helpers that leverage on AWS Key Management Service to store and encrypt the sensitive information.

D. Enable SSL encryption that leverages on AWS CloudHSM to store and encrypt the sensitive information.


---

# Question 12

An application consists of multiple Amazon EC2 instances in private subnets in different availability zones. The application uses a single NAT Gateway for downloading software patches from the Internet to the instances. There is a requirement to protect the application from a single point of failure when the NAT Gateway encounters a failure or if its availability zone goes down.

How should the Solutions Architect redesign the architecture to be more highly available and cost-effective?

## Options

A. Create two NAT Gateways in each availability zone. Configure the route table in each public subnet to ensure that instances use the NAT Gateway in the same availability zone.

B. Create a NAT Gateway in each availability zone. Configure the route table in each public subnet to ensure that instances use the NAT Gateway in the same availability zone.

C. Create three NAT Gateways in each availability zone. Configure the route table in each private subnet to ensure that instances use the NAT Gateway in the same availability zone.

D. Create a NAT Gateway in each availability zone. Configure the route table in each private subnet to ensure that instances use the NAT Gateway in the same availability zone.


---

# Question 13

A government agency plans to store confidential tax documents on AWS. Due to the sensitive information in the files, the Solutions Architect must restrict the data access requests made to the storage solution to a specific Amazon VPC only. The solution should also prevent the files from being deleted or overwritten to meet the regulatory requirement of having a write-once-read-many (WORM) storage model.

Which combination of the following options should the Architect implement? (Select TWO.)

## Options

A. Enable Object Lock but disable Object Versioning on the new Amazon S3 bucket to comply with the write-once-read-many (WORM) storage model requirement.

B. Create a new Amazon S3 bucket with the S3 Object Lock feature enabled. Store the documents in the bucket and set the Legal Hold option for object retention.

C. Store the tax documents in the Amazon S3 Glacier Instant Retrieval storage class. Use the PutBucketPolicy API to apply a bucket policy that restricts access requests to a specific VPC.

D. Configure an Amazon S3 Access Point for the S3 bucket to restrict data access to a particular VPC only.

E. Set up a new Amazon S3 bucket to store the tax documents and integrate it with AWS Network Firewall. Configure the Network Firewall to only accept data access requests from a specific VPC.


---

# Question 14

A company has a highly available architecture consisting of an Elastic Load Balancer and multiple Amazon EC2 instances configured with Auto Scaling across three Availability Zones. The company needs to monitor EC2 instances based on a specific metric that is not readily available in Amazon CloudWatch.

Which of the following is a custom metric in CloudWatch that requires manual setup?

## Options

A. CPU Utilization of an EC2 instance

B. Disk Read activity of an EC2 instance

C. Memory Utilization of an EC2 instance

D. Network packets out of an EC2 instance


---

# Question 15

A company wishes to query data that resides in multiple AWS accounts from a central data lake. Each account has its own Amazon S3 bucket that stores data unique to its business function. Access to the data lake must be granted based on user roles.

Which solution will minimize overhead and costs while meeting the required access patterns?

## Options

A. Use AWS Control Tower to centrally manage each account's S3 buckets.

B. Use AWS Lake Formation to consolidate data from multiple accounts into a single account.

C. Use Amazon Data Firehose to consolidate data from multiple accounts into a single account.

D. Create a scheduled AWS Lambda function using Amazon EventBridge for transferring data from multiple accounts to the S3 buckets of the central account.


---

# Question 16

A financial services company plans to migrate its trading application from on-premises Microsoft Windows Server to Amazon Web Services (AWS). The solution must ensure high availability across multiple Availability Zones and offer low-latency access to block storage.

Which of the following solutions will fulfill these requirements?

## Options

A. Configure the trading application on Amazon EC2 Windows instances across two Availability Zones. Use Amazon Simple Storage Service (Amazon S3) for storage and configure cross-region replication to sync data between S3 buckets in each Availability Zone.

B. Deploy the trading application on Amazon EC2 Windows Server instances across two Availability Zones. Use Amazon FSx for Windows File Server for shared storage.

C. Configure the trading application on Amazon EC2 Windows Server instances across two Availability Zones. Use Amazon FSx for NetApp ONTAP to create a Multi-AZ file system and access the data via iSCSI protocol.

D. Deploy the trading application on Amazon EC2 Windows Server instances across two Availability Zones. Use Amazon Elastic File System (Amazon EFS) to provide shared storage between the instances. Configure Amazon EFS with cross-region replication to sync data across Availability Zones.


---

# Question 17

A company plans to launch an Amazon EC2 instance in a private subnet for its internal corporate web portal. For security purposes, the EC2 instance must send data to Amazon DynamoDB and Amazon S3 via private endpoints that don't pass through the public Internet.

Which of the following can meet the above requirements?

## Options

A. Use AWS VPN CloudHub to route all access to S3 and DynamoDB via private endpoints.

B. Enable DynamoDB Encryption at Rest with the default AWS-managed key and S3 Server-Side Encryption with the default AWS KMS key to route all traffic to DynamoDB and S3 via private endpoints.

C. Use AWS Direct Connect to route all access to S3 and DynamoDB via private endpoints.

D. Use a DynamoDB VPC endpoint and an S3 VPC endpoint to route all access to these services via private endpoints.


---

# Question 18

A pharmaceutical company has resources hosted on both its on-premises network and in the AWS cloud. The company requires all Software Architects to access resources in both environments using on-premises credentials, which are stored in Active Directory.

In this scenario, which of the following can be used to fulfill this requirement?

## Options

A. Set up SAML 2.0-Based Federation by using a Microsoft Active Directory Federation Service.

B. Use IAM users

C. Use Amazon VPC

D. Set up SAML 2.0-Based Federation by using a Web Identity Federation.


---

# Question 19

An e-commerce company utilizes a regional Amazon API Gateway to host its public REST APIs. The API Gateway endpoint is accessed through a custom domain name set up with an Amazon Route 53 alias record. To support continuous improvement, the company intends to launch a new version of its APIs with enhanced features and performance optimizations.

How can the company reduce customer disruption and ensure MINIMAL data loss during the update process in the MOST cost-effective way?

## Options

A. Implement a canary release deployment strategy for the API Gateway. Deploy the latest version of the APIs to a canary stage and direct a portion of the user traffic to this stage. Verify the new APIs. Gradually increase the traffic percentage, monitor for any issues, and, if successful, promote the canary stage to production.

B. Implement a blue-green deployment strategy for the API Gateway, deploying the latest version of the APIs to the green environment. Route some user traffic to it, validate the new APIs, and once thoroughly validated, promote the green environment to production.

C. Create a new API Gateway with the updated version of the APIs in OpenAPI JSON or YAML file format, but keep the same custom domain name for the new API Gateway.

D. Modify the existing API Gateway with the updated version of the APIs, but keep the same custom domain name for the new API Gateway by using the import-to-update operation in either overwrite or merge mode.


---

# Question 20

An e-commerce company runs a highly scalable web application that depends on an Amazon Aurora database. As the number of users increases, the read replica faces difficulties keeping up with the increasing read traffic, causing performance bottlenecks during peak periods.

Which of the following will resolve the issue with the most cost-effective solution?

## Options

A. Increase the size of the Aurora DB cluster.

B. Implement read scaling with Aurora Global Database.

C. Set up a read replica that can operate across different regions.

D. Use automatic scaling for the Aurora read replica using Aurora Auto Scaling.


---

# Question 21

A telecommunications company is planning to grant AWS Console access to its developers. Company policy requires the use of identity federation and role-based access control. Currently, the roles are already assigned via groups in the corporate Active Directory.

In this scenario, what combination of the following services can provide developers access to the AWS console? (Select TWO.)

## Options

A. IAM Groups

B. AWS Directory Service Simple AD

C. AWS Directory Service AD Connector

D. AWS Lambda

E. IAM Roles


---

# Question 22

A payment processing company plans to migrate its on-premises application to an Amazon EC2 instance. An IPv6 CIDR block is attached to the company's Amazon VPC. Strict security policy mandates that the production VPC must only allow outbound communication over IPv6 between the instance and the internet but should prevent the internet from initiating an inbound IPv6 connection. The new architecture should also allow traffic flow inspection and traffic filtering.

What should a solutions architect do to meet these requirements?

## Options

A. Launch the EC2 instance to a private subnet and attach a NAT Gateway to the VPC to allow outbound IPv6 communication to the internet. Use AWS Firewall Manager to set up the required rules for traffic inspection and traffic filtering.

B. Launch the EC2 instance to a private subnet and attach AWS PrivateLink interface endpoint to the VPC to control outbound IPv6 communication to the internet. Use Amazon GuardDuty to set up the required rules for traffic inspection and traffic filtering.

C. Launch the EC2 instance to a private subnet and attach an Egress-Only Internet Gateway to the VPC to allow outbound IPv6 communication to the internet. Use AWS Network Firewall to set up the required rules for traffic inspection and traffic filtering.

D. Launch the EC2 instance to a public subnet and attach an Internet Gateway to the VPC to allow outbound IPv6 communication to the internet. Use Traffic Mirroring to set up the required rules for traffic inspection and traffic filtering.


---

# Question 23

A company has a web application that uses Internet Information Services (IIS) for Windows Server. A file share is used to store the application data on the network-attached storage of the company's on-premises data center. To achieve a highly available system, the company plans to migrate the application and file share to AWS.

Which of the following can be used to fulfill this requirement?

## Options

A. Migrate the existing file share configuration to Amazon EBS.

B. Migrate the existing file share configuration to Amazon EFS.

C. Migrate the existing file share configuration to AWS Storage Gateway.

D. Migrate the existing file share configuration to Amazon FSx for Windows File Server.


---

# Question 24

A global IT company with offices around the world has multiple AWS accounts. To improve efficiency and drive costs down, the Chief Information Officer (CIO) wants to set up a solution that centrally manages their AWS resources. This will allow them to procure AWS resources centrally and share resources such as AWS Transit Gateways, AWS License Manager configurations, or Amazon Route 53 Resolver rules across their various accounts.

As the Solutions Architect, which combination of options should you implement in this scenario? (Select TWO.)

## Options

A. Consolidate all of the company's accounts using AWS ParallelCluster.

B. Consolidate all of the company's accounts using AWS Organizations.

C. Use the AWS Resource Access Manager (RAM) service to easily and securely share your resources with your AWS accounts.

D. Use the AWS Identity and Access Management service to set up cross-account access that will easily and securely share your resources with your AWS accounts.

E. Use AWS Control Tower to easily and securely share your resources with your AWS accounts.


---

# Question 25

A travel photo-sharing website is using Amazon S3 to serve high-quality photos to visitors. After a few days, it was discovered that other travel websites are linking to and using these photos. This has resulted in financial losses for the business.

What is the MOST effective method to mitigate this issue?

## Options

A. Store and privately serve the high-quality photos on Amazon WorkDocs instead.

B. Configure your S3 bucket to remove public read access and use pre-signed URLs with expiry dates.

C. Block the IP addresses of the offending websites using NACL.

D. Use Amazon CloudFront distributions for your photos.


---

# Question 26

A company hosted an e-commerce website on an Auto Scaling group of Amazon EC2 instances behind an Application Load Balancer. The Solutions Architect noticed that the website is receiving a high number of illegitimate external requests from multiple systems with frequently changing IP addresses. To address the performance issues, the Solutions Architect must implement a solution that would block these requests while having minimal impact on legitimate traffic.

Which of the following options fulfills this requirement?

## Options

A. Create a rate-based rule in AWS WAF and associate the web ACL to an Application Load Balancer.

B. Create a custom rule in the security group of the Application Load Balancer to block the offending requests.

C. Create a regular rule in AWS WAF and associate the web ACL to an Application Load Balancer.

D. Create a custom network ACL and associate it with the subnet of the Application Load Balancer to block the offending requests.


---

# Question 27

An online cryptocurrency exchange platform is hosted in AWS, utilizing an Amazon ECS Cluster and Amazon RDS in a Multi-AZ Deployments configuration. The application heavily uses the RDS instance to process complex read and write database operations. To maintain reliability, availability, and performance, it is necessary to closely monitor how the different processes or threads on a DB instance use the CPU, including the percentage of CPU bandwidth and total memory consumed by each process.

Which of the following is the most suitable solution to monitor the database properly?

## Options

A. Create a script that collects and publishes custom metrics to Amazon CloudWatch, which tracks the real-time CPU Utilization of the RDS instance, and then set up a custom CloudWatch dashboard to view the metrics.

B. Use Amazon CloudWatch to monitor the CPU Utilization of your database.

C. Check the CPU% and MEM% metrics which are readily available in the RDS console that shows the percentage of the CPU bandwidth and total memory consumed by each database process of your RDS instance.

D. Enable Enhanced Monitoring in RDS.


---

# Question 28

A suite of web applications is hosted in an Auto Scaling group of Amazon EC2 instances across three Availability Zones and is configured with default settings. There is an Application Load Balancer that forwards the request to the respective target group on the URL path. The scale-in policy has been triggered due to the low number of incoming traffic to the application.

Which EC2 instance will be the first one to be terminated by the Auto Scaling group?

## Options

A. The EC2 instance which has been running for the longest time

B. The EC2 instance which has the least number of user sessions

C. The instance will be randomly selected by the Auto Scaling group

D. The EC2 instance launched from the oldest launch template.


---

# Question 29

A newly hired Solutions Architect is assigned to manage a set of CloudFormation templates that are used in the company's cloud architecture in AWS. The Architect accessed the templates and tried to analyze the configured IAM policy for an S3 bucket.

```json
{ 
 "Version": "2012-10-17", 
 "Statement": [ 
  { 
   "Effect": "Allow", 
   "Action": [ 
    "s3:Get*", 
    "s3:List*" 
   ], 
   "Resource": "*" 
  }, 
  { 
   "Effect": "Allow", 
   "Action": "s3:PutObject", 
   "Resource": "arn:aws:s3:::boracay/*" 
  } 
 ] 
}
```

What does the above IAM policy allow? (Select THREE.)

## Options

A. An IAM user with this IAM policy is allowed to read objects from all S3 buckets owned by the account.

B. An IAM user with this IAM policy is allowed to read objects in the boracay S3 bucket but not allowed to list the objects in the bucket.

C. An IAM user with this IAM policy is allowed to change access rights for the boracay S3 bucket.

D. An IAM user with this IAM policy is allowed to write objects into the boracay S3 bucket.

E. An IAM user with this IAM policy is allowed to read objects from the boracay S3 bucket.

F. An IAM user with this IAM policy is allowed to read and delete objects from the boracay S3 bucket.


---

# Question 30

A government entity is conducting a population and housing census in the city. Each household information uploaded on their online portal is stored in encrypted files in Amazon S3. The government assigned its Solutions Architect to set compliance policies that verify data containing personally identifiable information (PII) in a manner that meets their compliance standards. They should also be alerted if there are potential policy violations with the privacy of their S3 buckets.

Which of the following should the Architect implement to satisfy this requirement?

## Options

A. Set up and configure Amazon Fraud Detector to send out alert notifications whenever a security violation is detected on their Amazon S3 data.

B. Set up and configure Amazon Kendra to monitor malicious activity on their Amazon S3 data

C. Set up and configure Amazon Polly to scan for usage patterns on Amazon S3 data

D. Set up and configure Amazon Macie to monitor their Amazon S3 data.


---

# Question 31

An AI-powered Forex trading application consumes thousands of data sets to train its machine learning model. The application's workload requires a high-performance, parallel hot storage to process the training datasets concurrently. It also needs cost-effective cold storage to archive those datasets that yield low profit.

Which of the following Amazon storage services should the developer use?

## Options

A. Use Amazon FSx For Lustre and Amazon S3 for hot and cold storage respectively.

B. Use Amazon Elastic File System and Amazon S3 for hot and cold storage respectively.

C. Use Amazon FSx For Windows File Server and Amazon S3 for hot and cold storage respectively.

D. Use Amazon FSx For Lustre and the Provisioned IOPS SSD (io1) volumes of Amazon EBS for hot and cold storage respectively.


---

# Question 32

There was an incident in a production environment where user data stored in an Amazon S3 bucket was accidentally deleted by a Junior DevOps Engineer. The issue was escalated to management, and after a few days, an instruction was given to improve the security and protection of AWS resources.

What combination of the following options will protect the S3 objects in the bucket from both accidental deletion and overwriting? (Select TWO.)

## Options

A. Enable S3 Intelligent-Tiering

B. Disallow S3 Delete using an IAM bucket policy

C. Enable Multi-Factor Authentication Delete

D. Provide access to S3 data strictly through pre-signed URL only

E. Enable Versioning


---

# Question 33

A medical records company is planning to store sensitive clinical trial data in an Amazon S3 repository with the object-level versioning feature enabled. The Solutions Architect is tasked with ensuring that no object can be overwritten or deleted by any user in a period of one year only. To meet the strict compliance requirements, the root user of the company's AWS account must also be restricted from making any changes to an object in the S3 bucket.

Which of the following is the most secure way of storing the data in S3?

## Options

A. Enable S3 Object Lock in compliance mode with a legal hold of one year.

B. Enable S3 Object Lock in governance mode with a retention period of one year.

C. Enable S3 Object Lock in compliance mode with a retention period of one year.

D. Enable S3 Object Lock in governance mode with a legal hold of one year.


---

# Question 34

A business has recently migrated its applications to AWS. The audit team must be able to assess whether the services the company is using meet common security and regulatory standards. A solutions architect needs to provide the team with a report of all compliance-related documents for their account.

Which action should a solutions architect consider?

## Options

A. Run an Amazon Inspector assessment job to download all of the AWS compliance-related information.

B. View all of the AWS security compliance reports from AWS Security Hub.

C. Use AWS Artifact to view the security reports as well as other AWS compliance-related information.

D. Run an Amazon Macie job to view the Service Organization Control (SOC), Payment Card Industry (PCI), and other compliance reports from AWS Certificate Manager (ACM).


---

# Question 35

A Solutions Architect needs to make sure that the On-Demand Amazon EC2 instance can only be accessed from this IP address (110.238.98.71) via an SSH connection.

Which configuration below will satisfy this requirement?

## Options

A. Security Group Outbound Rule: Protocol – TCP, Port Range – 22, Destination 110.238.98.71/32

B. Security Group Outbound Rule: Protocol – UDP, Port Range – 22, Destination 0.0.0.0/0

C. Security Group Inbound Rule: Protocol – TCP. Port Range – 22, Source 110.238.98.71/32

D. Security Group Inbound Rule: Protocol – UDP, Port Range – 22, Source 110.238.98.71/32


---

# Question 36

An online learning company hosts its Microsoft .NET e-Learning application on a Windows Server in its on-premises data center. The application uses an Oracle Database Standard Edition as its backend database.

The company wants a high-performing solution to migrate this workload to the AWS cloud to take advantage of the cloud's high availability. The migration process should minimize development changes, and the environment should be easier to manage.

Which of the following options should be implemented to meet the company requirements? (Select TWO.)

## Options

A. Refactor the application to .NET Core and run it as a serverless container service using Amazon Elastic Kubernetes Service (Amazon EKS) with AWS Fargate.

B. Rehost the on-premises .NET application to an AWS Elastic Beanstalk Multi-AZ environment which runs in multiple Availability Zones.

C. Provision and replatform the application to Amazon Elastic Container Service (Amazon ECS) with Amazon EC2 worker nodes.

D. Perform a homogeneous migration by moving the Oracle database to Amazon RDS for Oracle in a Multi-AZ deployment using AWS Database Migration Service (AWS DMS).

E. Use AWS Application Migration Service (AWS MGN) to migrate the on-premises Oracle database server to a new Amazon EC2 instance.


---

# Question 37

A company has a web application that uses Amazon CloudFront to distribute its images, videos, and other static content stored in its Amazon S3 bucket to users around the world. The company has recently introduced a new member-only access feature for some of its high-quality media files. There is a requirement to provide access to multiple private media files only to paying subscribers without having to change the current URLs.

Which of the following is the most suitable solution to implement to satisfy this requirement?

## Options

A. Create a Signed URL with a custom policy which only allows the members to see the private files.

B. Configure your CloudFront distribution to use Match Viewer as its Origin Protocol Policy.

C. Use Signed Cookies to control who can access the private files in your CloudFront distribution by modifying your application to determine whether a user should have access to your content.

D. Configure your CloudFront distribution to use Field-Level Encryption to protect your private data and only allow access to members.


---

# Question 38

A tech company has a CRM application hosted on an Auto Scaling group of On-Demand EC2 instances with different instance types and sizes. The application is extensively used during office hours from 9 in the morning to 5 in the afternoon. Their users are complaining that the performance of the application is slow during the start of the day but then works normally after a couple of hours.

Which of the following is the MOST operationally efficient solution to implement to ensure the application works properly at the beginning of the day?

## Options

A. Configure a Predictive scaling policy for the Auto Scaling group to automatically adjust the number of Amazon EC2 instances

B. Configure a Dynamic scaling policy for the Auto Scaling group to launch new instances based on the CPU utilization.

C. Configure a Dynamic scaling policy for the Auto Scaling group to launch new instances based on the Memory utilization.

D. Configure a Scheduled scaling policy for the Auto Scaling group to launch new instances before the start of the day.


---

# Question 39

A company hosted a web application in an Auto Scaling group of EC2 instances. The IT manager is concerned about the over-provisioning of the resources that can cause higher operating costs. A Solutions Architect has been instructed to create a cost-effective solution without affecting the performance of the application.

Which dynamic scaling policy should be used to satisfy this requirement?

## Options

A. Use suspend and resume scaling.

B. Use target tracking scaling.

C. Use scheduled scaling.

D. Use simple scaling.


---

# Question 40

A company uses an Application Load Balancer (ALB) for its public-facing multi-tier web applications. The security team has recently reported that there has been a surge of SQL injection attacks lately, which causes critical data discrepancy issues. The same issue is also encountered by its other web applications in other AWS accounts that are behind an ALB. An immediate solution is required to prevent the remote injection of unauthorized SQL queries and protect their applications hosted across multiple accounts.

As a Solutions Architect, what solution would you recommend?

## Options

A. Use AWS WAF and set up a managed rule to block request patterns associated with the exploitation of SQL databases, like SQL injection attacks. Associate it with the Application Load Balancer. Integrate AWS WAF with AWS Firewall Manager to reuse the rules across all the AWS accounts.

B. Use Amazon GuardDuty and set up a managed rule to block request patterns associated with the exploitation of SQL databases.

C. Use Amazon Macie to scan for vulnerabilities and unintended network exposure.

D. Use AWS Network Firewall to filter web vulnerabilities and brute force attacks using stateful rule groups.


---

# Question 41

A company has a cloud architecture composed of Linux and Windows Amazon EC2 instances that process high volumes of financial data 24 hours a day, 7 days a week. To ensure high availability of the systems, the Solutions Architect must create a solution that enables monitoring of memory and disk utilization metrics for all instances.

Which of the following is the most suitable monitoring solution to implement?

## Options

A. Use the default Amazon CloudWatch configuration to EC2 instances where the memory and disk utilization metrics are already available.

B. Enable the Enhanced Monitoring option in EC2 and install Amazon CloudWatch agent to all the EC2 instances.

C. Use Amazon Inspector and install the Inspector agent to all EC2 instances.

D. Install the Amazon CloudWatch agent to all the EC2 instances that gather the memory and disk utilization data. View the custom metrics in the CloudWatch console.


---

# Question 42

A company is in the process of migrating their applications to AWS. One of their systems requires a database that can scale globally and handle frequent schema changes. The application should not have any downtime or performance issues whenever there is a schema change in the database. It should also provide a low latency response to high-traffic queries.

Which is the most suitable database solution to use to achieve this requirement?

## Options

A. An Amazon Aurora database with Read Replicas

B. Redshift

C. An Amazon RDS instance in Multi-AZ Deployments configuration

D. Amazon DynamoDB


---

# Question 43

A tech company that you are working for has undertaken a Total Cost Of Ownership (TCO) analysis evaluating the use of Amazon S3 versus acquiring more storage hardware. The result was that all 1200 employees would be granted access to use Amazon S3 for the storage of their personal documents.

Which of the following will you need to consider so you can set up a solution that incorporates a single sign-on feature from your corporate AD or LDAP directory and also restricts access for each individual user to a designated user folder in an S3 bucket? (Select TWO.)

## Options

A. Set up a matching IAM user for each of the 1200 users in your corporate directory.

B. Set up a Federation proxy or an Identity provider, and use AWS Security Token Service to generate temporary tokens.

C. Configure an IAM role and an IAM Policy to access the bucket.

D. Use 3rd party Single Sign-On solutions such as Atlassian Crowd, OKTA, OneLogin.

E. Map each individual user to a designated user folder in S3 using Amazon WorkDocs.


---

# Question 44

A startup is using Amazon RDS to store data from a web application. Most of the time, the application has low user activity but it receives bursts of traffic within seconds whenever there is a new product announcement. The Solutions Architect needs to create a solution that will allow users around the globe to access the data using an API.

What should the Solutions Architect do meet the above requirement?

## Options

A. Create an API using Amazon API Gateway and use Amazon Elastic Beanstalk with Auto Scaling to handle the bursts of traffic in seconds.

B. Create an API using Amazon API Gateway and use the Amazon ECS cluster with Service Auto Scaling to handle the bursts of traffic in seconds.

C. Create an API using Amazon API Gateway and use an Auto Scaling group of Amazon EC2 instances to handle the bursts of traffic in seconds.

D. Create an API using Amazon API Gateway and use AWS Lambda to handle the bursts of traffic in seconds.


---

# Question 45

An application that records weather data every minute is deployed in a fleet of Amazon EC2 Spot instances and uses a MySQL RDS database instance. Currently, there is only one Amazon RDS instance running in one Availability Zone. The database needs to be improved to ensure high availability by enabling synchronous data replication to another RDS instance.

Which of the following performs synchronous data replication in RDS?

## Options

A. RDS Read Replica

B. Amazon CloudFront running as a Multi-AZ deployment

C. RDS DB instance running as a Multi-AZ deployment

D. Amazon DynamoDB Read Replica


---

# Question 46

A company needs to deploy at least two Amazon EC2 instances to support the normal workloads of its application and automatically scale up to six EC2 instances to handle the peak load. The architecture must be highly available and fault-tolerant as it is processing mission-critical workloads.

As a Solutions Architect, what should be done to meet this requirement?

## Options

A. Create an Auto Scaling group of EC2 instances and set the minimum capacity to 2 and the maximum capacity to 6. Use 2 Availability Zones and deploy 1 instance for each AZ.

B. Create an Auto Scaling group of EC2 instances and set the minimum capacity to 2 and the maximum capacity to 4. Deploy 2 instances in Availability Zone A and 2 instances in Availability Zone B.

C. Create an Auto Scaling group of EC2 instances and set the minimum capacity to 4 and the maximum capacity to 6. Deploy 2 instances in Availability Zone A and another 2 instances in Availability Zone B.

D. Create an Auto Scaling group of EC2 instances and set the minimum capacity to 2 and the maximum capacity to 6. Deploy 4 instances in Availability Zone A.


---

# Question 47

A company requires all the data stored in the cloud to be encrypted at rest. To easily integrate this with other AWS services, they must have full control over the encryption of the created keys and also the ability to immediately remove the key material from AWS KMS. The solution should also be able to audit the key usage independently of AWS CloudTrail.

Which of the following options will meet this requirement?

## Options

A. Use AWS Key Management Service to create AWS owned Keys and store the non-extractable key material in AWS CloudHSM.

B. Use AWS Key Management Service to create AWS managed keys and store the non-extractable key material in AWS CloudHSM.

C. Use AWS Key Management Service to create a KMS key in a custom key store and store the non-extractable key material in AWS CloudHSM.

D. Use AWS Key Management Service to create a KMS key in a custom key store and store the non-extractable key material in Amazon S3.


---

# Question 48

A company has recently migrated its microservices-based application to Amazon Elastic Kubernetes Service (Amazon EKS). As part of the migration, the company must ensure that all sensitive configuration data and credentials, such as database passwords and API keys, are stored securely and encrypted within the Amazon EKS cluster's etcd key-value store.

What is the most suitable solution to meet the company's requirements?

## Options

A. Use Amazon EKS default options and the Amazon Elastic Block Store (Amazon EBS) Container Storage Interface (CSI) driver as an add-on to securely store sensitive data within the Amazon EKS cluster.

B. Use AWS Secrets Manager with a new AWS KMS key to securely manage and store sensitive data within the EKS cluster's etcd key-value store.

C. Enable default Amazon EBS volume encryption for the account with a new AWS KMS key to ensure encryption of sensitive data within the Amazon EKS cluster.

D. Enable secret encryption with a new AWS KMS key on an existing Amazon EKS cluster to encrypt sensitive data stored in the EKS cluster's etcd key-value store.


---

# Question 49

A car dealership website hosted in Amazon EC2 stores car listings in an Amazon Aurora database managed by Amazon RDS. Once a vehicle has been sold, its data must be removed from the current listings and forwarded to a distributed processing system.

Which of the following options can satisfy the given requirement?

## Options

A. Create an RDS event subscription and send the notifications to AWS Lambda. Configure the Lambda function to fan out the event notifications to multiple Amazon SQS queues.

B. Create an RDS event subscription and send the notifications to Amazon SQS. Configure the SQS queues to fan out the event notifications to multiple Amazon SNS topics.

C. Create a native function or a stored procedure that invokes an AWS Lambda function. Configure the Lambda function to send event notifications to an Amazon SQS queue for the processing system to consume.

D. Create an RDS event subscription and send the notifications to Amazon SNS. Configure the SNS topic to fan out the event notifications to multiple Amazon SQS queues.


---

# Question 50

A company is using Amazon S3 to store frequently accessed data. When an object is created or deleted, the S3 bucket will send an event notification to the Amazon SQS queue. A solutions architect needs to create a solution that will notify the development and operations team about the created or deleted objects.

Which of the following would satisfy this requirement?

## Options

A. Create an Amazon SNS topic and configure two SQS queues to subscribe to the topic. Grant S3 permission to send notifications to SNS and update the bucket to use the new SNS topic.

B. Set up an Amazon SNS topic and configure two SQS queues to poll the SNS topic.

C. Create a new Amazon SNS FIFO topic for the other team. Grant S3 permission to send the notification to the second SNS topic.

D. Set up another SQS queue for the other team. Grant S3 permission to send a notification to the second SQS queue.


---

# Question 51

A company collects atmospheric data such as temperature, air pressure, and humidity from different countries. Each site location is equipped with various weather instruments and a high-speed Internet connection. The average collected data in each location is around 500 GB and will be analyzed by a weather forecasting application hosted in Northern Virginia. The Solutions Architect must determine the fastest way to aggregate all the data.

Which of the following options can satisfy the given requirement?

## Options

A. Set up a Site-to-Site VPN connection.

B. Use AWS Snowball Edge to transfer large amounts of data.

C. Enable Transfer Acceleration in the destination bucket and upload the collected data using Multipart Upload.

D. Upload the data to the closest Amazon S3 bucket. Set up a cross-region replication and copy the objects to the destination bucket.


---

# Question 52

A healthcare organization wants to build a system that can predict drug prescription abuse. The organization will gather real-time data from multiple sources, which include Personally Identifiable Information (PII). It's crucial that this sensitive information is anonymized prior to landing in a NoSQL database for further processing.

Which solution would meet the requirements?

## Options

A. Create a data lake in Amazon S3 and use it as the primary storage for patient health data. Use an S3 trigger to run an AWS Lambda function that performs anonymization.

B. Ingest real-time data using Amazon Kinesis Data Stream. Use an AWS Lambda function to anonymize the PII, then store it in Amazon DynamoDB.

C. Deploy an Amazon Data Firehose stream to capture and transform the streaming data. Deliver the anonymized data to Amazon Redshift for analysis.

D. Stream the data in an Amazon DynamoDB table. Enable DynamoDB Streams, and configure an AWS Lambda function to perform anonymization on newly written items.


---

# Question 53

A logistics company plans to automate its order management application. The company wants to use SFTP file transfer for uploading business-critical documents. Since the files are confidential, encryption at rest is required, and high availability must be ensured. Additionally, each file must be automatically deleted one month after creation.

Which of the following options should be implemented to meet the company's requirements with the least operational overhead?

## Options

A. Create an Amazon S3 bucket with encryption enabled. Configure AWS Transfer for SFTP to securely upload files to the S3 bucket. Configure the retention policy on the SFTP server to delete files after a month.

B. Create an Amazon Elastic File System (Amazon EFS) and enable encryption. Configure AWS Transfer for SFTP to securely upload files to the EFS file system. Apply an EFS lifecycle policy to delete files after 30 days.

C. Create an Amazon S3 bucket with encryption enabled. Launch an AWS Transfer for SFTP endpoint to securely upload files to the S3 bucket. Configure an S3 lifecycle rule to delete files after a month.

D. Provision an Amazon EC2 instance and install the SFTP service. Mount an encrypted Amazon EFS file system on the EC2 instance.


---

# Question 54

A Forex trading platform, which frequently processes and stores global financial data every minute, is hosted in an on-premises data center and uses an Oracle database. Due to a recent cooling problem in its data center, the company urgently needs to migrate its infrastructure to AWS to improve the performance of its applications.

Which combination of actions would meet the requirement? (Select TWO.)

## Options

A. Create an Oracle database in Amazon RDS with Multi-AZ deployments.

B. Migrate the Oracle database to AWS using the AWS Database Migration Service

C. Convert the database schema using the AWS Schema Conversion Tool.

D. Migrate the Oracle database to a non-cluster Amazon Aurora with a single instance.

E. Launch an Oracle database instance in Amazon RDS with Recovery Manager (RMAN) enabled.


---

# Question 55

An online medical system hosted in AWS stores sensitive Personally Identifiable Information (PII) of the users in an Amazon S3 bucket. Both the master keys and the unencrypted data should never be sent to AWS to comply with the strict compliance and regulatory requirements of the company.

Which S3 encryption technique should the Architect use?

## Options

A. Use S3 client-side encryption with a client-side master key.

B. Use S3 client-side encryption with an AWS KMS key.

C. Use S3 server-side encryption with customer provided key.

D. Use S3 server-side encryption with an AWS KMS key.


---

# Question 56

A popular social media website uses a Amazon CloudFront web distribution to serve static content to millions of users around the globe. Recently, the website has received a number of complaints about long login times. Additionally, there are instances where users encounter HTTP 504 errors.

Which of the following options should be used together to set up a cost-effective solution that improves the application's performance? (Select TWO.)

## Options

A. Implement an origin failover by creating an origin group that includes two origins. Assign one as the primary origin and the other as secondary.

B. Deploy your application to multiple AWS regions to accommodate your users around the world.

C. Establish multiple Amazon VPCs in different AWS regions and configure a transit VPC.

D. Customize the content that the CloudFront web distribution delivers to your users using Lambda@Edge, which allows your AWS Lambda functions to execute the authentication process in AWS locations closer to the users.

E. Configure your origin to add a Cache-Control max-age directive to your objects.


---

# Question 57

A retail company receives raw .csv data files into its Amazon S3 bucket from multiple sources on an hourly basis, with an average file size of 2 GB.

An automated process must be implemented to convert these .csv files into the more efficient Apache Parquet format and store the converted files in another S3 bucket. Additionally, the conversion process must be automatically initiated each time a new file is uploaded into the S3 bucket.

Which of the following options must be implemented to meet these requirements with the LEAST operational overhead?

## Options

A. Set up an Apache Spark job running in an Amazon EC2 instance and create an Amazon EventBridge rule to monitor S3 PUT events.

B. Create an ETL (Extract, Transform, Load) job and a Data Catalog table in AWS Glue. Configure the Glue crawler to run on a schedule every hour.

C. Use an AWS Lambda function triggered by an S3 PUT event to convert the .csv files to Parquet format.

D. Utilize an AWS Glue extract, transform, and load (ETL) job to process and convert the .csv files to Apache Parquet format. Set up an S3 Event Notification to track every S3 PUT event and invoke the ETL job in Glue through Amazon SQS.


---

# Question 58

A company is using a combination of API Gateway and AWS Lambda for the web services of an online web portal that is accessed by hundreds of thousands of clients each day. The company will be announcing a new revolutionary product, and it is expected that the web portal will receive a massive number of visitors from all around the globe.

How can the back-end systems and applications be protected from traffic spikes?

## Options

A. Deploy Multi-AZ in API Gateway with Read Replica

B. Use throttling limits in API Gateway

C. API Gateway will automatically scale and handle massive traffic spikes so you do not have to do anything.

D. Manually upgrade the Amazon EC2 instances being used by API Gateway


---

# Question 59

A company plans to migrate its on-premises workload to AWS. The current architecture is composed of a Microsoft SharePoint server that uses a Windows shared file storage. The Solutions Architect needs to use a cloud storage solution that is highly available and can be integrated with Active Directory for access control and authentication.

Which of the following options can satisfy the given requirement?

## Options

A. Create a file system using Amazon EFS and join it to an Active Directory domain.

B. Launch an Amazon EC2 Windows Server to mount a new Amazon S3 bucket as a file volume.

C. Create a file system using Amazon FSx for Windows File Server and join it to an Active Directory domain in AWS.

D. Create a Network File System (NFS) file share using AWS Storage Gateway.


---

# Question 60

A Docker application, which is running on an Amazon ECS cluster behind a load balancer, is heavily using Amazon DynamoDB. The application requires improved database performance by distributing the workload evenly and utilizing the provisioned throughput efficiently.

Which of the following should be implemented for the DynamoDB table?

## Options

A. Avoid using a composite primary key, which is composed of a partition key and a sort key.

B. Use partition keys with high-cardinality attributes, which have a large number of distinct values for each item.

C. Reduce the number of partition keys in the DynamoDB table.

D. Use partition keys with low-cardinality attributes, which have a few number of distinct values for each item.


---

# Question 61

A financial application consists of an Auto Scaling group of Amazon EC2 instances, an Application Load Balancer, and a MySQL RDS instance set up in a Multi-AZ Deployment configuration. To protect customers' confidential data, it must be ensured that the Amazon RDS database is only accessible using an authentication token specific to the profile credentials of EC2 instances.

Which of the following actions should be taken to meet this requirement?

## Options

A. Use a combination of IAM and STS to enforce restricted access to your RDS instance using a temporary authentication token.

B. Enable the IAM DB Authentication.

C. Configure SSL in your application to encrypt the database connection to RDS.

D. Create an IAM Role and assign it to your EC2 instances which will grant exclusive access to your RDS instance.


---

# Question 62

A company has a hybrid cloud architecture that connects its on-premises data center and cloud infrastructure in AWS. It requires a durable storage backup for its corporate documents stored on-premises and a local cache that provides low-latency access to recently accessed data to reduce data egress charges. The documents must be stored on and retrieved from AWS via the Server Message Block (SMB) protocol. These files must be immediately accessible within minutes for six months and archived for another decade to meet data compliance.

Which of the following is the best and most cost-effective approach to implement in this scenario?

## Options

A. Launch a new file gateway that connects to your on-premises data center using AWS Storage Gateway. Upload the documents to the file gateway and set up a lifecycle policy to move the data into Glacier for data archival.

B. Use AWS DataSync to transfer all files from the on-premises network directly to an Amazon S3 bucket.

C. Launch a new tape gateway that connects to your on-premises data center using AWS Storage Gateway.

D. Establish a Direct Connect connection to integrate your on-premises network to your VPC. Upload the documents on Amazon EBS Volumes.


---

# Question 63

A content management system (CMS) is hosted on a fleet of auto-scaled, On-Demand Amazon EC2 instances that use Amazon Aurora as its database. Currently, the system stores the file documents that users upload in one of the attached Amazon EBS volumes. The system's performance has been observed to be slow, and the manager has instructed the team to improve the architecture.

In this scenario, which solution should be implemented to achieve a scalable, highly available, POSIX-compliant shared file system?

## Options

A. Leverage Amazon ElastiCache to cache frequently accessed data and reduce latency

B. Create an Amazon S3 bucket and use this as the storage for the CMS

C. Upgrade your existing EBS volumes to Provisioned IOPS SSD volumes

D. Use Amazon EFS to provide a shared file system for concurrent access to data


---

# Question 64

A company has 3 DevOps engineers that are handling its software development and infrastructure management processes. One of the engineers accidentally deleted a file hosted in Amazon S3 which has caused disruption of service.

What can the DevOps engineers do to prevent this from happening again?

## Options

A. Enable S3 Versioning and Multi-Factor Authentication Delete on the bucket.

B. Set up a signed URL for all users.

C. Use S3 Infrequently Accessed storage to store the data.

D. Create an IAM bucket policy that disables delete operation.


---

# Question 65

A company is designing a banking portal that uses Amazon ElastiCache for Redis as its distributed session management component. To secure session data and ensure that Cloud Engineers must authenticate before executing Redis commands, specifically MULTI EXEC commands, the system should enforce strong authentication by requiring users to enter a password. Additionally, access should be managed with long-lived credentials while supporting robust security practices.

Which of the following actions should be taken to meet the above requirement?

## Options

A. Enable the in-transit encryption for Redis replication groups.

B. Authenticate the users using Redis AUTH by creating a new Redis Cluster with both the --transit-encryption-enabled and --auth-token parameters enabled.

C. Generate an IAM authentication token using AWS credentials and provide this token as a password.

D. Set up a Redis replication group and enable the AtRestEncryptionEnabled parameter.


---

