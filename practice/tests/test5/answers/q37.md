# Question 37

A company wants to store data in S3 but keep frequently accessed data locally on-premises without extending local storage.

What is the best solution?

## Options

A. Use Amazon Glacier.

B. Use EC2 with EBS volumes.

C. Use ElastiCache and S3.

D. Use AWS Storage Gateway - Cached Volumes.

## Correct Answer

**D. Use AWS Storage Gateway - Cached Volumes.**

## Explanation

Cached Volumes:
- **Primary storage in S3**: Scalable, durable cloud storage
- **Local cache**: Frequently accessed data kept on-premises
- **iSCSI access**: Mount as local block storage
- **No local expansion**: Minimize on-premises storage needs

### Why other options are incorrect:

- **A** - Glacier is for archiving, not active storage with local caching.

- **B** - EC2/EBS doesn't provide local on-premises caching.

- **C** - ElastiCache is in-cloud caching, not on-premises.

## References

- https://aws.amazon.com/storagegateway/faqs/
- https://tutorialsdojo.com/aws-storage-gateway/

## Domain

Design High-Performing Architectures
