# Question 42

An organization uses AWS Direct Connect for private connectivity. They need a fully managed solution to automate and accelerate data replication to AWS storage services.

Which solution would you recommend?

## Options

A. Use AWS Storage Gateway tape gateway.

B. Use AWS DataSync agent to move data over a service endpoint.

C. Use AWS DataSync agent to move data over the Internet.

D. Use AWS Storage Gateway file gateway.

## Correct Answer

**B. Use AWS DataSync agent to move data over a service endpoint.**

## Explanation

AWS DataSync:
- **Fully managed**: Automates data transfer tasks
- **Direct Connect support**: Uses VPC endpoints (private connectivity) or public endpoints
- **Accelerated transfer**: 10x faster than open-source tools
- **Multi-service support**: S3, EFS, FSx, and more

Since Direct Connect provides private connectivity, use service endpoints (not public Internet).

### Why other options are incorrect:

- **A, D** - Storage Gateway provides hybrid cloud storage, not accelerated data replication.

- **C** - With Direct Connect, data should travel over private endpoints, not the public Internet.

## References

- https://docs.aws.amazon.com/datasync/latest/userguide/what-is-datasync.html
- https://tutorialsdojo.com/aws-datasync/

## Domain

Design High-Performing Architectures
