# Question 32

EC2 instances in private subnet access S3 via NAT Instance. How to reduce costs most effectively?

## Options

A. Use smaller instance type for NAT.

B. Replace NAT instance with NAT Gateway.

C. Remove NAT instance and use S3 Gateway endpoint.

D. Remove NAT instance and use S3 Interface endpoint.

## Correct Answer

**C. Remove NAT instance and use S3 Gateway endpoint.**

## Explanation

S3 Gateway Endpoint:
- **Free**: No hourly or data processing charges
- **Private access**: Traffic stays on AWS network
- **Route table integration**: Simple configuration

### Why other options are incorrect:

- **A** - Smaller NAT still has hourly + data processing costs.

- **B** - NAT Gateway has hourly + data processing charges.

- **D** - Interface endpoint has hourly charges (~$0.01/hour).

## References

- https://docs.aws.amazon.com/vpc/latest/privatelink/vpce-gateway.html
- https://tutorialsdojo.com/amazon-vpc/

## Domain

Design Secure Architectures
