# Question 1

A software company has resources hosted in AWS and on-premises servers. You have been requested to create a decoupled architecture for applications which make use of both resources.

Which of the following options are valid? (Select TWO.)

## Options

A. Use DynamoDB to utilize both on-premises servers and EC2 instances for your decoupled application

B. Use SWF to utilize both on-premises servers and EC2 instances for your decoupled application

C. Use SQS to utilize both on-premises servers and EC2 instances for your decoupled application

D. Use VPC peering to connect both on-premises servers and EC2 instances for your decoupled application

E. Use RDS to utilize both on-premises servers and EC2 instances for your decoupled application

## Correct Answers

**B. Use SWF to utilize both on-premises servers and EC2 instances for your decoupled application**

**C. Use SQS to utilize both on-premises servers and EC2 instances for your decoupled application**

## Explanation

Amazon Simple Queue Service (SQS) and Amazon Simple Workflow Service (SWF) are the services that you can use for creating a decoupled architecture in AWS. Decoupled architecture is a type of computing architecture that enables computing components or layers to execute independently while still interfacing with each other.

Amazon SQS offers reliable, highly-scalable hosted queues for storing messages while they travel between applications or microservices. Amazon SWF is a web service that makes it easy to coordinate work across distributed application components.

### Why other options are incorrect:

- **A & E** - RDS and DynamoDB are database services, not for decoupling.

- **D** - You can't create a VPC peering for your on-premises network and AWS VPC.

## References

- https://aws.amazon.com/sqs/
- http://docs.aws.amazon.com/amazonswf/latest/developerguide/swf-welcome.html
- https://tutorialsdojo.com/amazon-sqs/

## Domain

Design High-Performing Architectures
