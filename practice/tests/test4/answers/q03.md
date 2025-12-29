# Question 3

A Cloud Engineer is writing CloudFormation YAML scripts to define AWS resources for a new cryptocurrency trading platform. The manager is confused about why the engineer isn't creating resources directly and asks for clarification.

What are the benefits of using Amazon CloudFormation? (Select TWO.)

## Options

A. A storage location for the code of your application.

B. Using CloudFormation itself is free, including the AWS resources that have been created.

C. Enables modeling, provisioning, and version-controlling of your entire AWS infrastructure.

D. Allows you to model your entire infrastructure in a text file.

E. Provides highly durable and scalable data storage.

## Correct Answer

**C. Enables modeling, provisioning, and version-controlling of your entire AWS infrastructure.**

**D. Allows you to model your entire infrastructure in a text file.**

## Explanation

CloudFormation is an Infrastructure as Code (IaC) service that allows you to define your entire AWS infrastructure in template files (YAML or JSON). These templates can be version-controlled, enabling consistent and repeatable deployments across environments.

### Why other options are incorrect:

- **A** - CloudFormation is not a code storage service. Use CodeCommit or S3 for that.

- **B** - CloudFormation service is free, but you pay for the AWS resources it creates.

- **E** - CloudFormation doesn't provide storage. It provisions and manages resources.

## References

- https://aws.amazon.com/cloudformation/
- https://tutorialsdojo.com/aws-cloudformation/

## Domain

Design High-Performing Architectures
