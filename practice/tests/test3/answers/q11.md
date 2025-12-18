# Question 11

## Topic
Design Resilient Architectures

## Question
A company installed sensors to track the number of people who visit the park. The data is sent every day to an Amazon Kinesis stream with default settings for processing, in which a consumer is configured to process the data every other day. You noticed that the S3 bucket is not receiving all of the data that is being sent to the Kinesis stream. You checked the sensors if they are properly sending the data to Amazon Kinesis and verified that the data is indeed sent every day.

What could be the reason for this?

## Options
A. There is a problem in the sensors. They probably had some intermittent connection hence, the data is not sent to the stream.

B. By default, the data records are only accessible for 24 hours from the time they are added to a Kinesis stream.

C. By default, Amazon S3 stores the data for 1 day and moves it to Amazon Glacier.

D. Your AWS account was hacked and someone has deleted some data in your Kinesis stream.

## Correct Answer
B

## Explanation
Kinesis Data Streams supports changes to the data record retention period of your stream. A Kinesis data stream is an ordered sequence of data records meant to be written to and read from in real-time.

The time period from when a record is added to when it is no longer accessible is called the retention period. A Kinesis data stream stores records from 24 hours by default to a maximum of 8760 hours (365 days).

Since the consumer processes data every other day (48 hours) but the default retention is 24 hours, data is being lost.

**Why other options are incorrect:**
- **Option A** is incorrect because you already verified that the sensors are working properly.
- **Option C** is incorrect because Amazon S3 does not store data for 1 day only and move it to Glacier by default.
- **Option D** is incorrect because while possible, you should verify other more probable reasons first.

## References
- http://docs.aws.amazon.com/streams/latest/dev/kinesis-extended-retention.html
- https://tutorialsdojo.com/amazon-kinesis/
