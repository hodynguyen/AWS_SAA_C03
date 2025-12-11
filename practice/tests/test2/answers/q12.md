# Question 12

A company launched a website that accepts high-quality photos and turns the photos into a downloadable video montage. The website offers both a free and a premium account, with the premium account guaranteeing faster processing. All requests by both free and premium members go through a single Amazon SQS queue and are then processed by a group of Amazon EC2 instances that generate the videos. The company needs to ensure that premium users, who paid for the service, have higher priority than free members.

How should the company re-design its architecture to address this requirement?

## Options

A. Create an SQS queue for free members and another one for premium members. Configure your EC2 instances to consume messages from the premium queue first and if it is empty, poll from the free members' SQS queue.

B. For the requests made by premium members, set a higher priority in the SQS queue so it will be processed first compared to the requests made by free members.

C. Use Amazon S3 to store and process the photos and then generate the video montage afterward.

D. Use Amazon Kinesis to process the photos and generate the video montage in real-time.

## Correct Answer

**A. Create an SQS queue for free members and another one for premium members. Configure your EC2 instances to consume messages from the premium queue first and if it is empty, poll from the free members' SQS queue.**

## Explanation

Create 2 separate SQS queues for each type of member. The SQS queues for the premium members can be polled first by the EC2 Instances and once completed, the messages from the free members can be processed next.

### Why other options are incorrect:

- **B** - You cannot set priority to individual items in SQS.

- **D** - Kinesis is for streaming data, not photo processing.

- **C** - S3 is for storage, not processing.

## References

- https://aws.amazon.com/sqs/
- https://tutorialsdojo.com/amazon-sqs/

## Domain

Design High-Performing Architectures
