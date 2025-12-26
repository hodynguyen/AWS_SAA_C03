# Question 29

## Topic
Design High-Performing Architectures

## Question
A company has a web-based order processing system that is currently using a standard queue in Amazon SQS. The IT Manager noticed that there are a lot of cases where an order was processed twice. This issue has caused a lot of trouble in processing and made the customers very unhappy. The goal is to ensure that this issue will not recur.

What solution should be implemented to prevent this from happening again in the future?

## Options
A. Use an SQS FIFO Queue instead.

B. Alter the retention period in SQS.

C. Change the message size in SQS.

D. Alter the visibility timeout of SQS.

## Correct Answer
A

## Explanation
Amazon SQS FIFO (First-In-First-Out) Queues have all the capabilities of the standard queue with additional capabilities designed to enhance messaging between applications when the order of operations and events is critical or where duplicates can't be tolerated, for example:

- Ensure that user-entered commands are executed in the right order.

- Display the correct product price by sending price modifications in the right order.

- Prevent a student from enrolling in a course before registering for an account.

Standard Queue vs. FIFO Queue

Amazon Simple Queue Service (SQS) provides two types of queues: Standard Queues and FIFO (First-In-First-Out) Queues. Standard Queues allow for at-least-once delivery, meaning messages might sometimes be duplicated. This can lead to situations where an order is processed more than once.

Amazon SQS FIFO Queues guarantee that messages are processed exactly once and in the same order they were sent. FIFO queues eliminate the issue of duplicated messages by ensuring that each message is delivered only once using deduplication and message sequencing mechanisms.

The main issue in this scenario is that the order management system produces duplicate orders at times. Since the company is using a standard queue in Amazon SQS, there is a possibility that a message can have a duplicate in case an EC2 instance fails to delete the already processed message.

Hence, the correct answer is: Use an Amazon SQS FIFO Queue instead.

References:

https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-queue-types.html

https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/FIFO-queues-exactly-once-processing.html

https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html

Check out this Amazon SQS Cheat Sheet:

https://tutorialsdojo.com/amazon-sqs/

**Why other options are incorrect:**

- The option that says: Alter the retention period in SQS is incorrect because the retention period simply specifies if Amazon SQS should delete the messages that have been in a queue for a certain period of time.

- The option that says: Alter the visibility timeout of SQS is incorrect because, for standard queues, the visibility timeout isn't a guarantee against receiving a message twice. To avoid duplicate SQS messages, it is better to design your applications to be idempotent (they should not be affected adversely when processing the same message more than once).

- The option that says: Change the message size in SQS is incorrect because this is not related at all in this scenario. Adjusting the message size does not impact message duplication. The issue is primarily caused by at-least-once delivery, not by message size limitations.

