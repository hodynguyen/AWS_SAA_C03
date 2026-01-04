# Question 16

JSON documents in S3, Lake Formation catalog. Athena queries are slow.

How to improve query performance while ensuring security?

## Options

A. Convert to CSV. Use Lake Formation named resource access.

B. Transform to Apache Parquet. Use lakeformation:GetDataAccess permission.

C. Apply minification. Use LF-TBAC with IAM tags.

D. Compress to GZIP. Use IAM policy with SourceArn/SourceAccount.

## Correct Answer

**B. Transform to Apache Parquet. Use lakeformation:GetDataAccess permission.**

## Explanation

Parquet for Athena:
- **Columnar format**: 2x faster than row formats
- **Predicate pushdown**: Skip irrelevant data blocks
- **6x less storage**: Compressed efficiently
- **Lake Formation**: lakeformation:GetDataAccess for data access

### Why other options are incorrect:

- **A** - CSV is row-based, slower than Parquet.

- **C** - Minification doesn't improve query performance.

- **D** - GZIP saves storage, not query speed.

## References

- https://aws.amazon.com/blogs/big-data/top-10-performance-tuning-tips-for-amazon-athena/
- https://tutorialsdojo.com/amazon-athena/

## Domain

Design Secure Architectures
