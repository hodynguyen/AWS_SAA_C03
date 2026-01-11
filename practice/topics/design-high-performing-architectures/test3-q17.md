# Question 17

## Topic
Design High-Performing Architectures

## Question
A media company recently launched their newly created web application. Many users tried to visit the website, but they are receiving a 503 Service Unavailable Error. The system administrator tracked the EC2 instance status and saw the capacity is reaching its maximum limit and unable to process all the requests. To gain insights from the application's data, they need to launch a real-time analytics service.

Which of the following allows you to read records in batches?

## Options
A. Create a Data Firehose and use AWS Lambda to read records from the data stream.

B. Create a Kinesis Data Stream and use AWS Lambda to read records from the data stream.

C. Create an Amazon S3 bucket to store the captured data and use Amazon Redshift Spectrum to analyze the data.

D. Create an Amazon S3 bucket to store the captured data and use Amazon Athena to analyze the data.

## Correct Answer
B

## Explanation
Amazon Kinesis Data Streams (KDS) is a massively scalable and durable real-time data streaming service. You can use an AWS Lambda function to process records in Amazon KDS. By default, Lambda invokes your function as soon as records are available in the stream. Lambda can process up to 10 batches in each shard simultaneously.

Since the media company needs a real-time analytics service, you can use Kinesis Data Streams to gain insights from your data. The data collected is available in milliseconds. Use AWS Lambda to read records in batches.

**Why other options are incorrect:**
- **Option A** is incorrect because AWS Lambda can't be set as destination for Data Firehose to read records.
- **Option C and D** are incorrect because the company needs real-time analytics, not batch analysis with S3.

## References
- https://aws.amazon.com/kinesis/data-streams/
- https://docs.aws.amazon.com/lambda/latest/dg/with-kinesis.html
- https://tutorialsdojo.com/amazon-kinesis/
