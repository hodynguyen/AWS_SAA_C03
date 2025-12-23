# AWS SAA-C03 Practice Test 3

## Test Information
- **Total Questions:** 65
- **Time Limit:** 130 minutes
- **Passing Score:** 72%

---

## Question 1
You are automating the creation of EC2 instances in your VPC. Hence, you wrote a python script to trigger the Amazon EC2 API to request 50 EC2 instances in a single Availability Zone. However, you noticed that after 20 successful requests, subsequent requests failed.

What could be a reason for this issue and how would you resolve it?

A. By default, AWS allows you to provision a maximum of 20 instances per region. Select a different region and retry the failed request.
B. By default, AWS allows you to provision a maximum of 20 instances per Availability Zone. Select a different Availability Zone and retry the failed request.
C. There was an issue with the Amazon EC2 API. Just resend the requests and these will be provisioned successfully.
D. There is a vCPU-based On-Demand Instance limit per region which is why subsequent requests failed. Just submit the limit increase form to AWS and retry the failed requests once approved.

---

## Question 2
In Amazon EC2, you can manage your instances from the moment you launch them up to their termination. You can flexibly control your computing costs by changing the EC2 instance state. Which of the following statements is true regarding EC2 billing? (Select TWO.)

A. You will be billed when your Reserved instance is in terminated state.
B. You will not be billed for any instance usage while an instance is not in the running state.
C. You will be billed when your On-Demand instance is in pending state.
D. You will be billed when your Spot instance is preparing to stop with a stopping state.
E. You will be billed when your On-Demand instance is preparing to hibernate with a stopping state.

---

(Questions 3-46 omitted for brevity, see answers/ directory)

---

## Question 47
A new online banking platform has been re-designed to have a microservices architecture in which complex applications are decomposed into smaller, independent services. The new platform uses Kubernetes, and the application containers are optimally configured for running small, decoupled services.

The new solution should remove the need to provision and manage servers, let you specify and pay for resources per application as well as improve security through application isolation by design.

Which of the following is the MOST suitable solution to implement to launch this new platform to AWS?

A. Use Amazon ECS to run the Kubernetes cluster on AWS Fargate
B. Host the application in Amazon EMR Serverless and an EBS storage with the fast snapshot restore feature enabled
C. Use AWS Fargate on Amazon EKS with Service Auto Scaling to run the containerized banking platform
D. Deploy an Amazon EKS Cluster on AWS Outposts with Kubernetes Cluster Autoscaler and sync any orphaned pods with Amazon AppFlow

---

## Question 48
A company is deploying a Microsoft SharePoint Server environment on AWS using CloudFormation. The Solutions Architect needs to install and configure the architecture that is composed of Microsoft Active Directory (AD) domain controllers, Microsoft SQL Server 2012, multiple Amazon EC2 instances to host the Microsoft SharePoint Server and many other dependencies. The Architect needs to ensure that the required components are properly running before the stack creation proceeds.

Which of the following should the Architect do to meet this requirement?

A. Configure the UpdateReplacePolicy attribute in the CloudFormation template. Send a success signal after the applications are installed and configured using the cfn-signal helper script.
B. Configure a UpdatePolicy attribute to the instance in the CloudFormation template. Send a success signal after the applications are installed and configured using the cfn-signal helper script.
C. Configure the DependsOn attribute in the CloudFormation template. Send a success signal after the applications are installed and configured using the cfn-init helper script.
D. Configure a CreationPolicy attribute to the instance in the CloudFormation template. Send a success signal after the applications are installed and configured using the cfn-signal helper script.

---

## Question 49
A company is storing its financial reports and regulatory documents in an Amazon S3 bucket. To comply with the IT audit, they tasked their Solutions Architect to track all new objects added to the bucket as well as the removed ones. It should also track whether a versioned object is permanently deleted. The Architect must configure Amazon S3 to publish notifications for these events to a queue for post-processing and to an Amazon SNS topic that will notify the Operations team.

Which of the following is the MOST suitable solution that the Architect should implement?

A. Create a new Amazon SNS topic and Amazon MQ. Add an S3 event notification configuration on the bucket to publish s3:ObjectCreated:* and ObjectRemoved:DeleteMarkerCreated event types to SQS and SNS.
B. Create a new Amazon SNS topic and Amazon SQS queue. Add an S3 event notification configuration on the bucket to publish s3:ObjectCreated:* and ObjectRemoved:DeleteMarkerCreated event types to SQS and SNS.
C. Create a new Amazon SNS topic and Amazon SQS queue. Add an S3 event notification configuration on the bucket to publish s3:ObjectCreated:* and s3:ObjectRemoved:Delete event types to SQS and SNS.
D. Create a new Amazon SNS topic and Amazon MQ. Add an S3 event notification configuration on the bucket to publish s3:ObjectAdded:* and s3:ObjectRemoved:* event types to SQS and SNS.

---

## Question 50
A company needs to use Amazon Aurora as the Amazon RDS database engine of their web application. The Solutions Architect has been instructed to implement a 90-day backup retention policy.

Which of the following options can satisfy the given requirement?

A. Configure RDS to export the automated snapshot automatically to Amazon S3 and create a lifecycle policy to delete the object after 90 days.
B. Create an AWS Backup plan to take daily snapshots with a retention period of 90 days.
C. Configure an automated backup and set the backup retention period to 90 days.
D. Create a daily scheduled event using CloudWatch Events and AWS Lambda to directly download the RDS automated snapshot to an S3 bucket. Archive snapshots older than 90 days to Glacier.

---

## Question 51
A company needs to collect gigabytes of data per second from websites and social media feeds to gain insights into its product offerings and continuously improve the user experience. To meet this design requirement, an application is deployed on an Auto Scaling group of Spot EC2 instances which processes the data and stores the results to DynamoDB and Redshift. The solution should have a built-in enhanced fan-out feature.

Which fully-managed AWS service can you use to collect and process large streams of data records in real-time with the LEAST amount of administrative overhead?

A. Amazon S3 Access Points
B. Amazon Kinesis Data Streams
C. Amazon Managed Streaming for Apache Kafka (Amazon MSK)
D. AWS Data Exchange

---

## Question 52
A company is hosting an application on EC2 instances that regularly pushes and fetches data in Amazon S3. Due to a change in compliance, the instances need to be moved on a private subnet. Along with this change, the company wants to lower the data transfer costs by configuring its AWS resources.

How can this be accomplished in the MOST cost-efficient manner?

A. Set up a NAT Gateway in the public subnet to connect to Amazon S3.
B. Set up an AWS Transit Gateway to access Amazon S3.
C. Create an Amazon S3 gateway endpoint to enable a connection between the instances and Amazon S3.
D. Create an Amazon S3 interface endpoint to enable a connection between the instances and Amazon S3.

---

## Question 53
A manufacturing company has EC2 instances running in AWS. The EC2 instances are configured with Auto Scaling. There are a lot of requests being lost because of too much load on the servers. The Auto Scaling is launching new EC2 instances to take the load accordingly yet, there are still some requests that are being lost.

Which of the following is the MOST suitable solution that you should implement to avoid losing recently submitted requests?

A. Use larger instances for your application with an attached Elastic Fabric Adapter (EFA).
B. Set up Amazon Aurora Serverless for on-demand, auto-scaling configuration of your EC2 Instances and also enable Amazon Aurora Parallel Query feature for faster analytical queries over your current data.
C. Replace the Auto Scaling group with a cluster placement group to achieve a low-latency network performance necessary for tightly-coupled node-to-node communication.
D. Use an Amazon SQS queue to decouple the application components and scale-out the EC2 instances based upon the ApproximateNumberOfMessages metric in Amazon CloudWatch.

---

## Question 54
A Solutions Architect for a global news company is configuring a fleet of EC2 instances in a subnet that currently is in a VPC with an Internet gateway attached. All of these EC2 instances can be accessed from the Internet. The architect launches another subnet and deploys an EC2 instance in it, however, the architect is not able to access the EC2 instance from the Internet.

What could be the possible reasons for this issue? (Select TWO.)

A. The Amazon EC2 instance does not have an attached Elastic Fabric Adapter (EFA).
B. The Amazon EC2 instance does not have a public IP address associated with it.
C. The route table is not configured properly to send traffic from the EC2 instance to the Internet through the Internet gateway.
D. The Amazon EC2 instance is not a member of the same Auto Scaling group.
E. The route table is not configured properly to send traffic from the EC2 instance to the Internet through the customer gateway (CGW).

---

## Question 55
An online stock trading application stores financial data in an Amazon S3 bucket, with a lifecycle policy that moves older data to Glacier every month. A strict compliance requirement mandates that a surprise audit can occur at any time, and the required data must be retrievable in under 15 minutes under all circumstances. The manager has instructed that retrieval capacity be available when needed and should support up to 150 MB/s of retrieval throughput.

Which of the following will meet the given requirement? (Select TWO.)

A. Purchase provisioned retrieval capacity.
B. Use Expedited Retrieval to access the financial data.
C. Use Bulk Retrieval to access the financial data.
D. Use Standard Retrieval for accessing the financial data.
E. Specify a range, or portion, of the financial data archive to retrieve.

---

## Question 56
A large financial firm in the country has an AWS environment that contains several Reserved EC2 instances hosting a web application that has been decommissioned last week. To save costs, you need to stop incurring charges for the Reserved instances as soon as possible.

What cost-effective steps will you take in this circumstance? (Select TWO.)

A. Go to the Amazon.com online shopping website and sell the Reserved instances.
B. Terminate the Reserved instances as soon as possible to avoid getting billed at the on-demand price when it expires.
C. Stop the Reserved instances as soon as possible.
D. Contact AWS to cancel your AWS subscription.
E. Go to the AWS Reserved Instance Marketplace and sell the Reserved instances.

---

## Question 57
A company is hosting EC2 instances that are on non-production environment and processing non-priority batch loads, which can be interrupted at any time.

What is the best instance purchasing option which can be applied to your EC2 instances in this case?

A. On-Demand Capacity Reservations
B. On-Demand Instances
C. Reserved Instances
D. Spot Instances

---

## Question 58
A tech startup is launching an on-demand food delivery platform using Amazon ECS cluster with an AWS Fargate serverless compute engine and Amazon Aurora. It is expected that the database read queries will significantly increase in the coming weeks ahead. A Solutions Architect recently launched two Read Replicas to the database cluster to improve the platform's scalability.

Which of the following is the MOST suitable configuration that the Architect should implement to load balance all of the incoming read requests equally to the two Read Replicas?

A. Enable Amazon Aurora Parallel Query.
B. Use the built-in Reader endpoint of the Amazon Aurora database.
C. Use the built-in Cluster endpoint of the Amazon Aurora database.
D. Create a new Network Load Balancer to evenly distribute the read queries to the Read Replicas of the Amazon Aurora database.

---

## Question 59
A large telecommunications company needs to run analytics against all combined log files from the Application Load Balancer as part of the regulatory requirements.

Which AWS services can be used together to collect logs and then easily perform log analysis?

A. Amazon S3 for storing ELB log files and Amazon EMR for analyzing the log files.
B. Amazon DynamoDB for storing and EC2 for analyzing the logs.
C. Amazon EC2 with EBS volumes for storing and analyzing the log files.
D. Amazon S3 for storing the ELB log files and an EC2 instance for analyzing the log files using a custom-built application.

---

## Question 60
A company hosted a web application on a Linux Amazon EC2 instance in the public subnet that uses a non-default network ACL. The instance uses a default security group and has an attached Elastic IP address. The network ACL is configured to block all inbound and outbound traffic. The Solutions Architect must allow incoming traffic on port 443 to access the application from any source.

Which combination of steps will accomplish this requirement? (Select TWO.)

A. In the Security Group, add a new rule to allow TCP connection on port 443 from source 0.0.0.0/0
B. In the Network ACL, update the rule to allow inbound TCP connection on port 443 from source 0.0.0.0/0 and outbound TCP connection on port 32768 - 65535 to destination 0.0.0.0/0
C. In the Network ACL, update the rule to allow outbound TCP connection on port 32768 - 65535 to destination 0.0.0.0/0
D. In the Network ACL, update the rule to allow both inbound and outbound TCP connection on port 443 from source 0.0.0.0/0 and to destination 0.0.0.0/0
E. In the Security Group, create a new rule to allow TCP connection on port 443 to destination 0.0.0.0/0

---

## Question 61
A company has established a dedicated network connection from its on-premises data center to AWS Cloud using AWS Direct Connect (DX). The core network services, such as the Domain Name System (DNS) service and Active Directory services, are all hosted on-premises. The company has new AWS accounts that will also require consistent and dedicated access to these network services.

Which of the following can satisfy this requirement with the LEAST amount of operational overhead and in a cost-effective manner?

A. Set up another Direct Connect connection for each and every new AWS account that will be added.
B. Set up a new Direct Connect gateway and integrate it with the existing Direct Connect connection. Configure a VPC peering connection between AWS accounts and associate it with Direct Connect gateway.
C. Create a new Direct Connect gateway and integrate it with the existing Direct Connect connection. Set up a Transit Gateway between AWS accounts and associate it with the Direct Connect gateway.
D. Create a new AWS VPN CloudHub. Set up a Virtual Private Network (VPN) connection for additional AWS accounts.

---

## Question 62
A solutions architect is managing an application that runs on a Windows EC2 instance with an attached Amazon FSx for Windows File Server. To save cost, management has decided to stop the instance during off-hours and restart it only when needed. It has been observed that the application takes several minutes to become fully operational which impacts productivity.

How can the solutions architect speed up the instance’s loading time without driving the cost up?

A. Migrate the application to a Linux-based EC2 instance.
B. Enable the hibernation mode on the EC2 instance.
C. Migrate the application to an EC2 instance with hibernation enabled.
D. Disable the Instance Metadata Service to reduce the things that need to be loaded at startup.

---

## Question 63
A call center wants to use Artificial Intelligence(AI) to extract insights from audio recordings to assess the quality of its customer service. The calls are available in both English and Hindi. A sentiment analysis report in English must be generated for each recording to assess whether or not the customer had a positive experience. Once the solution is completed, new languages will eventually be supported, such as Arabic, Mandarin, and Spanish.

How can the solutions architect build the solution without maintaining any machine learning model?

A. Set up Amazon Comprehend to convert audio recordings into text. Use Amazon Kendra to translate Hindi texts into English and utilize the Amazon Detective service to automatically detect negative user behaviors for sentiment analysis.
B. Convert audio recordings into text using Amazon Transcribe. Set up Amazon Translate to translate Hindi texts into English and use Amazon Comprehend for sentiment analysis.
C. Utilize the Amazon Lex service to convert audio recordings into text. Call the Amazon Translate API to translate Hindi texts into English and use Amazon SageMaker Clarify for sentiment prediction and analysis.
D. Transcribe audio recordings into text using Amazon Polly's StartSpeechSynthesisTask operation. Set up Amazon Rekognition to recognize and automatically translate Hindi texts into English. Use the combination of Amazon Fraud Detector and Amazon SageMaker BlazingText algorithm for sentiment analysis.

---

## Question 64
A company intends to give each of its developers a personal AWS account through AWS Organizations. To enforce regulatory policies, preconfigured AWS Config rules will be set in the new accounts. A solutions architect must see to it that developers are unable to remove or modify any rules in AWS Config.

Which solution meets the objective with the least operational overhead?

A. Use an IAM Role in the new accounts with an attached IAM trust relationship to disable the access of the root user to AWS Config.
B. Add the developers' AWS account to an organization unit (OU). Attach a service control policy (SCP) to the OU that restricts access to AWS Config.
C. Configure an AWS Config rule in the root account to detect if changes to the new account’s Config rules are made.
D. Set up an AWS Control Tower in the root account to detect if there were any changes to the new account’s AWS Config rules. Attach an IAM trust relationship to the IAM User of each developer which prevents any changes in AWS Config.

---

## Question 65
A solutions architect is designing an infrastructure for a serverless application. The application is packaged as a Docker image stored in Amazon Elastic Container Registry (Amazon ECR) and must be deployed on a fully managed serverless compute service. Additionally, the application requires 5 GB of ephemeral storage for temporary data processing.

Which deployment option meets these requirements?

A. Deploy the application in an AWS Lambda function with Container image support. Set the function’s storage to 5 GB.
B. Deploy the application to an Amazon ECS cluster that uses AWS Fargate tasks.
C. Deploy the application Amazon ECS cluster with Amazon EC2 worker nodes and attach a 5 GB Amazon EBS volume.
D. Deploy the application in an AWS Lambda function with Container image support. Attach an Amazon Elastic File System (Amazon EFS) volume to the function.

---

## End of Test

Good luck on your AWS Solutions Architect Associate exam!
