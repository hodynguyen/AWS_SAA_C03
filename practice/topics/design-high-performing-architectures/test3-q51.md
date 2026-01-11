# Question 51

## Topic
Design High-Performing Architectures

## Question
A company needs to collect gigabytes of data per second from websites and social media feeds to gain insights into its product offerings and continuously improve the user experience. To meet this design requirement, an application is deployed on an Auto Scaling group of Spot EC2 instances which processes the data and stores the results to DynamoDB and Redshift. The solution should have a built-in enhanced fan-out feature.

Which fully-managed AWS service can you use to collect and process large streams of data records in real-time with the LEAST amount of administrative overhead?

## Options
A. Amazon S3 Access Points

B. Amazon Kinesis Data Streams

C. Amazon Managed Streaming for Apache Kafka (Amazon MSK)

D. AWS Data Exchange

## Correct Answer
B

## Explanation
Amazon Kinesis Data Streams is used to collect and process large streams of data records in real-time. You can use Kinesis Data Streams for rapid and continuous data intake and aggregation. The type of data used includes IT infrastructure log data, application logs, social media, market data feeds, and web clickstream data. Because the response time for the data intake and processing is in real-time, the processing is typically lightweight.

The following diagram illustrates the high-level architecture of Kinesis Data Streams. The producers continually push data to Kinesis Data Streams, and the consumers process the data in real-time. Consumers (such as a custom application running on Amazon EC2 or an Amazon Data Firehose stream) can store their results using an AWS service such as Amazon DynamoDB, Amazon Redshift, or Amazon S3.

Hence, the correct answer is: Amazon Kinesis Data Streams.

Amazon S3 Access Points is incorrect because this is mainly used to manage access of your S3 objects. Amazon S3 access points are named network endpoints that are attached to buckets that you can use to perform S3 object operations, such as uploading and retrieving objects.

AWS Data Exchange is incorrect because this is just a data marketplace service.

Amazon Managed Streaming for Apache Kafka (Amazon MSK) is incorrect. Although you can process streaming data in real-time with Amazon MSK, this service still entails a lot of administrative overhead, unlike Amazon Kinesis. Moreover, it doesn't have a built-in enhanced fan-out feature as required in the scenario.

## References
- https://docs.aws.amazon.com/streams/latest/dev/introduction.html
- https://aws.amazon.com/kinesis/
- https://tutorialsdojo.com/amazon-kinesis/
- https://tutorialsdojo.com/aws-certified-solutions-architect-associate/
