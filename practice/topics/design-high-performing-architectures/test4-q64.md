# Question 64

## Topic
Design High-Performing Architectures

## Question
A company plans to develop a custom messaging service that will be used to train an AI for an automatic response feature. The service is expected to receive thousands of messages per day, all of which will be processed by an Amazon EMR cluster. It is crucial that none of the messages are lost, no duplicates are produced, and that the messages are processed in EMR in the same order as their arrival.

Which of the following options can satisfy the given requirement?

## Options
A. Create an Amazon Data Firehose to handle the messages.

B. Set up a default Amazon SQS queue to handle the messages.

C. Create an Amazon Kinesis Data Stream to collect the messages.

D. Set up an Amazon SNS Topic to handle the messages.

## Correct Answer
C

## Explanation
Two important requirements that the chosen AWS service should fulfill is that data should not go missing, is durable, and streams data in the sequence of arrival. Kinesis can do the job just fine because of its architecture. A Kinesis data stream is a set of shards that has a sequence of data records, and each data record has a sequence number that is assigned by Kinesis Data Streams. Kinesis can also easily handle the high volume of messages being sent to the service.

Amazon Kinesis Data Streams enables real-time processing of streaming big data. It provides ordering of records, as well as the ability to read and/or replay records in the same order to multiple Amazon Kinesis Applications. The Amazon Kinesis Client Library (KCL) delivers all records for a given partition key to the same record processor, making it easier to build multiple applications reading from the same Amazon Kinesis data stream (for example, to perform counting, aggregation, and filtering).

References:

https://docs.aws.amazon.com/streams/latest/dev/introduction.html

https://aws.amazon.com/kinesis/data-streams/faqs/

Check out this Amazon Kinesis Cheat Sheet:

https://tutorialsdojo.com/amazon-kinesis/

**Why other options are incorrect:**

- The option that says: Set up a default Amazon SQS queue to handle the messages is incorrect because although SQS is a valid messaging service, it is not suitable for scenarios where you need to process the data based on the order they were received. Take note that a default queue in SQS is just a standard queue and not a FIFO (First-In-First-Out) queue. In addition, SQS does not guarantee that no duplicates will be sent.

- The option that says: Set up an Amazon SNS Topic to handle the messages is incorrect because SNS is a pub-sub messaging service in AWS. SNS might not be capable of handling such a large volume of messages being received and sent at a time. It does not also guarantee that the data will be transmitted in the same order they were received.

- The option that says: Create an Amazon Data Firehose to handle the messages is incorrect because Amazon Data Firehose is primarily designed for delivering real-time streaming data to destinations such as data lakes, data stores, and analytics services. It ensures reliable data delivery, but it doesn't guarantee the order of message delivery and processing.

