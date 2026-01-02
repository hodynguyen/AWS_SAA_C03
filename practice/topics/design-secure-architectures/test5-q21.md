# Question 21

EC2 in private subnet accesses financial data in S3 via pre-signed URLs. Security team is concerned about Internet connectivity to S3.

What is the most cost-effective solution?

## Options

A. Access S3 through Interface VPC Endpoint (PrivateLink).

B. Access S3 through VPN connection.

C. Access S3 through Gateway VPC Endpoint.

D. Create custom VPC endpoint service.

## Correct Answer

**C. Access S3 through Gateway VPC Endpoint.**

## Explanation

Gateway VPC Endpoint:
- **Free**: No hourly charges (unlike Interface endpoints)
- **Private access**: Traffic stays on AWS network
- **S3 supported**: Gateway endpoint specifically for S3 and DynamoDB

Interface endpoints cost ~$0.01/hour + data processing fees.

### Why other options are incorrect:

- **A** - Interface endpoint works but costs money; Gateway is free.

- **B** - VPN still goes over public Internet.

- **D** - Endpoint service is for your own services, not S3.

## References

- https://docs.aws.amazon.com/vpc/latest/userguide/vpce-gateway.html
- https://tutorialsdojo.com/amazon-vpc/

## Domain

Design Secure Architectures
