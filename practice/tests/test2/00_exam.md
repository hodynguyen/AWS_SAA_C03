# AWS SAA-C03 Practice Test 2 - Exam

# Question 1

A software company has resources hosted in AWS and on-premises servers. You have been requested to create a decoupled architecture for applications which make use of both resources.

Which of the following options are valid? (Select TWO.)

## Options

A. Use DynamoDB to utilize both on-premises servers and EC2 instances for your decoupled application

B. Use SWF to utilize both on-premises servers and EC2 instances for your decoupled application

C. Use SQS to utilize both on-premises servers and EC2 instances for your decoupled application

D. Use VPC peering to connect both on-premises servers and EC2 instances for your decoupled application

E. Use RDS to utilize both on-premises servers and EC2 instances for your decoupled application


---

# Question 2

A company has a top priority requirement to monitor certain database metrics and send email notifications to the Operations team if any issues occur.

Which combination of AWS services can accomplish this requirement? (Select TWO.)

## Options

A. Amazon Simple Notification Service (SNS)

B. Amazon CloudWatch

C. Amazon Simple Queue Service (SQS)

D. Amazon EC2 Instance with a running Berkeley Internet Name Domain (BIND) Server

E. Amazon Simple Email Service


---

# Question 3

A global company has deployed numerous AWS Outposts servers in various remote locations worldwide. These servers frequently need to download software updates consisting of multiple files from an S3 bucket in the us-west-2 region. The company is experiencing significant delays in distributing these updates across all servers.

What solution would most effectively reduce the deployment latency while minimizing operational overhead?

## Options

A. Create an Amazon CloudFront distribution with the us-west-2 S3 bucket as the origin. Use signed URLs for software downloads.

B. Use Amazon S3 Transfer Acceleration on the existing S3 bucket and have the Outposts servers use the Transfer Acceleration endpoint for downloads.

C. Set up AWS Global Accelerator to route traffic from Outposts servers to the nearest AWS edge location, then use private VIF connections to access the S3 bucket in us-west-2.

D. Set up an Amazon CloudFront distribution with the us-west-2 S3 bucket as the primary origin and create a secondary origin in another region, implementing a CachingDisabled cache policy. Use signed URLs for downloads.


---

# Question 4

A company receives semi-structured and structured data from different sources, which are eventually stored in their Amazon S3 data lake. The Solutions Architect plans to use big data processing frameworks to analyze these data and access it using various business intelligence tools and standard SQL queries.

Which of the following provides the MOST high-performing solution that fulfills this requirement?

## Options

A. Create an Amazon EMR cluster and store the processed data in Amazon Redshift.

B. Use AWS Glue and store the processed data in Amazon S3.

C. Create an Amazon EC2 instance and store the processed data in Amazon EBS.

D. Use Amazon Managed Service for Apache Flink Studio and store the processed data in Amazon DynamoDB.


---

# Question 5

A company is hosting its web application in an Auto Scaling group of EC2 instances behind an Application Load Balancer. Recently, the Solutions Architect identified a series of SQL injection attempts and cross-site scripting attacks to the application, which had adversely affected their production data.

Which of the following should the Architect implement to mitigate this kind of attack?

## Options

A. Using AWS Firewall Manager, set up security rules that block SQL injection and cross-site scripting attacks. Associate the rules to the Application Load Balancer.

B. Use Amazon GuardDuty to prevent any further SQL injection and cross-site scripting attacks in your application.

C. Block all the IP addresses where the SQL injection and cross-site scripting attacks originated using the Network Access Control List.

D. Set up security rules that block SQL injection and cross-site scripting attacks in AWS Web Application Firewall (WAF). Associate the rules to the Application Load Balancer.


---

# Question 6

An application is hosted in AWS Fargate and uses RDS database in Multi-AZ Deployments configuration with several Read Replicas. A Solutions Architect was instructed to ensure that all of their database credentials, API keys, and other secrets are encrypted and rotated on a regular basis to improve data security.

Which of the following is the MOST appropriate solution to secure the credentials?

## Options

A. Store the database credentials, API keys, and other secrets to AWS ACM.

B. Store the database credentials, API keys, and other secrets in AWS KMS.

C. Use AWS Secrets Manager to store and encrypt the database credentials, API keys, and other secrets. Enable automatic rotation for all of the credentials.

D. Store the database credentials, API keys, and other secrets to Systems Manager Parameter Store each with a SecureString data type. The credentials are automatically rotated by default.


---

# Question 7

A music publishing company is building a multitier web application that requires a key-value store which will save the document models. Each model is composed of band ID, album ID, song ID, composer ID, lyrics, and other data. The web tier will be hosted in an Amazon ECS cluster with AWS Fargate launch type.

Which of the following is the MOST suitable setup for the database-tier?

## Options

A. Launch a DynamoDB table.

B. Launch an Amazon RDS database with Read Replicas.

C. Launch an Amazon Aurora Serverless database.

D. Use Amazon WorkDocs to store the document models.


---

# Question 8

A company plans to migrate all of their applications to AWS. The Solutions Architect suggested to store all the data to EBS volumes. The Chief Technical Officer is worried that EBS volumes are not appropriate for the existing workloads due to compliance requirements, downtime scenarios, and IOPS performance.

Which of the following are valid points in proving that EBS is the best service to use for migration? (Select TWO.)

## Options

A. EBS volumes can be attached to any EC2 Instance in any Availability Zone.

B. Amazon EBS provides the ability to create snapshots (backups) of any EBS volume and write a copy of the data in the volume to Amazon RDS, where it is stored redundantly in multiple Availability Zones.

C. An EBS volume is off-instance storage that can persist independently from the life of an instance.

D. EBS volumes support live configuration changes while in production which means that you can modify the volume type, volume size, and IOPS capacity without service interruptions.

E. When you create an EBS volume in an Availability Zone, it is automatically replicated on a separate AWS region to prevent data loss due to a failure of any single hardware component.


---

# Question 9

A Solutions Architect of a multinational gaming company develops video games for PS4, Xbox One, and Nintendo Switch consoles, plus a number of mobile games for Android and iOS. Due to the wide range of their products and services, the architect proposed that they use API Gateway.

What are the key features of API Gateway that the architect can tell to the client? (Select TWO.)

## Options

A. It automatically provides a query language for your APIs similar to GraphQL.

B. Enables you to run applications requiring high levels of inter-node communications at scale on AWS through its custom-built operating system (OS) bypass hardware interface.

C. Enables you to build RESTful APIs and WebSocket APIs that are optimized for serverless workloads.

D. Provides you with static anycast IP addresses that serve as a fixed entry point to your applications hosted in one or more AWS Regions.

E. You pay only for the API calls you receive and the amount of data transferred out.


---

# Question 10

A company has an application that continually sends encrypted documents to Amazon S3. The company requires that the configuration for data access is in line with its strict compliance standards. It should also be alerted if there is any risk of unauthorized access or suspicious access patterns.

Which step is needed to meet the requirements?

## Options

A. Use Amazon GuardDuty to monitor malicious activity on S3.

B. Use Amazon Rekognition to monitor and recognize patterns on S3.

C. Use AWS CloudTrail to monitor and detect access patterns on S3.

D. Use Amazon Inspector to alert whenever a security violation is detected on S3.


---

# Question 11

An organization stores and manages financial records of various companies in its on-premises data center, which is almost out of space. The management decided to move all of their existing records to a cloud storage service. All future financial records will also be stored in the cloud. For additional security, all records must be prevented from being deleted or overwritten.

Which of the following should you do to meet the above requirement?

## Options

A. Use AWS DataSync to move the data. Store all of your data in Amazon S3 and enable object lock.

B. Use AWS Storage Gateway to establish hybrid cloud storage. Store all of your data in Amazon S3 and enable object lock.

C. Use AWS Storage Gateway to establish hybrid cloud storage. Store all of your data in Amazon EBS and enable object lock.

D. Use AWS DataSync to move the data. Store all of your data in Amazon EFS and enable object lock.


---

# Question 12

A company launched a website that accepts high-quality photos and turns the photos into a downloadable video montage. The website offers both a free and a premium account, with the premium account guaranteeing faster processing. All requests by both free and premium members go through a single Amazon SQS queue and are then processed by a group of Amazon EC2 instances that generate the videos. The company needs to ensure that premium users, who paid for the service, have higher priority than free members.

How should the company re-design its architecture to address this requirement?

## Options

A. Create an SQS queue for free members and another one for premium members. Configure your EC2 instances to consume messages from the premium queue first and if it is empty, poll from the free members' SQS queue.

B. For the requests made by premium members, set a higher priority in the SQS queue so it will be processed first compared to the requests made by free members.

C. Use Amazon S3 to store and process the photos and then generate the video montage afterward.

D. Use Amazon Kinesis to process the photos and generate the video montage in real-time.


---

# Question 13

A company is running a multi-tier web application farm in a virtual private cloud (VPC) that is not connected to their corporate network. They are connecting to the VPC over the Internet to manage the fleet of Amazon EC2 instances running in both the public and private subnets. The Solutions Architect has added a bastion host with Microsoft Remote Desktop Protocol (RDP) access to the application instance security groups, but the company wants to further limit administrative access to all of the instances in the VPC.

Which of the following bastion host deployment options will meet this requirement?

## Options

A. Deploy a Windows Bastion host with an Elastic IP address in the public subnet and allow RDP access to bastion only from the corporate IP addresses.

B. Deploy a Windows Bastion host with an Elastic IP address in the public subnet and allow SSH access to the bastion from anywhere.

C. Deploy a Windows Bastion host on the corporate network that has RDP access to all EC2 instances in the VPC.

D. Deploy a Windows Bastion host with an Elastic IP address in the private subnet, and restrict RDP access to the bastion from only the corporate public IP addresses.


---

# Question 14

An online events registration system is hosted in AWS and uses ECS to host its front-end tier and an RDS configured with Multi-AZ for its database tier. What are the events that will make Amazon RDS automatically perform a failover to the standby replica? (Select TWO.)

## Options

A. Loss of availability in primary Availability Zone

B. Compute unit failure on secondary DB instance

C. Storage failure on secondary DB instance

D. Storage failure on primary

E. In the event of Read Replica failure


---

# Question 15

A media company has two VPCs: VPC-1 and VPC-2 with peering connection between each other. VPC-1 only contains private subnets while VPC-2 only contains public subnets. The company uses a single AWS Direct Connect connection and a virtual interface to connect their on-premises network with VPC-1.

Which of the following options increase the fault tolerance of the connection to VPC-1? (Select TWO.)

## Options

A. Establish a hardware VPN over the Internet between VPC-1 and the on-premises network.

B. Establish a new AWS Direct Connect connection and private virtual interface in the same region as VPC-2.

C. Use the AWS VPN CloudHub to create a new AWS Direct Connect connection and private virtual interface in the same region as VPC-2.

D. Establish another AWS Direct Connect connection and private virtual interface in the same AWS region as VPC-1.

E. Establish a hardware VPN over the Internet between VPC-2 and the on-premises network.


---

# Question 16

A company needs to assess and audit all the configurations in its AWS account. It must enforce strict compliance by tracking all configuration changes made to any of its Amazon S3 buckets. Publicly accessible S3 buckets should also be identified automatically to avoid data breaches.

Which of the following options will meet this requirement?

## Options

A. Use AWS Config to set up a rule in your AWS account.

B. Use AWS IAM to generate a credential report.

C. Use AWS CloudTrail and review the event history of your AWS account.

D. Use AWS Trusted Advisor to analyze your AWS environment.


---

# Question 17

A media company hosts large volumes of archive data that are about 250 TB in size on its internal servers. The company has decided to move this data to Amazon S3 because of its durability and redundancy. The company currently has a 100 Mbps dedicated line connecting its head office to the Internet.

Which of the following is the FASTEST and MOST COST-EFFECTIVE way to import all this data to S3?

## Options

A. Request several AWS Snowball devices to upload the data into S3.

B. Upload it directly to S3

C. Use S3 Transfer Acceleration to speed up the upload.

D. Establish a direct connection using AWS Direct Connect, then transfer the data over to S3.


---

# Question 18

An organization needs to control access to several Amazon S3 buckets. The organization plans to use a gateway endpoint to allow access to trusted buckets.

Which of the following could help you achieve this requirement?

## Options

A. Generate a bucket policy for trusted VPCs.

B. Generate a bucket policy for trusted S3 buckets.

C. Generate an endpoint policy for trusted VPCs.

D. Generate an endpoint policy for trusted S3 buckets.


---

# Question 19

A company hosts its web application on a set of Amazon EC2 instances in an Auto Scaling group behind an Application Load Balancer (ALB). The application has an embedded NoSQL database. As the application receives more traffic, the application becomes overloaded mainly due to database requests.

Which of the following options can meet the company requirements with the least operational overhead?

## Options

A. Configure the Auto Scaling group to spread the EC2 instances across three Availability Zones. Configure replication of the NoSQL database on the set of EC2 instances to spread the database load.

B. Change the ALB with a Network Load Balancer (NLB) to handle more traffic. Use the AWS Glue DynamoDB export connector to export data from Amazon DynamoDB to Amazon S3 for analytics periodically.

C. Configure the Auto Scaling group to spread the EC2 instances across three Availability Zones. Use the AWS Database Migration Service (AWS DMS) with a replication server and an ongoing replication task to migrate the embedded NoSQL database to Amazon DynamoDB.

D. Change the ALB with a Network Load Balancer (NLB) to handle more traffic and integrate AWS Global Accelerator to ensure high availability.


---

# Question 20

A company has a serverless application made up of AWS Amplify, Amazon API Gateway and a Lambda function. The application is connected to an Amazon RDS MySQL database inside a private subnet. There are times during peak loads when the database throws a "too many connections" error.

Which solution could the company take to resolve the issue?

## Options

A. Increase the rate limit of API Gateway

B. Increase the concurrency limit of the Lambda function

C. Provision an RDS Proxy between the Lambda function and RDS database instance

D. Increase the memory allocation of the Lambda function


---

# Question 21

A commercial bank has a forex trading application. They created an Auto Scaling group of EC2 instances that allow the bank to cope with the current traffic and achieve cost-efficiency. They want the Auto Scaling group to behave in such a way that it will follow a predefined set of parameters before it scales down the number of EC2 instances, which protects the system from unintended slowdown or unavailability.

Which of the following statements are true regarding the cooldown period? (Select TWO.)

## Options

A. It ensures that the Auto Scaling group launches or terminates additional EC2 instances without any downtime.

B. Its default value is 300 seconds.

C. It ensures that before the Auto Scaling group scales out, the EC2 instances have ample time to cooldown.

D. Its default value is 600 seconds.

E. It ensures that the Auto Scaling group does not launch or terminate additional EC2 instances before the previous scaling activity takes effect.


---

# Question 22

A company plans to migrate its suite of containerized applications running on-premises to a container service in AWS. The solution must be cloud-agnostic and use an open-source platform that can automatically manage containerized workloads and services.

What should the Solution Architect do to properly migrate and satisfy the given requirement?

## Options

A. Migrate the application to Amazon Container Registry (ECR) with Amazon EC2 instance worker nodes.

B. Migrate the application to Amazon Elastic Kubernetes Service with EKS worker nodes.

C. Migrate the application to Amazon Elastic Container Service with ECS tasks that use the Amazon EC2 launch type.

D. Migrate the application to Amazon Elastic Container Service with ECS tasks that use the AWS Fargate launch type.


---

# Question 23

A company is building an internal application that allows users to upload images. Each upload request must be sent to Amazon Kinesis Data Streams for processing before the pictures are stored in an Amazon S3 bucket. The application should immediately return a success message to the user after the upload, while the downstream processing is handled asynchronously.

Which solution will enable asynchronous processing from Kinesis to S3 in the most cost-effective way?

## Options

A. Use Kinesis Data Streams with AWS Lambda consumers to asynchronously process records and write them to S3.

B. Send data from Kinesis Data Streams to Amazon Data Firehose and configure it to deliver directly to S3.

C. Use a combination of Amazon SQS to queue the requests and then asynchronously process them using On-Demand Amazon EC2 Instances.

D. Use a combination of AWS Lambda and Step Functions to orchestrate service components and asynchronously process the requests.


---

# Question 24

A business has a network of surveillance cameras installed within the premises of its data center. Management wants to leverage Artificial Intelligence to monitor and detect unauthorized personnel entering restricted areas. Should an unauthorized person be detected, the security team must be alerted via SMS.

Which solution satisfies the requirement?

## Options

A. Use Amazon Kinesis Video Streams to stream live feeds from the cameras. Use Amazon Rekognition to detect unauthorized personnel. Set the phone numbers of the security team as subscribers to an Amazon SNS topic.

B. Set up Amazon Managed Service for Prometheus to stream live feeds from the cameras. Use Amazon Fraud Detector to detect unauthorized personnel.

C. Configure Amazon Elastic Transcoder to stream live feeds from the cameras. Use Amazon Kendra to detect authorized personnel.

D. Utilize a custom containerized video processing application on Amazon EKS. Integrate AWS App2Container and Amazon SageMaker Autopilot.


---

# Question 25

A digital media company shares static content to its premium users around the world and also to their partners who syndicate their media files. The company is looking for ways to reduce its server costs and securely deliver their data to their customers globally with low latency.

Which combination of services should be used to provide the MOST suitable and cost-effective architecture? (Select TWO.)

## Options

A. AWS Lambda

B. Amazon CloudFront

C. AWS Global Accelerator

D. Amazon S3

E. AWS Fargate


---

# Question 26

A media company is setting up an ECS batch architecture for its image processing application. It will be hosted in an Amazon ECS Cluster with two ECS tasks that will handle image uploads from the users and image processing. The first ECS task will process the user requests, store the image in an S3 input bucket, and push a message to a queue. The second task reads from the queue, parses the message containing the object name, and then downloads the object.

Which of the following should the Architect do next?

## Options

A. Launch a new Amazon Data Firehose and configure the second ECS task to read from it. Create an IAM role that the ECS tasks can assume to get access to the S3 buckets and Data Firehose. Specify the ARN of the IAM Role in the taskDefinitionArn field.

B. Launch a new Amazon SQS queue and configure the second ECS task to read from it. Create an IAM role that the ECS tasks can assume to get access to the S3 buckets and SQS queue. Declare the IAM Role (taskRoleArn) in the task definition.

C. Launch a new Amazon AppStream 2.0 queue and configure the second ECS task to read from it.

D. Launch a new Amazon MQ queue and configure the second ECS task to read from it. Set the (EnableTaskIAMRole) option to true.


---

# Question 27

A company has a dynamic web app written in MEAN stack that is going to be launched in the next month. There is a probability that the traffic will be quite high in the first couple of weeks. In the event of a load failure, how can you set up DNS failover to a static website?

## Options

A. Add more servers in case the application fails.

B. Enable failover to an application hosted in an on-premises data center.

C. Duplicate the exact application architecture in another region and configure DNS weight-based routing.

D. Use Route 53 with the failover option to a static S3 website bucket or CloudFront distribution.


---

# Question 28

A company runs a messaging application in the ap-northeast-1 and ap-southeast-2 region. A Solutions Architect needs to create a routing policy wherein a larger portion of traffic from the Philippines and North India will be routed to the resource in the ap-northeast-1 region.

Which Route 53 routing policy should the Solutions Architect use?

## Options

A. Latency Routing

B. Geolocation Routing

C. Geoproximity Routing

D. Weighted Routing


---

# Question 29

A multinational company currently operates multiple AWS accounts to support its operations across various branches and business units. The company needs a more efficient and secure approach in managing its vast AWS infrastructure to avoid costly operational overhead.

Which combination of options can be used to meet the above requirements? (Select TWO.)

## Options

A. Implement AWS Organizations to create a multi-account architecture that provides a consolidated view and centralized management of AWS accounts.

B. Utilize AWS CloudTrail to enable centralized logging and monitoring across all AWS accounts.

C. Integrate AWS IAM Identity Center with the corporate directory service for centralized authentication. Configure a service control policy (SCP) to manage the AWS accounts.

D. Set up a new entity in AWS Organizations and configure its authentication system to utilize AWS Directory Service directly.

E. Establish an identity pool through Amazon Cognito and adjust the AWS IAM Identity Center settings to allow Amazon Cognito authentication.


---

# Question 30

A Solutions Architect is building a cloud infrastructure where Amazon EC2 instances require access to various AWS services, such as Amazon S3 and Amazon Redshift. The Architect will also need to provide access to system administrators so that the administrators can deploy and test changes.

Which configuration should be used to ensure that access to the resources is secured and not compromised? (Select TWO.)

## Options

A. Assign an IAM user for each EC2 Instance.

B. Store the AWS Access Keys in the EC2 instance.

C. Store the AWS Access Keys in ACM.

D. Enable Multi-Factor Authentication.

E. Assign an IAM role to the EC2 instance.


---

# Question 31

A solutions architect is instructed to host a website that consists of HTML, CSS, and some Javascript files. The web pages will display several high-resolution images. The website should have optimal loading times and be able to respond to high request rates.

Which of the following architectures can provide the most cost-effective and fastest loading experience?

## Options

A. Launch an Auto Scaling Group using an AMI that has a pre-configured Apache web server, then configure the scaling policy accordingly. Store the images in an Elastic Block Store.

B. Host the website in an AWS Elastic Beanstalk environment. Upload the images in an S3 bucket. Use CloudFront as a CDN.

C. Upload the HTML, CSS, Javascript, and the images in a single bucket. Then enable website hosting. Create a CloudFront distribution and point the domain on the S3 website endpoint.

D. Host the website using an Nginx server in an EC2 instance. Upload the images in an S3 bucket. Use CloudFront as a CDN.


---

# Question 32

An insurance company plans to implement a message filtering feature in its web application. To implement this solution, it needs to create separate Amazon SQS queues for each type of quote request. The entire message processing should not exceed 24 hours.

Which of the following solutions should be implemented to meet the above requirement?

## Options

A. Create a data stream in Amazon Kinesis Data Streams. Use the Kinesis Client Library to deliver all the records to the designated SQS queues.

B. Create one Amazon SNS topic and configure the SQS queues to subscribe to the SNS topic. Publish the same messages to all SQS queues. Filter the messages in each queue.

C. Create one Amazon SNS topic and configure the SQS queues to subscribe to the SNS topic. Set the filter policies in the SNS subscriptions to publish the message to the designated SQS queue.

D. Create multiple Amazon SNS topics and configure the SQS queues to subscribe to the SNS topics.


---

# Question 33

A start-up company that offers an intuitive financial data analytics service has consulted about its AWS architecture. The company has a fleet of Amazon EC2 worker instances that process financial data and then output reports used by its clients. The reports must be stored in a durable storage.

Which of the following is a cost-efficient and scalable storage option for this scenario?

## Options

A. Use Amazon Redshift as the data storage and Amazon CloudFront as the CDN.

B. Use Amazon S3 Glacier as the data storage and Amazon ElastiCache as the CDN.

C. Use multiple EC2 instance stores for data storage and Amazon ElastiCache as the CDN.

D. Use Amazon S3 as the data storage and Amazon CloudFront as the CDN.


---

# Question 34

A company has a cryptocurrency exchange portal that is hosted in an Auto Scaling group of EC2 instances behind an Application Load Balancer and is deployed across multiple AWS regions. The majority users are from Japan and Sweden. Because of compliance requirements, the Japanese users should connect to the ap-northeast-1 region, while the Swedish users should be connected to the eu-west-1 region.

Which of the following services would allow you to easily fulfill this requirement?

## Options

A. Set up an Application Load Balancers that will automatically route the traffic to the proper AWS region.

B. Use Route 53 Geolocation Routing policy.

C. Set up a new CloudFront web distribution with the geo-restriction feature enabled.

D. Use Route 53 Weighted Routing policy.


---

# Question 35

A company wants to organize the way it tracks its spending on AWS resources. A report that summarizes the total billing accrued by each department must be generated at the end of the month.

Which solution will meet the requirements?

## Options

A. Tag resources with the department name and enable cost allocation tags.

B. Use AWS Cost Explorer to view spending and filter usage data by Resource.

C. Create a Cost and Usage report for AWS services that each department is using.

D. Tag resources with the department name and configure a budget action in AWS Budget.


---

# Question 36

An organization is currently using a tape backup solution to store its application data on-premises. Plans are in place to use a cloud storage service to preserve the backup data for up to 10 years, which may be accessed about once or twice a year.

Which of the following is the most cost-effective option to implement this solution?

## Options

A. Use Amazon S3 to store the backup data and add a lifecycle rule to transition the current version to Amazon S3 Glacier.

B. Use AWS Storage Gateway to backup the data directly to Amazon S3 Glacier Flexible Retrieval.

C. Use AWS Storage Gateway to backup the data and transition it to Amazon S3 Glacier Deep Archive.

D. Order an AWS Snowball Edge appliance to import the backup directly to Amazon S3 Glacier Flexible Retrieval.


---

# Question 37

A media company wants to ensure that the images it delivers through Amazon CloudFront are compatible across various user devices. The company plans to serve images in WebP format to user agents that support it and return to JPEG format for those that don't.

Which approach would you recommend to meet these requirements while minimizing operational overhead?

## Options

A. Create multiple CloudFront distributions, each serving a specific image format.

B. Implement an image conversion service on Amazon EC2 instances and integrate it with CloudFront.

C. Configure CloudFront behaviors to handle different image formats based on the User-Agent header. Use Lambda@Edge functions to modify the response headers.

D. Generate a CloudFront response headers policy to deliver the suitable image format.


---

# Question 38

A Solutions Architect created a new Standard-class Amazon S3 bucket to store financial reports that are not frequently accessed but should immediately be available when an auditor requests the reports.

In S3 Standard - Infrequent Access storage class, which of the following statements are true? (Select TWO.)

## Options

A. It is designed for data that requires rapid access when needed.

B. It is designed for data that is accessed less frequently.

C. Ideal to use for data archiving.

D. It provides high latency and low throughput performance.

E. It automatically moves data to the most cost-effective access tier.


---

# Question 39

A company owns a photo-sharing app that stores user uploads on Amazon S3. There has been an increase in explicit and offensive images being reported. The company wants to streamline moderation using Artificial Intelligence to flag images for review. Any communication with its resources on its Amazon VPC must not traverse the public Internet.

How can this task be accomplished with the LEAST amount of effort?

## Options

A. Use Amazon Detective to detect images with graphic nudity or violence in S3.

B. Use Amazon Rekognition to detect images with graphic nudity or violence in S3. Create an Interface VPC endpoint for Rekognition.

C. Use AWS Lambda to create custom image moderation logic. Deploy this Lambda function in a public VPC.

D. Use an image classification model in Amazon SageMaker. Set up Amazon GuardDuty.


---

# Question 40

A company wants to streamline the process of creating multiple AWS accounts within an AWS Organization. Each organization unit (OU) must be able to launch new accounts with preapproved configurations from the security team.

Which solution entails the least amount of effort to implement?

## Options

A. Centralized the creation of AWS accounts using AWS Systems Manager OpsCenter. Enforce policies using AWS Security Hub.

B. Configure AWS Resource Access Manager (AWS RAM) to launch new AWS accounts.

C. Set up an AWS Config aggregator on the root account of the organization to enable multi-account data aggregation.

D. Set up an AWS Control Tower Landing Zone. Enable pre-packaged guardrails to enforce policies or detect violations.


---

# Question 41

A DevOps Engineer is required to design a cloud architecture in AWS. The Engineer is planning to develop a highly available and fault-tolerant architecture consisting of an Elastic Load Balancer and an Auto Scaling group of EC2 instances deployed across multiple Availability Zones. This will be used by an online accounting application that requires path-based routing, host-based routing, and bi-directional streaming using Remote Procedure Call (gRPC).

Which configuration will satisfy the given requirement?

## Options

A. Configure a Network Load Balancer in front of the auto-scaling group. Create an AWS Global Accelerator.

B. Configure a Network Load Balancer in front of the auto-scaling group. Use a UDP listener for routing.

C. Configure a Gateway Load Balancer in front of the auto-scaling group. Use the GENEVE protocol on port 6081.

D. Configure an Application Load Balancer in front of the auto-scaling group. Select gRPC as the protocol version.


---

# Question 42

A company is running a dashboard application on a Spot EC2 instance inside a private subnet. The dashboard is reachable via a domain name that maps to the private IPv4 address of the instance's network interface. A solutions architect needs to increase network availability by allowing the traffic flow to resume in another instance if the primary instance is terminated.

Which solution accomplishes these requirements?

## Options

A. Use the AWS Transit Gateway to automatically move an EIP to a secondary instance.

B. Create a secondary elastic network interface and point its private IPv4 address to the application's domain name. Attach the new network interface to the primary instance. If the instance goes down, move the secondary network interface to another instance.

C. Set up AWS Transfer for FTPS service to disable the source/destination checks.

D. Use the AWS Network Firewall to detach the instance's primary elastic network interface.


---

# Question 43

A company has two On-Demand EC2 instances inside the Virtual Private Cloud in the same Availability Zone but are deployed to different subnets. One EC2 instance is running a database and the other EC2 instance a web application that connects with the database. You need to ensure that these two instances can communicate using their private IP addresses.

What should be done to accomplish this requirement?

## Options

A. Ensure that the default security group allows inbound and outbound traffic.

B. Create a site-to-site VPN connection between the two subnets.

C. Ensure that the route tables have the correct configurations to send traffic from one subnet to another.

D. Enable VPC peering between the subnets.


---

# Question 44

A company needs a storage solution that provides very high throughput performance for processing financial workloads. The workloads involve data processing, model training, and simulation. The data is stored in Amazon S3 and must be accessible to the compute resources running on EC2 instances.

Which AWS service should the Solutions Architect recommend?

## Options

A. Amazon EFS with Max I/O performance mode.

B. Amazon FSx for Lustre.

C. AWS DataSync.

D. Amazon S3 File Gateway.


---

# Question 45

A company is migrating an on-premises Oracle database to Amazon RDS for Oracle. The database handles mission-critical workloads and the company wants the migration to involve minimal downtime.

Which service should be used to migrate the database?

## Options

A. AWS Database Migration Service (DMS).

B. AWS DataSync.

C. AWS Snowball Edge.

D. Amazon Kinesis Data Firehose.


---

# Question 46

A company runs a mobile gaming application that uses Amazon DynamoDB as its data store. The game has spiked in popularity and the development team needs to reduce response times. Read requests on specific items are much more common than write requests.

Which solution provides the lowest latency for repeated reads?

## Options

A. Enable DynamoDB Accelerator (DAX).

B. Enable DynamoDB Auto Scaling.

C. Enable DynamoDB Global Tables.

D. Enable DynamoDB Streams.


---

# Question 47

A company is implementing a disaster recovery strategy. They need to ensure that data from an Amazon Aurora MySQL database can be recovered in a secondary AWS Region.

Which approach provides the MOST operationally efficient solution?

## Options

A. Create manual snapshots and copy them to the secondary region.

B. Configure an Aurora Global Database with a secondary read replica in another Region.

C. Use AWS DataSync to replicate the database.

D. Set up cross-region replication using Amazon S3.


---

# Question 48

A solutions architect is designing a solution to store and analyze log files from a web application across multiple servers. The log files should be aggregated in near real-time and subsequently stored in a data lake for batch analysis.

Which solution meets these requirements?

## Options

A. Use Amazon Kinesis Data Firehose to collect and deliver the log data to Amazon S3.

B. Install CloudWatch agent on each server and send logs to Amazon RDS.

C. Use AWS Data Pipeline to transfer log files to Amazon Redshift.

D. Set up Amazon SQS queues to aggregate logs and write to Amazon DynamoDB.


---

# Question 49

A company requires that all HTTP traffic to its web applications be automatically redirected to HTTPS. The application runs behind an Application Load Balancer.

Which solution meets this requirement with minimal operational effort?

## Options

A. Configure an AWS WAF web ACL to check for HTTP traffic and redirect to HTTPS.

B. Configure a Lambda function to inspect incoming requests.

C. Configure a listener rule on the ALB to redirect HTTP traffic to HTTPS.

D. Configure Amazon CloudFront to handle the redirect.


---

# Question 50

A company is running a three-tier architecture on AWS with a web tier, application tier, and database tier. The application requires low latency and the ability to handle thousands of concurrent connections to a MySQL database.

Which solution provides the LOWEST latency for database operations?

## Options

A. Enable Multi-AZ deployment for the RDS instance.

B. Create an Amazon ElastiCache cluster in front of the RDS instance.

C. Enable RDS read replicas.

D. Migrate to Amazon Aurora with provisioned capacity.


---

# Question 51

A company needs to implement a solution that provides persistent storage for a Docker container environment running on Amazon ECS. The containers are running on EC2 instances and need to share files between tasks.

Which storage option is most appropriate?

## Options

A. Amazon EBS volumes.

B. Amazon S3.

C. Amazon EFS.

D. EC2 instance store.


---

# Question 52

A company has strict data sovereignty requirements and must ensure that data does not leave a specific AWS Region. The company uses Amazon S3 for data storage.

Which feature should be used to enforce this requirement?

## Options

A. Enable S3 Object Lock.

B. Configure S3 Bucket Policies with IP restrictions.

C. Enable S3 Block Public Access.

D. Create an S3 Bucket that is restricted to a specific AWS Region using bucket policy conditions.


---

# Question 53

A Solutions Architect is designing a solution for a company that runs batch processing jobs. The jobs can be interrupted and restarted without any impact on the final output. The company wants to minimize compute costs.

Which EC2 purchasing option is most cost-effective?

## Options

A. On-Demand Instances.

B. Reserved Instances.

C. Spot Instances.

D. Dedicated Hosts.


---

# Question 54

A company runs an e-commerce application that experiences variable traffic. During peak periods, customers experience slow response times when the application writes data to the database. The company uses Amazon RDS MySQL.

Which solution will improve write performance?

## Options

A. Enable RDS Multi-AZ deployment.

B. Add read replicas to the RDS instance.

C. Migrate to Amazon Aurora with multiple writer endpoints.

D. Increase the RDS instance size.


---

# Question 55

A company wants to encrypt all data stored in Amazon S3 using keys that it manages itself. The company must retain full control over the encryption keys.

Which solution meets this requirement?

## Options

A. Use SSE-S3 with Amazon S3 managed keys.

B. Use SSE-KMS with AWS managed keys.

C. Use SSE-C with customer-provided keys.

D. Use SSE-KMS with customer managed keys (CMK).


---

# Question 56

A company is running a legacy application that uses a file-based storage system. The application needs to migrate to AWS with minimal code changes. The storage must be accessible from multiple EC2 instances simultaneously.

Which storage solution should be used?

## Options

A. Amazon S3 with S3 File Gateway.

B. Amazon EBS with Multi-Attach.

C. Amazon EFS.

D. AWS Storage Gateway Volume Gateway.


---

# Question 57

A company has deployed an application using Amazon EC2 instances with an Application Load Balancer. The security team requires that all inbound traffic to the application be inspected for malicious content.

Which solution provides this capability?

## Options

A. Deploy AWS Shield Standard.

B. Configure Security Groups to filter traffic.

C. Integrate AWS WAF with the Application Load Balancer.

D. Enable VPC Flow Logs.


---

# Question 58

A company needs to process large volumes of video files. The processing is CPU-intensive and takes several hours per file. The company wants to optimize costs while maintaining consistent throughput.

Which EC2 instance type is most suitable?

## Options

A. General purpose (M5) instances.

B. Compute optimized (C5) instances.

C. Memory optimized (R5) instances.

D. Storage optimized (I3) instances.


---

# Question 59

A company wants to grant temporary access to AWS resources for mobile application users. The users should not need to create AWS accounts.

Which service should be used?

## Options

A. AWS IAM users with temporary credentials.

B. Amazon Cognito identity pools.

C. AWS Directory Service.

D. AWS Single Sign-On.


---

# Question 60

A company is designing a solution to collect and analyze clickstream data from a web application. The data must be available for analysis in near real-time.

Which solution meets these requirements?

## Options

A. Amazon SQS and AWS Lambda.

B. Amazon Kinesis Data Streams and Amazon OpenSearch Service.

C. Amazon S3 and Amazon Athena.

D. AWS Glue and Amazon Redshift.


---

# Question 61

A company runs a serverless application using AWS Lambda functions. The functions retrieve configuration data from a database. The company wants to reduce latency and improve performance.

Which solution improves function performance?

## Options

A. Increase the Lambda function memory.

B. Store configuration in Lambda environment variables.

C. Use provisioned concurrency.

D. Enable Lambda function URL.


---

# Question 62

A company has a requirement to retain application logs for 7 years for compliance purposes. The logs should be easily searchable for the first 90 days and archived afterward.

Which solution meets these requirements cost-effectively?

## Options

A. Store logs in Amazon CloudWatch Logs with a 7-year retention period.

B. Store logs in Amazon S3 Standard and use S3 lifecycle policies to transition to S3 Glacier after 90 days.

C. Store logs in Amazon EBS volumes with snapshots.

D. Store logs in Amazon DynamoDB with TTL enabled.


---

# Question 63

A company runs a web application on Amazon EC2 instances in an Auto Scaling group. The company notices that the instances are frequently scaling up and down rapidly.

Which action will stabilize the scaling behavior?

## Options

A. Increase the cooldown period.

B. Decrease the minimum instance count.

C. Enable detailed monitoring.

D. Change from target tracking to simple scaling.


---

# Question 64

A company wants to host a static website on Amazon S3. The website should be accessible through a custom domain with HTTPS.

Which combination of services should be used? (Select TWO.)

## Options

A. Amazon S3 website hosting with custom SSL certificate.

B. Amazon CloudFront with an ACM certificate.

C. Amazon Route 53 with an alias record.

D. AWS Certificate Manager with S3 directly.

E. Application Load Balancer.


---

# Question 65

A company is designing an application that requires a highly available relational database. The database should automatically handle read scaling and failover.

Which solution provides these capabilities with least operational overhead?

## Options

A. Amazon RDS for MySQL with Multi-AZ and read replicas.

B. Amazon Aurora with Auto Scaling for read replicas.

C. Amazon DynamoDB with global tables.

D. Amazon Redshift with concurrency scaling.


---

