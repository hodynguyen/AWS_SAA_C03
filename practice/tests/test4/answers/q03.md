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

## Correct Answer
C, D

## Explanation
AWS CloudFormation provides a common language for you to describe and provision all the infrastructure resources in your cloud environment. CloudFormation allows you to use a simple text file to model and provision, in an automated and secure manner, all the resources needed for your applications across all regions and accounts. This file serves as the single source of truth for your cloud environment. AWS CloudFormation is available at no additional charge, and you pay only for the AWS resources needed to run your applications.

Hence, the correct answers are:

- Enables modeling, provisioning, and version-controlling of your entire AWS infrastructure

- Allows you to model your entire infrastructure in a text file

References:

https://aws.amazon.com/cloudformation/

https://aws.amazon.com/cloudformation/faqs/

Check out this AWS CloudFormation Cheat Sheet:

https://tutorialsdojo.com/aws-cloudformation/

**Why other options are incorrect:**

- The option that says: Provides highly durable and scalable data storage is incorrect because CloudFormation is not a data storage service.

- The option that says: A storage location for the code of your application is incorrect because CloudFormation is not primarily used to store your application code.

- The option that says: Using CloudFormation itself is free, including the AWS resources that have been created is incorrect because although the use of CloudFormation service is only free, you have to pay for the AWS resources that you created.

