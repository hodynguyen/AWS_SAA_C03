# Question 22

## Topic
Design Resilient Architectures

## Question
A real-time data analytics application is using AWS Lambda to process data and store results in JSON format to an S3 bucket. To speed up the existing workflow, you have to use a service where you can run sophisticated Big Data analytics on your data without moving them into a separate analytics system.

Which of the following group of services can you use to meet this requirement?

## Options
A. Amazon Glue, Amazon Redshift, Amazon S3

B. Amazon Neptune, DynamoDB DAX, Amazon Redshift Spectrum

C. Amazon X-Ray, Amazon Neptune, DynamoDB

D. Amazon Athena, Amazon Redshift Spectrum, AWS Glue

## Correct Answer
D

## Explanation
Amazon Athena, Amazon Redshift Spectrum, and AWS Glue are highly relevant services for performing Big Data analytics directly on data stored in Amazon S3, without needing to move the data to a separate system.

Amazon Athena allows users to query data directly in Amazon S3 using SQL, providing a serverless approach to perform analytics on S3-stored data in formats such as JSON.

Amazon Redshift Spectrum extends the querying capabilities of Amazon Redshift to also access and analyze structured and semi-structured data in S3, supporting large-scale analytics.

AWS Glue is a fully managed ETL (Extract, Transform, Load) service that helps catalog, prepare, and transform data in S3 for analytics, simplifying Big Data workflows.

These services together provide an efficient way to perform sophisticated analytics on S3-stored data without moving it, which fits the scenario requirements.

Hence, the correct answer is: Amazon Athena, Amazon Redshift Spectrum, AWS Glue.

Reference:

https://docs.aws.amazon.com/athena/latest/ug/what-is.html

https://docs.aws.amazon.com/redshift/latest/dg/c-using-spectrum.html

https://docs.aws.amazon.com/glue/latest/dg/what-is-glue.html

Amazon Redshift Overview:

Check out these Amazon Athena, Amazon Redshift, and AWS Glue Cheat Sheets:

https://tutorialsdojo.com/amazon-athena/

https://tutorialsdojo.com/amazon-redshift/

https://tutorialsdojo.com/aws-glue/

**Why other options are incorrect:**

- The option that says: Amazon Neptune, DynamoDB DAX, Amazon Redshift Spectrum is incorrect because Amazon Neptune and DynamoDB DAX simply do not support analytics or querying capabilities on data stored in S3. They are used for graph databases and caching, respectively.

- The option that says: Amazon X-Ray, Amazon Neptune, DynamoDB is incorrect because Amazon X-Ray is only a tracing service, and Neptune and DynamoDB are not relevant for analytics on S3 data.

- The option that says: Amazon Glue, Amazon Redshift, Amazon S3 is incorrect. This option is only partially correct. While Glue can transform and catalog data in S3 and S3 provides storage, Redshift requires data to be loaded into its cluster for analytics. This contradicts the requirement to perform analytics directly on data in S3 without moving it.

