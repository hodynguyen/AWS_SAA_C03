# Question 48

A company has Linux EC2 instances generating application logs. The Audit team needs to collect and process these log files.

Which services should be used?

## Options

A. Amazon S3 for storage and Amazon EMR for processing.

B. A single EC2 instance for storage and processing.

C. S3 Glacier Deep Archive for storage and AWS ParallelCluster for processing.

D. S3 Glacier for storage and Spot instances for processing.

## Correct Answer

**A. Amazon S3 for storage and Amazon EMR for processing.**

## Explanation

- **S3**: Scalable, durable storage for log files with immediate access
- **Amazon EMR**: Managed Hadoop/Spark for big data processing, ideal for log analysis

EMR can directly process data from S3 and output results back to S3.

### Why other options are incorrect:

- **B** - EC2 is not a storage service. Single instance has no durability or scalability.

- **C** - Glacier Deep Archive has long retrieval times (12+ hours). ParallelCluster is for HPC, not log processing.

- **D** - Glacier is for archival, not active log processing.

## References

- http://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html
- https://tutorialsdojo.com/amazon-emr/

## Domain

Design Resilient Architectures
