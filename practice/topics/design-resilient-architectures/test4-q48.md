# Question 48

## Topic
Design Resilient Architectures

## Question
A company has a set of Linux servers running on multiple On-Demand EC2 Instances. The Audit team wants to collect and process the application log files generated from these servers for their report.

Which of the following services is best to use in this case?

## Options
A. Amazon S3 for storing the application log files and Amazon Elastic MapReduce for processing the log files.

B. A single On-Demand Amazon EC2 instance for both storing and processing the log files

C. Amazon S3 Glacier Deep Archive for storing the application log files and AWS ParallelCluster for processing the log files.

D. Amazon S3 Glacier for storing the application log files and Spot EC2 Instances for processing them.

## Correct Answer
A

## Explanation
Amazon EMR is a managed cluster platform that simplifies running big data frameworks, such as Apache Hadoop and Apache Spark, on AWS to process and analyze vast amounts of data. By using these frameworks and related open-source projects such as Apache Hive and Apache Pig, you can process data for analytics purposes and business intelligence workloads. Additionally, you can use Amazon EMR to transform and move large amounts of data into and out of other AWS data stores and databases such as Amazon Simple Storage Service (Amazon S3) and Amazon DynamoDB.

Hence, the correct answer is: Amazon S3 for storing the application log files and Amazon Elastic MapReduce for processing the log files.

References:

http://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html

https://aws.amazon.com/hpc/parallelcluster/

Check out this Amazon EMR Cheat Sheet:

https://tutorialsdojo.com/amazon-emr/

**Why other options are incorrect:**

- The option that says: Amazon S3 Glacier for storing the application log files and Spot EC2 Instances for processing them is incorrect as Amazon S3 Glacier is used for data archive only.

- The option that says: A single On-Demand Amazon EC2 instance for both storing and processing the log files is incorrect as an EC2 instance is not a recommended storage service. In addition, Amazon EC2 does not have a built-in data processing engine to process large amounts of data.

- The option that says: Amazon S3 Glacier Deep Archive for storing the application log files and AWS ParallelCluster for processing the log files is incorrect because the long retrieval time of Amazon S3 Glacier Deep Archive makes this option unsuitable. Moreover, AWS ParallelCluster is just an AWS-supported open-source cluster management tool that makes it easy for you to deploy and manage High-Performance Computing (HPC) clusters on AWS. ParallelCluster uses a simple text file to model and provision all the resources needed for your HPC applications in an automated and secure manner.

