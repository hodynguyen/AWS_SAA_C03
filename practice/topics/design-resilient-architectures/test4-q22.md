# Question 22

A Lambda function stores JSON results in S3. The company needs to run Big Data analytics on this data without moving it to a separate system.

Which services can meet this requirement?

## Options

A. Amazon Glue, Amazon Redshift, Amazon S3

B. Amazon Neptune, DynamoDB DAX, Amazon Redshift Spectrum

C. Amazon X-Ray, Amazon Neptune, DynamoDB

D. Amazon Athena, Amazon Redshift Spectrum, AWS Glue

## Correct Answer

**D. Amazon Athena, Amazon Redshift Spectrum, AWS Glue**

## Explanation

These services analyze S3 data in-place:
- **Athena**: Serverless SQL queries directly on S3 data
- **Redshift Spectrum**: Query S3 data from Redshift without loading
- **Glue**: ETL service with Data Catalog for S3 data discovery

No data movement required—all query S3 directly.

### Why other options are incorrect:

- **A** - Redshift (not Spectrum) requires data loading into clusters.

- **B** - Neptune is a graph database; DAX is DynamoDB cache. Neither analyzes S3.

- **C** - X-Ray is for tracing; Neptune and DynamoDB aren't S3 analytics tools.

## References

- https://docs.aws.amazon.com/athena/latest/ug/what-is.html
- https://docs.aws.amazon.com/redshift/latest/dg/c-using-spectrum.html
- https://tutorialsdojo.com/amazon-athena/

## Domain

Design Resilient Architectures
