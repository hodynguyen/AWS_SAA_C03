# Question 4

A data analytics startup stores clickstream data in S3. An AWS Lambda function should trigger ETL jobs when new data arrives.

Which service can be used for ETL?

## Options

A. AWS Step Functions

B. AWS Glue

C. Redshift Spectrum

D. S3 Select

## Correct Answer

**B. AWS Glue**

## Explanation

AWS Glue is a fully managed ETL service:
- **Serverless**: No infrastructure to manage
- **Auto-generates code**: Python/Scala ETL scripts
- **Data Catalog**: Discovers schema automatically
- **S3 integration**: Reads from and writes to S3

Lambda can trigger Glue jobs when new S3 objects arrive.

### Why other options are incorrect:

- **A** - Step Functions orchestrates workflows, not ETL transformation.

- **C** - Redshift Spectrum queries S3 from Redshift, not for ETL.

- **D** - S3 Select retrieves subsets of data, not ETL transformation.

## References

- https://aws.amazon.com/glue/
- https://tutorialsdojo.com/aws-glue/

## Domain

Design Resilient Architectures
