# Question 17

A company plans to launch an Amazon EC2 instance in a private subnet for its internal corporate web portal. For security purposes, the EC2 instance must send data to Amazon DynamoDB and Amazon S3 via private endpoints that don't pass through the public Internet.

Which of the following can meet the above requirements?

## Options

A. Use AWS VPN CloudHub to route all access to S3 and DynamoDB via private endpoints.

B. Enable DynamoDB Encryption at Rest with the default AWS-managed key and S3 Server-Side Encryption with the default AWS KMS key to route all traffic to DynamoDB and S3 via private endpoints.

C. Use AWS Direct Connect to route all access to S3 and DynamoDB via private endpoints.

D. Use a DynamoDB VPC endpoint and an S3 VPC endpoint to route all access to these services via private endpoints.

## Correct Answer

**D. Use a DynamoDB VPC endpoint and an S3 VPC endpoint to route all access to these services via private endpoints.**

## Explanation

A VPC endpoint allows you to privately connect your VPC to supported AWS and VPC endpoint services powered by AWS PrivateLink without needing an Internet gateway, NAT computer, VPN connection, or AWS Direct Connect connection. Instances in your VPC do not require public IP addresses to communicate with resources in the service. Traffic between your VPC and the other service does not leave the Amazon network.

VPC endpoint is the most suitable service that will allow you to use private IP addresses to access both DynamoDB and S3 without any exposure to the public internet.

### Why other options are incorrect:

- **B** - Encryption at rest does not affect the traffic routing. Encryption manages data security but does not control how traffic is routed between services.

- **C** - AWS Direct Connect is primarily used to establish a dedicated network connection from your premises to AWS. The scenario didn't mention on-premises servers or hybrid cloud architecture.

- **A** - AWS VPN CloudHub is typically used to provide secure communication between remote sites and not for creating a private endpoint to access Amazon S3 and DynamoDB within the Amazon network.

## References

- https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/vpc-endpoints-dynamodb.html
- https://docs.aws.amazon.com/glue/latest/dg/vpc-endpoints-s3.html
- https://tutorialsdojo.com/amazon-vpc/

## Domain

Design High-Performing Architectures
