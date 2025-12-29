# Question 44

A tech company is running low on on-premises storage and wants to extend storage using AWS.

Which AWS service can help them achieve this?

## Options

A. Amazon SQS

B. Amazon Elastic Block Storage

C. Amazon EC2

D. AWS Storage Gateway

## Correct Answer

**D. AWS Storage Gateway**

## Explanation

AWS Storage Gateway provides hybrid cloud storage:
- **Seamless integration**: On-premises appliance connects to AWS storage
- **Multiple modes**: File, Volume, or Tape Gateway
- **Extends capacity**: Use AWS S3/Glacier as backend storage
- **Low-latency access**: Local cache for frequently accessed data

### Why other options are incorrect:

- **A** - SQS is a message queuing service, not storage.

- **B** - EBS is block storage for EC2 instances, not for extending on-premises storage.

- **C** - EC2 is compute, not storage extension.

## References

- http://docs.aws.amazon.com/storagegateway/latest/userguide/WhatIsStorageGateway.html
- https://tutorialsdojo.com/aws-storage-gateway/

## Domain

Design Resilient Architectures
