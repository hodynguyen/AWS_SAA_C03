# AWS SAA-C03 Practice Test 4 - Full Exam

# Question 1

## Topic
Design High-Performing Architectures

## Question
An organization uses a Microsoft SQL Server database to support its suite of applications. The organization plans to transition to an Amazon Aurora PostgreSQL database while minimizing application code modifications.

Which combination of actions will achieve these objectives? (Select TWO.)

## Options
A. Use AWS Schema Conversion Tool (AWS SCT) to convert the database schema and AWS Database Migration Service (AWS DMS) to migrate the data.

B. Use Amazon Kinesis Data Streams for real-time data replication to Aurora PostgreSQL.

C. Use AWS AppConfig to manage configuration updates during the migration.

D. Turn on Babelfish on Aurora PostgreSQL to allow applications to continue using existing SQL queries.

E. Use AWS Glue to transform the SQL queries from the applications for compatibility with Aurora PostgreSQL.

---

# Question 2

## Topic
Design Cost-Optimized Architectures

## Question
A company has stored 200 TB of backup files in Amazon S3. The files are in a vendor-proprietary format. The Solutions Architect needs to use the vendor's proprietary file conversion software to retrieve the files from their Amazon S3 bucket, transform the files to an industry-standard format, and re-upload the files back to Amazon S3. The solution must minimize the data transfer costs.

Which of the following options can satisfy the given requirement?

## Options
A. Deploy the EC2 instance in the same Region as Amazon S3. Install the file conversion software on the instance. Perform data transformation and re-upload it to Amazon S3.

B. Deploy the EC2 instance in a different Region. Install the conversion software on the instance. Perform data transformation and re-upload it to Amazon S3.

C. Install the file conversion software in Amazon S3. Use S3 Batch Operations to perform data transformation.

D. Export the data using AWS Snowball Edge device. Install the file conversion software on the device. Transform the data and re-upload it to Amazon S3.

---

# Question 3

## Topic
Design High-Performing Architectures

## Question
A technology company is building a new cryptocurrency trading platform that allows the buying and selling of Bitcoin, Ethereum, Ripple, Tether, and many others. A Cloud Engineer was hired to build the infrastructure required for this platform. During the first week, the engineer began creating CloudFormation YAML scripts to define all of the AWS resources needed for the application. The manager was shocked that the engineer hadn't set up the EC2 instances, S3 buckets, and other AWS resources immediately. He doesn't understand the purpose of the text-based scripts the engineer has written and has asked for clarification.

In this scenario, what are the benefits of using Amazon CloudFormation that the manager should know to address his concerns? (Select TWO.)

## Options
A. A storage location for the code of your application

B. Using CloudFormation itself is free, including the AWS resources that have been created.

C. Enables modeling, provisioning, and version-controlling of your entire AWS infrastructure

D. Allows you to model your entire infrastructure in a text file

E. Provides highly durable and scalable data storage

---

# Question 4

## Topic
Design High-Performing Architectures

## Question
A company plans to migrate a NoSQL database to an EC2 instance. The database is configured to replicate the data automatically to keep multiple copies of data for redundancy. The Solutions Architect needs to launch an instance that has a high IOPS and sequential read/write access.

Which of the following options fulfills the requirement if I/O throughput is the highest priority?

## Options
A. Use Memory optimized instances with EBS volume.

B. Use Storage optimized instances with instance store volume.

C. Use Compute optimized instance with instance store volume.

D. Use General purpose instances with EBS volume.

---

# Question 5

## Topic
Design High-Performing Architectures

## Question
A leading IT consulting company has an application which processes a large stream of financial data by an Amazon ECS Cluster then stores the result to a DynamoDB table. You have to design a solution to detect new entries in the DynamoDB table then automatically trigger a Lambda function to run some tests to verify the processed data.

What solution can be easily implemented to alert the Lambda function of new entries while requiring minimal configuration change to your architecture?

## Options
A. Use CloudWatch Alarms to trigger the Lambda function whenever a new entry is created in the DynamoDB table.

B. Enable DynamoDB Streams to capture table activity and automatically trigger the Lambda function.

C. Invoke the Lambda functions using SNS each time that the ECS Cluster successfully processed financial data.

D. Use Systems Manager Automation to detect new entries in the DynamoDB table then automatically invoke the Lambda function for processing.

---

# Question 6

## Topic
Design Secure Architectures

## Question
A startup is planning to set up and govern a secure, compliant, multi-account AWS environment in preparation for its upcoming projects. The IT Manager requires the solution to have a dashboard for continuous detection of policy non-conformance and non-compliant resources across the enterprise, as well as to comply with the AWS multi-account strategy best practices.

Which of the following offers the easiest way to fulfill this task?

## Options
A. Launch new AWS member accounts using the AWS CloudFormation StackSets. Use AWS Config to continuously track the configuration changes and set rules to monitor non-compliant resources. Set up a Multi-Account Multi-Region Data Aggregator to monitor compliance data for rules and accounts in an aggregated view

B. Use AWS Control Tower to launch a landing zone to automatically provision and configure new accounts through an Account Factory. Utilize the AWS Control Tower dashboard to monitor provisioned accounts across your enterprise. Set up preventive and detective guardrails for policy enforcement.

C. Use AWS Organizations to build a landing zone to automatically provision new AWS accounts. Utilize the AWS Personal Health Dashboard to see provisioned accounts across your enterprise. Enable preventive and detective guardrails enabled for policy enforcement.

D. Use AWS Service Catalog to launch new AWS member accounts. Configure AWS Service Catalog Launch Constraints to continuously track configuration changes and monitor non-compliant resources. Set up a Multi-Account Multi-Region Data Aggregator to monitor compliance data for rules and accounts in an aggregated view

---

# Question 7

## Topic
Design Resilient Architectures

## Question
Every week, an e-commerce company announces a sales promotion, causing its application hosted on an Auto Scaling group to experience intermittent downtime. Because of long initialization times, the application only becomes operational minutes before a new EC2 instance turns into RUNNING state. A solutions architect must devise a solution that launches capacity in advance based on a forecasted load in order to scale faster.

Which solution meets the requirements with the least amount of effort?

## Options
A. Use Amazon SageMaker Clarify to analyze and predict the workload pattern of the application. Create a scheduled scaling policy based on the prediction results.

B. Create a dynamic scaling policy based on the historical average CPU load of the application.

C. Configure the Auto Scaling group to use predictive scaling.

D. Create a Scheduled Amazon EventBridge (Amazon CloudWatch Events) Rule that runs a scaling job on a Lambda function every midnight.

---

# Question 8

## Topic
Design High-Performing Architectures

## Question
A company has hundreds of VPCs with multiple VPN connections to their data centers spanning 5 AWS Regions. As the number of its workloads grows, the company must be able to scale its networks across multiple accounts and VPCs to keep up. A Solutions Architect is tasked to interconnect all of the company's on-premises networks, VPNs, and VPCs into a single gateway, which includes support for inter-region peering across multiple AWS regions.

Which of the following is the BEST solution that the architect should set up to support the required interconnectivity?

## Options
A. Set up an AWS Transit Gateway in each region to interconnect all networks within it. Then, route traffic between the transit gateways through a peering connection.

B. Set up an AWS Direct Connect Gateway to achieve inter-region VPC access to all of the AWS resources and on-premises data centers. Set up a link aggregation group (LAG) to aggregate multiple connections at a single AWS Direct Connect endpoint in order to treat them as a single, managed connection. Launch a virtual private gateway in each VPC and then create a public virtual interface for each AWS Direct Connect connection to the Direct Connect Gateway.

C. Enable inter-region VPC peering that allows peering relationships to be established between multiple VPCs across different AWS regions. Set up a networking configuration that ensures that the traffic will always stay on the global AWS backbone and never traverse the public Internet.

D. Set up an AWS VPN CloudHub for inter-region VPC access and a Direct Connect gateway for the VPN connections to the on-premises data centers. Create a virtual private gateway in each VPC, then create a private virtual interface for each AWS Direct Connect connection to the Direct Connect gateway.

---

# Question 9

## Topic
Design Secure Architectures

## Question
A company must integrate the Lightweight Directory Access Protocol (LDAP) directory service from the on-premises data center to the AWS VPC using IAM. The identity store which is currently being used is not compatible with SAML.

Which of the following provides the most valid approach to implement the integration?

## Options
A. Use IAM roles to rotate the IAM credentials whenever LDAP credentials are updated.

B. Use AWS IAM Identity Center to manage access between AWS and your LDAP.

C. Use an IAM policy that references the LDAP identifiers and AWS credentials.

D. Develop an on-premises custom identity broker application and use STS to issue short-lived AWS credentials.

---

# Question 10

## Topic
Design Secure Architectures

## Question
A new company policy requires IAM users to change their passwords’ minimum length to 12 characters. After a random inspection, you found out that there are still employees who do not follow the policy.

How can you automatically check and evaluate whether the current password policy for an account complies with the company password policy?

## Options
A. Create a rule in the Amazon CloudWatch event. Build an event pattern to match events on IAM. Set the event name to “ChangePassword” in the event pattern. Configure SNS to send notifications to you whenever a user has made changes to his password.

B. Create a CloudTrail trail. Filter the result by setting the attribute to “Event Name” and lookup value to “ChangePassword”. This easily gives you the list of users who have made changes to their passwords.

C. Create a Scheduled Lambda Function that will run a custom script to check compliance against changes made to the passwords periodically.

D. Configure AWS Config to trigger an evaluation that will check the compliance for a user’s password periodically.

---

# Question 11

## Topic
Design Secure Architectures

## Question
A financial services organization is developing a cloud-native application on AWS to process and analyze customer transaction data. The application utilizes Amazon Aurora for the database, Amazon EFS for file storage, and Amazon EventBridge to trigger AWS Step Functions for workflow orchestration.

The organization has implemented AWS IAM Identity Center for user authentication. The data science, engineering, and compliance teams require secure access to Amazon Aurora and Amazon EFS while maintaining strict data privacy standards. The solution must adhere to the principle of least privilege and minimize administrative overhead.

Which approach best satisfies these requirements?

## Options
A. Enable the IAM Identity Center with an Identity Center directory and create permission sets for granular access for Amazon Aurora and Amazon EFS. Assign teams to groups linked to specific permission sets based on their roles.

B. Use Amazon Cognito User Pools for authentication and use Cognito Identity Pools to provide temporary AWS credentials. Create fine-grained IAM roles for Aurora and EFS access in each team.

C. Set up AWS Control Tower to manage multi-account access. Use Service Control Policies (SCPs) to restrict access to Aurora and EFS at the organizational level. Create IAM roles in each account with specific permissions.

D. Create separate AWS accounts for each team using AWS Organizations. Set up cross-account IAM roles with least privilege and assign specific Aurora and EFS permissions based on team roles.

---

# Question 12

## Topic
Design Secure Architectures

## Question
A company is using an On-Demand EC2 instance to host a legacy web application that uses an Amazon Instance Store-Backed AMI. The web application should be decommissioned as soon as possible and hence, you need to terminate the EC2 instance.

When the instance is terminated, what happens to the data on the root volume?

## Options
A. Data is automatically saved as an EBS snapshot.

B. Data is unavailable until the instance is restarted.

C. Data is automatically saved as an EBS volume.

D. Data is automatically deleted.

---

# Question 13

## Topic
Design Resilient Architectures

## Question
A company deployed an online enrollment system database on a prestigious university, which is hosted in RDS. The Solutions Architect is required to monitor the database metrics in Amazon CloudWatch to ensure the availability of the enrollment system.

What are the enhanced monitoring metrics that Amazon CloudWatch gathers from Amazon RDS DB instances which provide more accurate information? (Select TWO.)

## Options
A. OS processes

B. Database Connections

C. CPU Utilization

D. RDS child processes.

E. Freeable Memory

---

# Question 14

## Topic
Design Secure Architectures

## Question
A company decided to change its third-party data analytics tool to a cheaper solution. They sent a full data export on a CSV file which contains all of their analytics information. You then save the CSV file to an S3 bucket for storage. Your manager asked you to do some validation on the provided data export.

In this scenario, what is the most cost-effective and easiest way to analyze export data using standard SQL?

## Options
A. Create a migration tool to load the CSV export file from S3 to a DynamoDB instance. Once the data has been loaded, run queries using DynamoDB.

B. To be able to run SQL queries, use AWS Athena to analyze the export data file in S3.

C. Use mysqldump client utility to load the CSV export file from S3 to a MySQL RDS instance. Run some SQL queries once the data has been loaded to complete your validation.

D. Use a migration tool to load the CSV export file from S3 to a database that is designed for online analytic processing (OLAP) such as AWS RedShift. Run some queries once the data has been loaded to complete your validation.

---

# Question 15

## Topic
Design Secure Architectures

## Question
A media company needs to configure an Amazon S3 bucket to serve static assets for the public-facing web application. Which methods ensure that all of the objects uploaded to the S3 bucket can be read publicly all over the Internet? (Select TWO.)

## Options
A. Grant public read access to the object when uploading it using the S3 Console.

B. Configure the cross-origin resource sharing (CORS) of the S3 bucket to allow objects to be publicly accessible from all domains.

C. Create an IAM role to set the objects inside the S3 bucket to public read.

D. Do nothing. Amazon S3 objects are already public by default.

E. Configure the S3 bucket policy to set all objects to public read.

---

# Question 16

## Topic
Design Secure Architectures

## Question
A Solutions Architect is designing a monitoring application which generates audit logs of all operational activities of the company's cloud infrastructure. Their IT Security and Compliance team mandates that the application retain the logs for 5 years before the data can be deleted.

How can the Architect meet the above requirement?

## Options
A. Store the audit logs in an EFS volume and use Network File System version 4 (NFSv4) file-locking mechanism.

B. Store the audit logs in an Amazon S3 bucket and enable Multi-Factor Authentication Delete (MFA Delete) on the S3 bucket.

C. Store the audit logs in a Glacier vault and use the Vault Lock feature.

D. Store the audit logs in an EBS volume and then take EBS snapshots every month.

---

# Question 17

## Topic
Design Cost-Optimized Architectures

## Question
A media company is using Amazon EC2, ELB, and S3 for its video-sharing portal for filmmakers. They are using a standard S3 storage class to store all high-quality videos that are frequently accessed only during the first three months of posting.

As a Solutions Architect, what should you do if the company needs to automatically transfer or archive media data from an S3 bucket to Glacier?

## Options
A. Use Lifecycle Policies

B. Use Amazon SWF

C. Use a custom shell script that transfers data from the S3 bucket to Glacier

D. Use Amazon SQS

---

# Question 18

## Topic
Design High-Performing Architectures

## Question
A company has a High Performance Computing (HPC) cluster that is composed of EC2 Instances with Provisioned IOPS (io1) volume to process transaction-intensive, low-latency workloads. The Solutions Architect must maintain high IOPS while keeping the latency down by setting the optimal queue length for the volume. The size of each volume is 10 GiB.

Which of the following is the MOST suitable configuration that the Architect should set up?

## Options
A. Set the IOPS to 800 then maintain a low queue length.

B. Set the IOPS to 600 then maintain a high queue length.

C. Set the IOPS to 400 then maintain a low queue length.

D. Set the IOPS to 500 then maintain a low queue length.

---

# Question 19

## Topic
Design High-Performing Architectures

## Question
A Solutions Architect is designing the cloud architecture for the enterprise application suite of the company. Both the web and application tiers need to access the Internet to fetch data from public APIs. However, these servers should be inaccessible from the Internet.

Which of the following steps should the Architect implement to meet the above requirements?

## Options
A. Deploy a NAT gateway in the public subnet and add a route to it from the private subnet where the web and application tiers are hosted.

B. Deploy a NAT gateway in the private subnet and add a route to it from the public subnet where the web and application tiers are hosted.

C. Deploy the web and application tier instances to a private subnet and then allocate an Elastic IP address to each EC2 instance.

D. Deploy the web and application tier instances to a public subnet and then allocate an Elastic IP address to each EC2 instance.

---

# Question 20

## Topic
Design Resilient Architectures

## Question
A company launched an EC2 instance in the newly created VPC. They noticed that the generated instance does not have an associated DNS hostname.

Which of the following options could be a valid reason for this issue?

## Options
A. The newly created VPC has an invalid CIDR block.

B. Amazon Route53 is not enabled.

C. The DNS resolution and DNS hostname of the VPC configuration should be enabled.

D. The security group of the EC2 instance needs to be modified.

---

# Question 21

## Topic
Design Cost-Optimized Architectures

## Question
A company conducts performance testing on a large instance MySQL RDS DB instance twice a week. They use Performance Insights to analyze and fine-tune expensive queries. The company needs to reduce its operational expenses in running the tests without compromising the tests' integrity.

Which of the following is the most cost-effective solution?

## Options
A. Perform a mysqldump to get a copy of the database on a local machine. Use MySQL Workbench to analyze the queries.

B. Downgrade the database to a smaller instance.

C. Stop the database once the test is done and restart it only when necessary.

D. Once the testing is completed, take a snapshot of the database and terminate it. Restore the database from the snapshot when necessary.

---

# Question 22

## Topic
Design Resilient Architectures

## Question
A real-time data analytics application is using AWS Lambda to process data and store results in JSON format to an S3 bucket. To speed up the existing workflow, you have to use a service where you can run sophisticated Big Data analytics on your data without moving them into a separate analytics system.

Which of the following group of services can you use to meet this requirement?

## Options
A. Amazon Glue, Amazon Redshift, Amazon S3

B. Amazon Neptune, DynamoDB DAX, Amazon Redshift Spectrum

C. Amazon X-Ray, Amazon Neptune, DynamoDB

D. Amazon Athena, Amazon Redshift Spectrum, AWS Glue

---

# Question 23

## Topic
Design Secure Architectures

## Question
A company has a regional API Gateway in the us-east-2 region that serves as a proxy to a backend service. Clients connect to the service using the invoke URL of the API stage. To improve usability, the company wants to associate a custom domain name (api.tutorialsdojo.com) with the API. Moreover, the domain name must support HTTPS to ensure secure connections. The company has an existing hosted zone for its domain on Amazon Route 53.

Which of the following would be the next step to achieve the company's objective?

## Options
A. Import an existing public certificate for api.tutorialsdojo.com into AWS Certificate Manager (ACM) in the us-east-2. In Route 53, create a CNAME record for api.tutorialsdojo.com that points to the invoke URL of the API Gateway stage.

B. Request a public certificate in the us-east-1 region for api.tutorialsdojo.com using AWS Certificate Manager (ACM). Create a regional API Gateway domain name and associate it with api.tutorialsdojo.com and the ACM certificate. In Route 53, create an alias record for api.tutorialsdojo.com that points to the API Gateway domain name.

C. Request a public certificate in the us-east-2 region for api.tutorialsdojo.com using AWS Certificate Manager (ACM). Create a regional API Gateway domain name and associate it with api.tutorialsdojo.com and the ACM certificate. In Route 53, create an alias record for api.tutorialsdojo.com that points to the API Gateway domain name.

D. Use the AWS Certificate Manager Private Certificate Authority (ACM PCA) to generate a private certificate for api.tutorialsdojo.com. Override the invoke URL using stage variables.

---

# Question 24

## Topic
Design High-Performing Architectures

## Question
A company has a team of developers that provisions its own resources on the AWS cloud. The developers use IAM user access keys to automate resource provisioning and application testing processes in AWS. To ensure proper security compliance, the security team wants to automate the process of deactivating and deleting any IAM user access key that is over 90 days old.

Which solution will meet these requirements with the LEAST operational effort?

## Options
A. Use the AWS Config managed rule to check if the IAM user access keys are not rotated within 90 days. Create an Amazon EventBridge rule for the non-compliant keys, and define a target to invoke a custom AWS Lambda function to deactivate and delete the keys.

B. Create an Amazon EventBridge rule to filter IAM user access keys older than 90 days. Schedule an AWS Batch job that runs every 24 hours to delete all the specified access keys.

C. Create a custom AWS Config rule to check the max-age of IAM access keys. Use Amazon EventBridge Scheduler to invoke an AWS Batch job every 24 hours to delete all non-compliant access keys.

D. Create an Amazon EventBridge rule to filter IAM user access keys older than 90 days. Define a target to invoke an AWS Lambda function to deactivate and delete the old access keys.

---

# Question 25

## Topic
Design Resilient Architectures

## Question
A Solutions Architect is designing a setup for a database that will run on Amazon RDS for MySQL. He needs to ensure that the database can automatically failover to an RDS instance to continue operating in the event of failure. The architecture should also be as highly available as possible.

Which among the following actions should the Solutions Architect do?

## Options
A. Create a standby replica in another availability zone by enabling Multi-AZ deployment.

B. Create five read replicas across different availability zones. In the event of an Availability Zone outage, promote any replica to become the primary instance.

C. Create five cross-region read replicas in each region. In the event of an Availability Zone outage, promote any replica to become the primary instance.

D. Create a read replica in the same region where the DB instance resides. In addition, create a read replica in a different region to survive a region’s failure. In the event of an Availability Zone outage, promote any replica to become the primary instance.

---

# Question 26

## Topic
Design Resilient Architectures

## Question
A solutions architect is tasked with designing a scalable infrastructure solution for a business that runs uses Amazon Elastic Kubernetes Service (Amazon EKS) to execute container applications. Since the company's workload varies throughout the day, they want to make sure that its underlying infrastructure automatically scales in and out in response to demand.

Which of the following would meet the requirements with the LEAST amount of operational overhead?

## Options
A. Integrate an edge-optimized API endpoint in Amazon API Gateway with Amazon EKS to manage and expose APIs for the containerized applications running on EKS.

B. Set up CloudWatch alarms for CPU utilization or request count to monitor the relevant metrics of the container applications running on Amazon EKS.

C. Use Amazon EC2 Auto Scaling Groups with custom scaling policies to manage the scaling of EKS worker nodes.

D. Use a combination of Kubernetes Metrics and Kubernetes Cluster Autoscaler to manage the number of nodes.

---

# Question 27

## Topic
Design High-Performing Architectures

## Question
A popular augmented reality (AR) mobile game is heavily using a RESTful API which is hosted in AWS. The API uses Amazon API Gateway and a DynamoDB table with a preconfigured read and write capacity. Based on your systems monitoring, the DynamoDB table begins to throttle requests during high peak loads which causes the slow performance of the game.

Which of the following can you do to improve the performance of your app?

## Options
A. Integrate an Application Load Balancer with your DynamoDB table.

B. Use DynamoDB Auto Scaling

C. Add the DynamoDB table to an Auto Scaling Group.

D. Create an SQS queue in front of the DynamoDB table.

---

# Question 28

## Topic
Design Resilient Architectures

## Question
A company has a web application hosted in AWS cloud where the application logs are sent to Amazon CloudWatch. Lately, the web application has been encountering some errors which can be resolved simply by restarting the instance.

What will you do to automatically restart the EC2 instances whenever the same application error occurs?

## Options
A. First, look at the existing CloudWatch logs for keywords related to the application error to create a custom metric. Then, create an alarm in Amazon SNS for that custom metric which invokes an action to restart the EC2 instance.

B. First, look at the existing Flow logs for keywords related to the application error to create a custom metric. Then, create a CloudWatch alarm for that custom metric which calls a Lambda function that invokes an action to restart the EC2 instance.

C. First, look at the existing Flow logs for keywords related to the application error to create a custom metric. Then, create a CloudWatch alarm for that custom metric which invokes an action to restart the EC2 instance.

D. First, look at the existing CloudWatch logs for keywords related to the application error to create a custom metric. Then, create a CloudWatch alarm for that custom metric which invokes an action to restart the EC2 instance.

---

# Question 29

## Topic
Design High-Performing Architectures

## Question
A company has a web-based order processing system that is currently using a standard queue in Amazon SQS. The IT Manager noticed that there are a lot of cases where an order was processed twice. This issue has caused a lot of trouble in processing and made the customers very unhappy. The goal is to ensure that this issue will not recur.

What solution should be implemented to prevent this from happening again in the future?

## Options
A. Use an SQS FIFO Queue instead.

B. Alter the retention period in SQS.

C. Change the message size in SQS.

D. Alter the visibility timeout of SQS.

---

# Question 30

## Topic
Design Resilient Architectures

## Question
A company has a fixed set of Amazon EC2 instances inside a VPC in the AWS cloud. The instances run a mission-critical application. In a recent incident, one of the EC2 instances suddenly powered down which affected the availability of the application. To avoid this incident in the future, the management wants to get notified of any upcoming AWS events that may affect these EC2 instances.

Which of the following options is the recommended action to meet the above requirements?

## Options
A. Create an Amazon EventBridge (Amazon CloudWatch Events) rule that is scheduled to run every 24 hours. Set the target to an AWS Lambda function that will check AWS Service Health Dashboard and send notifications for any events that may affect Amazon EC2 instances.

B. Set up an Amazon EventBridge (Amazon CloudWatch Events) rule to check for AWS Service Health Dashboard events that are related to Amazon EC2 instances. To send notifications, set an Amazon SNS topic as a target for the rule.

C. Create an Amazon EventBridge (Amazon CloudWatch Events) rule to check for AWS Personal Health Dashboard events that are related to Amazon EC2 instances. To send notifications, set an Amazon SNS topic as a target for the rule.

D. Set up an Amazon EventBridge (Amazon CloudWatch Events) rule to check for any status change for Amazon EC2 instances. Set the target to an AWS Lambda function that will send a notification and restart the affected Amazon EC2 instances.

---

# Question 31

## Topic
Design High-Performing Architectures

## Question
A company hosts all its applications on its data center on the US East Coast. Most of the workloads are legacy applications that are hosted on individual virtual machines running in Linux and Windows operating systems. The company plans to migrate all of its VM workloads to the AWS cloud. To minimize changes in the applications during the migration process, it has been decided that the company will use a “lift-and-shift” strategy. The company also wants to minimize downtime during the migration process.

Which of the following options should the Solutions Architect implement for this scenario?

## Options
A. Utilize AWS DataSync to migrate the application workloads to AWS. Deploy the AWS DataSync VM on the on-premises data center. Once replication is completed, launch Amazon EC2 instances based on the created AMIs.

B. Export the on-premises VMs and upload the images to an Amazon S3 bucket. Use VM Import/Export service to import the images and launch them as Amazon EC2 instances.

C. Install the AWS Replication Agent on each of the on-premises VMs to continuously replicate the servers to AWS. Use AWS Migration Service (AWS MGN) to launch test instances and perform cutover once testing is completed.

D. Use the AWS Application Discovery Service for lift-and-shift migrations. Deploy the AWS Application Discovery Agent to the on-premises data center to start the replication process. After the replication task is completed, launch Amazon EC2 instances based on the created AMIs.

---

# Question 32

## Topic
Design High-Performing Architectures

## Question
A company has an OLTP (Online Transactional Processing) application that is hosted in an Amazon ECS cluster using the Fargate launch type. It has an Amazon RDS database that stores data of its production website. The Data Analytics team needs to run queries against the database to track and audit all user transactions. These query operations against the production database must not impact application performance in any way.

Which of the following is the MOST suitable and cost-effective solution that you should implement?

## Options
A. Upgrade the instance type of the RDS database to a large instance.

B. Set up a new Amazon RDS Read Replica of the production database. Direct the Data Analytics team to query the production data from the replica.

C. Set up a Multi-AZ deployments configuration of your production database in RDS. Direct the Data Analytics team to query the production data from the standby instance.

D. Set up a new Amazon Redshift database cluster. Migrate the product database into Redshift and allow the Data Analytics team to fetch data from it.

---

# Question 33

## Topic
Design Cost-Optimized Architectures

## Question
A company is looking to store its confidential financial files in AWS, which are accessed every week. The Architect was instructed to set up the storage system, which uses envelope encryption and automates key rotation. It should also provide an audit trail that shows who used the encryption key and by whom for security purposes.

Which combination of actions should the Architect implement to satisfy the requirement in the most cost-effective way? (Select TWO.)

## Options
A. Configure Server-Side Encryption with Amazon S3-Managed Keys (SSE-S3).

B. Configure Server-Side Encryption with AWS KMS Keys (SSE-KMS).

C. Use Amazon S3 Glacier Deep Archive to store the data.

D. Use Amazon S3 to store the data.

E. Configure Server-Side Encryption with Customer-Provided Keys (SSE-C).

---

# Question 34

## Topic
Design Secure Architectures

## Question
A food company bought 50 licenses of Windows Server to be used by the developers when launching Amazon EC2 instances to deploy and test applications. The developers are free to provision EC2 instances as long as there is a license available. The licenses are tied to the total CPU count of each virtual machine. The company wants to ensure that developers won’t be able to launch new instances once the licenses are exhausted. The company wants to receive notifications when all licenses are in use.

Which of the following options is the recommended solution to meet the company's requirements?

## Options
A. Upload the licenses on AWS Systems Manager Fleet Manager to be encrypted and distributed to Amazon EC2 instances. Attach an IAM role on the EC2 instances to request a license from the Fleet Manager. Set up an Amazon SNS to send notifications and alerts once all licenses are used

B. Define license configuration rules on AWS Certificate Manager to track and control license usage. Enable the option to “Enforce certificate limit” to prevent going over the number of allocated licenses. Add an Amazon SQS queue with ChangeVisibility Timeout configured to send notifications and alerts.

C. Define licensing rules on AWS License Manager to track and control license usage. Enable the option to “Enforce license limit” to prevent going over the number of allocated licenses. Add an Amazon SNS topic to send notifications and alerts.

D. Configure AWS Resource Access Manager (AWS RAM) to track and control the licenses used by AWS resources. Configure AWS RAM to provide available licenses for Amazon EC2 instances. Set up an Amazon SNS to send notifications and alerts once all licenses are used.

---

# Question 35

## Topic
Design Cost-Optimized Architectures

## Question
There are a few, easily reproducible but confidential files that your client wants to store in AWS without worrying about storage capacity. For the first month, all of these files will be accessed frequently but after that, they will rarely be accessed at all. The old files will only be accessed by developers so there is no set retrieval time requirement. However, the files under a specific tdojo-finance prefix in the S3 bucket will be used for post-processing that requires millisecond retrieval time.

Given these conditions, which of the following options would be the most cost-effective solution for your client's storage needs?

## Options
A. Store the files in S3 then after a month, change the storage class of the bucket to Intelligent-Tiering using lifecycle policy.

B. Store the files in S3 then after a month, change the storage class of the tdojo-finance prefix to S3-IA while the remaining go to Glacier using lifecycle policy.

C. Store the files in S3 then after a month, change the storage class of the bucket to S3-IA using lifecycle policy.

D. Store the files in S3 then after a month, change the storage class of the tdojo-finance prefix to One Zone-IA while the remaining go to Glacier using lifecycle policy.

---

# Question 36

## Topic
Design High-Performing Architectures

## Question
An automotive company is working on an autonomous vehicle development and deployment project using AWS. The solution requires High Performance Computing (HPC) in order to collect, store and manage massive amounts of data as well as to support deep learning frameworks. The Linux EC2 instances that will be used should have a lower latency and higher throughput than the TCP transport traditionally used in cloud-based HPC systems. It should also enhance the performance of inter-instance communication and must include an OS-bypass functionality to allow the HPC to communicate directly with the network interface hardware to provide low-latency, reliable transport functionality.

Which of the following is the MOST suitable solution that you should implement to achieve the above requirements?

## Options
A. Attach an Elastic Network Interface (ENI) on each Amazon EC2 instance to accelerate High Performance Computing (HPC).

B. Attach an Elastic Fabric Adapter (EFA) on each Amazon EC2 instance to accelerate High Performance Computing (HPC).

C. Attach an Elastic Network Adapter (ENA) on each Amazon EC2 instance to accelerate High Performance Computing (HPC).

D. Attach a Private Virtual Interface (VIF) on each Amazon EC2 instance to accelerate High Performance Computing (HPC).

---

# Question 37

## Topic
Design High-Performing Architectures

## Question
A company launched a global news website that is deployed to AWS and is using MySQL RDS. The website has millions of viewers from all over the world, which means that the website has a read-heavy database workload. All database transactions must be ACID compliant to ensure data integrity.

In this scenario, which of the following is the best option to use to increase the read-throughput on the MySQL database?

## Options
A. Enable Multi-AZ deployments

B. Enable Amazon RDS Standby Replicas

C. Use SQS to queue up the requests

D. Enable Amazon RDS Read Replicas

---

# Question 38

## Topic
Design High-Performing Architectures

## Question
There is a new compliance rule in your company that audits every Windows and Linux EC2 instances each month to view any performance issues. They have more than a hundred EC2 instances running in production, and each must have a logging function that collects various system details regarding that instance. The SysOps team will periodically review these logs and analyze their contents using AWS Analytics tools, and the result will need to be retained in an S3 bucket.

In this scenario, what is the most efficient way to collect and analyze logs from the instances with minimal effort?

## Options
A. Install AWS Inspector Agent in each instance which will collect and push data to CloudWatch Logs periodically. Set up a CloudWatch dashboard to properly analyze the log data of all instances.

B. Install the AWS Systems Manager Agent (SSM Agent) in each instance which will automatically collect and push data to CloudWatch Logs. Analyze the log data with CloudWatch Logs Insights.

C. Install the unified CloudWatch Logs agent in each instance which will automatically collect and push data to CloudWatch Logs. Analyze the log data with CloudWatch Logs Insights.

D. Install AWS SDK in each instance and create a custom daemon script that would collect and push data to CloudWatch Logs periodically. Enable CloudWatch detailed monitoring and use CloudWatch Logs Insights to analyze the log data of all instances.

---

# Question 39

## Topic
Design Secure Architectures

## Question
A company has several web applications with users all around the world. Each application is hosted in an Auto Scaling group of EC2 instances in multiple AZs behind an Application Load Balancer (ALB). All applications have their own fully qualified domain name. For added security, the applications must use a publicly trusted SSL certificate.

Which solution will meet this requirement with the LEAST operational overhead?

## Options
A. Launch a self-hosted certificate authority (CA) using the Let's Encrypt tool in an Amazon EC2 instance. Utilize the built-in ISRG Root X1 trusted root CA certificate. Generate a new SSL/TLS certificate using the certbot CLI utility. Associate the new certificate on the HTTPS listener of the ALBs.

B. Issue an SSL/TLS certificate using the AWS Certificate Manager Private Certificate Authority. Associate the new certificate on the HTTPS listener of the ALBs.

C. Use OpenSSL to generate a self-signed certificate. Import the SSL/TLS certificate to the AWS Certificate Manager (ACM) and associate it with the HTTPS listener of the ALBs

D. Use the AWS Certificate Manager (ACM) to generate a public SSL/TLS certificate. Associate the new SSL/TLS certificate on the HTTPS listener of the ALBs.

---

# Question 40

## Topic
Design Resilient Architectures

## Question
A newly hired Solutions Architect is checking all of the security groups and network access control list rules of the company's AWS resources. For security purposes, the MS SQL connection via port 1433 of the database tier should be secured. Below is the security group configuration of their Microsoft SQL Server database:

The application tier hosted in an Auto Scaling group of EC2 instances is the only identified resource that needs to connect to the database. The Architect should ensure that the architecture complies with the best practice of granting least privilege.

Which of the following changes should be made to the security group configuration?

## Options
A. For the MS SQL rule, change the Source to the EC2 instance IDs of the underlying instances of the Auto Scaling group.

B. For the MS SQL rule, change the Source to the Network ACL ID attached to the application tier.

C. For the MS SQL rule, change the Source to the static AnyCast IP address attached to the application tier.

D. For the MS SQL rule, change the Source to the security group ID attached to the application tier.

---

# Question 41

## Topic
Design High-Performing Architectures

## Question
A company needs to implement a solution that will process real-time streaming data of its users across the globe. This will enable them to track and analyze globally-distributed user activity on their website and mobile applications, including clickstream analysis. The solution should process the data in close geographical proximity to their users and respond to user requests at low latencies.

Which of the following is the most suitable solution for this scenario?

## Options
A. Integrate CloudFront with Lambda@Edge in order to process the data in close geographical proximity to users and respond to user requests at low latencies. Process real-time streaming data using Kinesis and durably store the results to an Amazon S3 bucket.

B. Integrate CloudFront with Lambda@Edge in order to process the data in close geographical proximity to users and respond to user requests at low latencies. Process real-time streaming data using Amazon Athena and durably store the results to an Amazon S3 bucket.

C. Use a CloudFront web distribution and Route 53 with a Geoproximity routing policy in order to process the data in close geographical proximity to users and respond to user requests at low latencies. Process real-time streaming data using Kinesis and durably store the results to an Amazon S3 bucket.

D. Use a CloudFront web distribution and Route 53 with a latency-based routing policy, in order to process the data in close geographical proximity to users and respond to user requests at low latencies. Process real-time streaming data using Kinesis and durably store the results to an Amazon S3 bucket.

---

# Question 42

## Topic
Design High-Performing Architectures

## Question
An organization plans to use an AWS Direct Connect connection to establish a dedicated connection between its on-premises network and AWS. The organization needs to launch a fully managed solution that will automate and accelerate the replication of data to and from various AWS storage services.

Which of the following solutions would you recommend?

## Options
A. Use an AWS Storage Gateway tape gateway to store data on virtual tape cartridges and asynchronously copy your backups to AWS.

B. Use an AWS DataSync agent to rapidly move the data over a service endpoint.

C. Use an AWS DataSync agent to rapidly move the data over the Internet.

D. Use an AWS Storage Gateway file gateway to store and retrieve files directly using the SMB file system protocol.

---

# Question 43

## Topic
Design Secure Architectures

## Question
A company is using the AWS Directory Service to integrate their on-premises Microsoft Active Directory (AD) domain with their Amazon EC2 instances via an AD connector. The below identity-based policy is attached to the IAM Identities that use the AWS Directory service:

{

"Version":"2012-10-17",

"Statement":[

{

"Sid":"DirectoryTutorialsDojo1234",

"Effect":"Allow",

"Action":[

"ds:*"

],

"Resource":"arn:aws:ds:us-east-1:987654321012:directory/d-1234567890"

},

{

"Effect":"Allow",

"Action":[

"ec2:*"

],

"Resource":"*"

}

]

}

Which of the following BEST describes what the above resource policy does?

## Options
A. Allows all AWS Directory Service (ds) calls as long as the resource contains the directory ID:  987654321012

B. Allows all AWS Directory Service (ds) calls as long as the resource contains the directory ID: DirectoryTutorialsDojo1234

C. Allows all AWS Directory Service (ds) calls as long as the resource contains the directory name of: DirectoryTutorialsDojo1234

D. Allows all AWS Directory Service (ds) calls as long as the resource contains the directory ID: d-1234567890

---

# Question 44

## Topic
Design Resilient Architectures

## Question
A tech company currently has an on-premises infrastructure. They are currently running low on storage and want to have the ability to extend their storage using the AWS cloud.

Which AWS service can help them achieve this requirement?

## Options
A. Amazon SQS

B. Amazon Elastic Block Storage

C. Amazon EC2

D. AWS Storage Gateway

---

# Question 45

## Topic
Design Resilient Architectures

## Question
A company recently launched an e-commerce application that is running in eu-east-2 region, which strictly requires six EC2 instances running at all times. In that region, there are 3 Availability Zones (AZ) that you can use - eu-east-2a, eu-east-2b, and eu-east-2c.

Which of the following deployments provide 100% fault tolerance if any single AZ in the region becomes unavailable? (Select TWO.)

## Options
A. eu-east-2a with three EC2 instances, eu-east-2b with three EC2 instances, and eu-east-2c with three EC2 instances

B. eu-east-2a with two EC2 instances, eu-east-2b with two EC2 instances, and eu-east-2c with two EC2 instances

C. eu-east-2a with six EC2 instances, eu-east-2b with six EC2 instances, and eu-east-2c with no EC2 instances

D. eu-east-2a with four EC2 instances, eu-east-2b with two EC2 instances, and eu-east-2c with two EC2 instances

E. eu-east-2a with two EC2 instances, eu-east-2b with four EC2 instances, and eu-east-2c with two EC2 instances

---

# Question 46

## Topic
Design High-Performing Architectures

## Question
A startup plans to develop a multiplayer game that uses UDP as the protocol for communication between clients and game servers. The data of the users will be stored in a key-value store. As the Solutions Architect, you need to implement a solution that will distribute the traffic across a number of servers.

Which of the following could help you achieve this requirement?

## Options
A. Distribute the traffic using Application Load Balancer and store the data in Amazon RDS.

B. Distribute the traffic using Network Load Balancer and store the data in Amazon DynamoDB.

C. Distribute the traffic using Network Load Balancer and store the data in Amazon Aurora.

D. Distribute the traffic using Application Load Balancer and store the data in Amazon DynamoDB.

---

# Question 47

## Topic
Design Resilient Architectures

## Question
A data analytics company, which uses machine learning to collect and analyze consumer data, is using Redshift cluster as their data warehouse. You are instructed to implement a disaster recovery plan for their systems to ensure business continuity even in the event of an AWS region outage.

Which of the following is the best approach to meet this requirement?

## Options
A. Enable Cross-Region Snapshots Copy in your Amazon Redshift Cluster.

B. Do nothing because Amazon Redshift is a highly available, fully-managed data warehouse which can withstand an outage of an entire AWS region.

C. Use Automated snapshots of your Redshift Cluster.

D. Create a scheduled job that will automatically take the snapshot of your Redshift Cluster and store it to an S3 bucket. Restore the snapshot in case of an AWS region outage.

---

# Question 48

## Topic
Design Resilient Architectures

## Question
A company has a set of Linux servers running on multiple On-Demand EC2 Instances. The Audit team wants to collect and process the application log files generated from these servers for their report.

Which of the following services is best to use in this case?

## Options
A. Amazon S3 for storing the application log files and Amazon Elastic MapReduce for processing the log files.

B. A single On-Demand Amazon EC2 instance for both storing and processing the log files

C. Amazon S3 Glacier Deep Archive for storing the application log files and AWS ParallelCluster for processing the log files.

D. Amazon S3 Glacier for storing the application log files and Spot EC2 Instances for processing them.

---

# Question 49

## Topic
Design High-Performing Architectures

## Question
A technical lead of the Cloud Infrastructure team was consulted by a software developer regarding the required AWS resources of the web application that he is building. The developer knows that an Instance Store only provides ephemeral storage where the data is automatically deleted when the instance is terminated. To ensure that the data of the web application persists, the app should be launched in an EC2 instance that has a durable, block-level storage volume attached. The developer knows that they need to use an EBS volume, but they are not sure what type they need to use.

In this scenario, which of the following is true about Amazon EBS volume types and their respective usage? (Select TWO.)

## Options
A. Provisioned IOPS volumes offer storage with consistent and low-latency performance, and are designed for I/O intensive applications such as large relational or NoSQL databases.

B. Spot volumes provide the lowest cost per gigabyte of all EBS volume types and are ideal for workloads where data is accessed infrequently, and applications where the lowest storage cost is important.

C. Single root I/O virtualization (SR-IOV) volumes are suitable for a broad range of workloads, including small to medium-sized databases, development and test environments, and boot volumes.

D. General Purpose SSD (gp3) volumes with multi-attach enabled offer consistent and low-latency performance, and are designed for applications requiring multi-az resiliency.

E. Magnetic volumes provide the lowest cost per gigabyte of all EBS volume types and are ideal for workloads where data is accessed infrequently, and applications where the lowest storage cost is important.

---

# Question 50

## Topic
Design Secure Architectures

## Question
A multinational bank is storing its confidential files in an S3 bucket. The security team recently performed an audit, and the report shows that multiple files have been uploaded without 256-bit Advanced Encryption Standard (AES) server-side encryption. For added protection, the encryption key must be automatically rotated every year. The solutions architect must ensure that there would be no other unencrypted files uploaded in the S3 bucket in the future.

Which of the following will meet these requirements with the LEAST operational overhead?

## Options
A. Create a Service Control Policy (SCP) for the S3 bucket that rejects any object uploads unless the request includes the s3:x-amz-server-side-encryption": "AES256" header. Enable server-side encryption with Amazon S3-managed encryption keys (SSE-S3) and modify the built-in key rotation feature of the SSE-S3 encryption keys to rotate the key yearly.

B. Create an S3 bucket policy that denies permissions to upload an object unless the request includes the s3:x-amz-server-side-encryption": "AES256" header. Enable server-side encryption with Amazon S3-managed encryption keys (SSE-S3) and rely on the built-in key rotation feature of the SSE-S3 encryption keys.

C. Create an S3 bucket policy for the S3 bucket that rejects any object uploads unless the request includes the s3:x-amz-server-side-encryption":"aws:kms" header. Enable the S3 Object Lock in compliance mode for all objects to automatically rotate the built-in AES256 customer-managed key of the bucket.

D. Create a new customer-managed key from the AWS Key Management Service (AWS KMS). Configure the default encryption behavior of the bucket to use the customer-managed key. Manually rotate the KMS key and every year.

---

# Question 51

## Topic
Design Secure Architectures

## Question
A Solutions Architect is working for a large global media company with multiple office locations all around the world. The Architect is instructed to build a system to distribute training videos to all employees.

Using Amazon CloudFront, what method would be used to serve content that is stored in Amazon S3 but not publicly accessible from S3 directly?

## Options
A. Create an Identity and Access Management (IAM) user for CloudFront and grant access to the objects in your S3 bucket to that IAM user.

B. Create an S3 bucket policy that lists the CloudFront distribution ID as the principal and the target bucket as the Amazon Resource Name (ARN).

C. Create an Origin Access Control (OAC) for CloudFront and grant access to the objects in your S3 bucket to that OAC.

D. Create a web ACL in AWS WAF to block any public S3 access and attach it to the CloudFront distribution.

---

# Question 52

## Topic
Design Secure Architectures

## Question
An online survey startup is collecting real estate data in the United States for several years. The startup already has a total of 5 TB of data stored in an Amazon S3 bucket located in the us-east-1 Region. All real estate data must be shared with a European AWS Managed Service Provider (MSP) Partner which also uses Amazon S3 for storage. Due to budget constraints, the startup must keep its data transfer costs in S3 as low as possible and disable anonymous access.

Which solution meets this requirement MOST cost-effectively?

## Options
A. Enable cross-account access of the startup’s S3 bucket to allow the data downloads and exclusive access from the partner’s AWS account

B. Enable the Requester Pays feature on the Amazon S3 bucket to lower data transfer costs and disable anonymous access

C. Enable S3 Object Lock in governance mode to lower data transfer costs and set a Legal Hold for each object to disable anonymous access

D. Enable Cross-Region Replication(CRR) on the startup’s S3 bucket to automatically copy the S3 content to the partner’s S3 bucket in Europe.

---

# Question 53

## Topic
Design Resilient Architectures

## Question
A financial firm is designing an application architecture for its online trading platform that must have high availability and fault tolerance. Their Solutions Architect configured the application to use an Amazon S3 bucket located in the us-east-1 region to store large amounts of intraday financial data. The stored financial data in the bucket must not be affected even if there is an outage in one of the Availability Zones or if there's a regional service failure.

What should the Architect do to avoid any costly service disruptions and ensure data durability?

## Options
A. Create a new S3 bucket in another region and configure Cross-Account Access to the bucket located in us-east-1.

B. Copy the S3 bucket to an EBS-backed EC2 instance.

C. Create a Lifecycle Policy to regularly backup the S3 bucket to Amazon Glacier.

D. Enable Cross-Region Replication.

---

# Question 54

## Topic
Design High-Performing Architectures

## Question
An Auto Scaling group (ASG) of Amazon EC2 Linux instances has an Amazon FSx for OpenZFS file system with basic monitoring enabled in Amazon CloudWatch. The Solutions Architect noticed that the legacy web application hosted in the ASG takes a long time to load. After checking the instances, the Architect noticed that the ASG is not launching more instances as it should be, even though the servers already have high memory usage.

Which of the following options should the Architect implement to solve this issue?

## Options
A. Install the CloudWatch unified agent to the EC2 instances. Set up a custom parameter in AWS Systems Manager Parameter Store with the CloudWatch agent configuration to create an aggregated metric on memory usage percentage. Scale the Auto Scaling group based on the aggregated metric.

B. Set up Amazon Rekognition to automatically identify and recognize the cause of the high memory usage. Use the AWS Well-Architected Tool to automatically trigger the scale-out event in the ASG based on the overall memory usage.

C. Enable detailed monitoring on the EC2 instances of the Auto Scaling group. Use Auto Scaling with custom metrics to scale out the Auto Scaling group based on the aggregated memory usage of EC2 instances.

D. Implement an AI solution that leverages Amazon Comprehend to track the near-real-time memory usage of each and every EC2 instance. Use Amazon SageMaker AI to automatically trigger the Auto Scaling event if there is high memory usage.

---

# Question 55

## Topic
Design Resilient Architectures

## Question
A company has a web application hosted in an On-Demand EC2 instance. You are creating a shell script that needs the instance's public and private IP addresses.

What is the best way to get the instance's associated IP addresses which your shell script can use?

## Options
A. By using a Curl or Get Command to get the latest metadata information from http://169.254.169.254/latest/meta-data/

B. By using IAM.

C. By using a CloudWatch metric.

D. By using a Curl or Get Command to get the latest user data information from http://169.254.169.254/latest/user-data/

---

# Question 56

## Topic
Design Cost-Optimized Architectures

## Question
To save costs, your manager instructed you to analyze and review the setup of your AWS cloud infrastructure. You should also provide an estimate of how much your company will pay for all of the AWS resources that they are using. In this scenario, which of the following will incur costs? (Select TWO.)

## Options
A. Using an Amazon VPC

B. A stopped On-Demand EC2 Instance

C. EBS Volumes attached to stopped EC2 Instances

D. Public Data Set

E. A running EC2 Instance

---

# Question 57

## Topic
Design Cost-Optimized Architectures

## Question
A web application is hosted in an Auto Scaling group of EC2 instances deployed across multiple Availability Zones behind an Application Load Balancer. You need to implement an SSL solution for your system to improve its security which is why you requested an SSL/TLS certificate from a third-party certificate authority (CA).

Where can you safely import the SSL/TLS certificate of your application? (Select TWO.)

## Options
A. AWS Certificate Manager

B. IAM certificate store

C. A private S3 bucket with versioning enabled

D. An S3 bucket configured with server-side encryption with customer-provided encryption keys (SSE-C)

E. CloudFront

---

# Question 58

## Topic
Design Secure Architectures

## Question
A hospital has a mission-critical application that uses a RESTful API powered by Amazon API Gateway and AWS Lambda. The medical officers upload PDF reports to the system which are then stored as static media content in an Amazon S3 bucket.

The security team wants to improve its visibility when it comes to cyber-attacks and ensure HIPAA (Health Insurance Portability and Accountability Act) compliance. The company is searching for a solution that continuously monitors object-level S3 API operations and identifies protected health information (PHI) in the reports, with minimal changes in the existing Lambda function.

Which of the following solutions will meet these requirements with the LEAST operational overhead?

## Options
A. Use Amazon Transcribe to read and analyze the PDF reports using the StartTranscriptionJob API operation. Use Amazon CloudWatch Logs to detect protected health information (PHI) content by tracking access logs and security events.

B. Use Amazon Textract Medical with PII redaction turned on to extract and filter sensitive text from the PDF reports. Create a new Lambda function that calls the regular Amazon Comprehend API to identify the PHI from the extracted text.

C. Use Amazon Textract to extract the text from the PDF reports. Integrate Amazon Comprehend Medical with the existing Lambda function to identify the PHI from the extracted text.

D. Use Amazon Textract with the StartDocumentTextDetection API operation to extract text from PDF reports. Analyze the extracted data with a custom-built PHI detection algorithm within the Lambda function.

---

# Question 59

## Topic
Design Secure Architectures

## Question
A startup launched a new FTP server using an On-Demand EC2 instance in a newly created VPC with default settings. The server should not be accessible publicly but only through the IP address 175.45.116.100 and nowhere else.

Which of the following is the most suitable way to implement this requirement?

## Options
A. Create a new Network ACL inbound rule in the subnet of the EC2 instance with the following details:

B. Protocol: UDP

C. Port Range: 20 - 21

D. Source: 175.45.116.100/0

E. Allow/Deny: ALLOW

F. Create a new Network ACL inbound rule in the subnet of the EC2 instance with the following details:

G. Protocol: TCP

H. Port Range: 20 - 21

I. Source: 175.45.116.100/0

J. Allow/Deny: ALLOW

K. Create a new inbound rule in the security group of the EC2 instance with the following details:

L. Protocol: UDP

M. Port Range: 20 - 21

N. Source: 175.45.116.100/32

O. Create a new inbound rule in the security group of the EC2 instance with the following details:

P. Protocol: TCP

Q. Port Range: 20 - 21

R. Source: 175.45.116.100/32

---

# Question 60

## Topic
Design Resilient Architectures

## Question
A large multinational investment bank has a web application that requires a minimum of 4 EC2 instances to run to ensure that it can cater to its users across the globe. You are instructed to ensure fault tolerance of this system.

Which of the following is the best option?

## Options
A. Deploy an Auto Scaling group with 2 instances in each of 2 Availability Zones behind an Application Load Balancer.

B. Deploy an Auto Scaling group with 4 instances in one Availability Zone behind an Application Load Balancer.

C. Deploy an Auto Scaling group with 1 instance in each of 4 Availability Zones behind an Application Load Balancer.

D. Deploy an Auto Scaling group with 2 instances in each of 3 Availability Zones behind an Application Load Balancer.

---

# Question 61

## Topic
Design High-Performing Architectures

## Question
A company has a global news website hosted in a fleet of EC2 Instances. Lately, the load on the website has increased which resulted in slower response time for the site visitors. This issue impacts the revenue of the company as some readers tend to leave the site if it does not load after 10 seconds. The goal is to address the issue in a cost-effective manner.”

Which of the below services in AWS can be used to solve this problem? (Select TWO.)

## Options
A. For better read throughput, use AWS Storage Gateway to distribute the content across multiple regions.

B. Deploy the website to all regions in different VPCs for faster processing.

C. Use Amazon RDS Multi-AZ deployments for database read scalability.

D. Use Amazon ElastiCache for the website's in-memory data store or cache.

E. Use Amazon CloudFront with website as the custom origin.

---

# Question 62

## Topic
Design Cost-Optimized Architectures

## Question
A web application requires a minimum of six Amazon Elastic Compute Cloud (EC2) instances running at all times. You are tasked to deploy the application to three availability zones in the EU Ireland region (eu-west-1a, eu-west-1b, and eu-west-1c). It is required that the system is fault-tolerant up to the loss of one Availability Zone.

Which of the following setup is the most cost-effective solution which also maintains the fault-tolerance of your system?

## Options
A. 6 instances in eu-west-1a, 6 instances in eu-west-1b, and 6 instances in eu-west-1c

B. 6 instances in eu-west-1a, 6 instances in eu-west-1b, and no instances in eu-west-1c

C. 3 instances in eu-west-1a, 3 instances in eu-west-1b, and 3 instances in eu-west-1c

D. 2 instances in eu-west-1a, 2 instances in eu-west-1b, and 2 instances in eu-west-1c

---

# Question 63

## Topic
Design Secure Architectures

## Question
A company has an Application Load Balancer (ALB) that accepts HTTP and HTTPS traffic on ports 80 and 443, respectively. Recently, the company associated a new domain for its website, and they want to ensure that all HTTP traffic for this new domain is automatically redirected to HTTPS to improve security.

Which ALB configuration should be done to satisfy the requirement?

## Options
A. Configure the existing on port 443 and add a redirect action to HTTP on port 80.

B. Configure the existing HTTP listener to redirect traffic to port 443.

C. Create a new HTTP listener on port 80 and add a redirect action to the HTTPS protocol on port 443.

D. Create a new ALB listener on port 443 and configure it to redirect HTTP traffic to HTTPS.

---

# Question 64

## Topic
Design High-Performing Architectures

## Question
A company plans to develop a custom messaging service that will be used to train an AI for an automatic response feature. The service is expected to receive thousands of messages per day, all of which will be processed by an Amazon EMR cluster. It is crucial that none of the messages are lost, no duplicates are produced, and that the messages are processed in EMR in the same order as their arrival.

Which of the following options can satisfy the given requirement?

## Options
A. Create an Amazon Data Firehose to handle the messages.

B. Set up a default Amazon SQS queue to handle the messages.

C. Create an Amazon Kinesis Data Stream to collect the messages.

D. Set up an Amazon SNS Topic to handle the messages.

---

# Question 65

## Topic
Design Resilient Architectures

## Question
A company is running a web application on AWS. The application is made up of an Auto-Scaling group that sits behind an Application Load Balancer and an Amazon DynamoDB table where user data is stored. The solutions architect must design the application to remain available in the event of a regional failure. A solution to automatically monitor the status of your workloads across your AWS account, conduct architectural reviews and check for AWS best practices.

Which configuration meets the requirement with the least amount of downtime possible?

## Options
A. Write a CloudFormation template that includes the auto-scaling group, application load balancer, and DynamoDB table. In the event of a failure, deploy the template in a secondary region. Use Route 53 DNS failover to automatically route traffic to the resources in the secondary region. Set up and configure the Amazon Managed Service for Prometheus service to receive insights for improving your workloads based on the AWS best practices.

B. Write a CloudFormation template that includes the auto-scaling group, application load balancer, and DynamoDB table. In the event of a failure, deploy the template in a secondary region. Configure Amazon EventBridge (Amazon CloudWatch Events) to trigger a Lambda function that updates the application’s Route 53 DNS record. Launch an Amazon Managed Grafana workspace to automatically receive tips and action items for improving your workloads based on the AWS best practices

C. In a secondary region, create a global table of the DynamoDB table and replicate the auto-scaling group and application load balancer. Use Route 53 DNS failover to automatically route traffic to the resources in the secondary region. Set up the AWS Well-Architected Tool to easily get recommendations for improving your workloads based on the AWS best practices

D. In a secondary region, create a global secondary index of the DynamoDB table and replicate the auto-scaling group and application load balancer. Use Route 53 DNS failover to automatically route traffic to the resources in the secondary region. Set up the AWS Compute Optimizer to automatically get recommendations for improving your workloads based on the AWS best practices

---
