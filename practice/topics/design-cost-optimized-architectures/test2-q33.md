# Question 33

A start-up company that offers an intuitive financial data analytics service has consulted about its AWS architecture. The company has a fleet of Amazon EC2 worker instances that process financial data and then output reports used by its clients. The reports must be stored in a durable storage.

Which of the following is a cost-efficient and scalable storage option for this scenario?

## Options

A. Use Amazon Redshift as the data storage and Amazon CloudFront as the CDN.

B. Use Amazon S3 Glacier as the data storage and Amazon ElastiCache as the CDN.

C. Use multiple EC2 instance stores for data storage and Amazon ElastiCache as the CDN.

D. Use Amazon S3 as the data storage and Amazon CloudFront as the CDN.

## Correct Answer

**D. Use Amazon S3 as the data storage and Amazon CloudFront as the CDN.**

## Explanation

Amazon S3 offers highly durable, scalable, and secure storage. CloudFront is a fast CDN that integrates with S3 for global content delivery.

### Why other options are incorrect:

- **A** - Redshift is a data warehouse, not for file storage.

- **B** - S3 Glacier is for archives; ElastiCache is for caching.

- **C** - EC2 instance stores are not durable.

## References

- https://aws.amazon.com/s3/
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Cost-Optimized Architectures
