# Question 55

## Topic
Design Resilient Architectures

## Question
An online stock trading application stores financial data in an Amazon S3 bucket, with a lifecycle policy that moves older data to Glacier every month. A strict compliance requirement mandates that a surprise audit can occur at any time, and the required data must be retrievable in under 15 minutes under all circumstances. The manager has instructed that retrieval capacity be available when needed and should support up to 150 MB/s of retrieval throughput.

Which of the following will meet the given requirement? (Select TWO.)

## Options
A. Purchase provisioned retrieval capacity.

B. Use Expedited Retrieval to access the financial data.

C. Use Bulk Retrieval to access the financial data.

D. Use Standard Retrieval for accessing the financial data.

E. Specify a range, or portion, of the financial data archive to retrieve.

## Correct Answers
A, B

## Explanation
Expedited retrievals allow you to quickly access your data when occasional urgent requests for a subset of archives are required. For all but the largest archives (250 MB+), data accessed using Expedited retrievals are typically made available within 1–5 minutes. Provisioned Capacity ensures that retrieval capacity for Expedited retrievals is available when you need it.

To make an Expedited, Standard, or Bulk retrieval, set the Tier parameter in the Initiate Job (POST jobs) REST API request to the option you want, or the equivalent in the AWS CLI or AWS SDKs. If you have purchased provisioned capacity, then all expedited retrievals are automatically served through your provisioned capacity.

Provisioned capacity ensures that your retrieval capacity for expedited retrievals is available when you need it. Each unit of capacity provides that at least three expedited retrievals can be performed every five minutes and provides up to 150 MB/s of retrieval throughput. You should purchase provisioned retrieval capacity if your workload requires highly reliable and predictable access to a subset of your data in minutes. Without provisioned capacity Expedited retrievals are accepted, except for rare situations of unusually high demand. However, if you require access to Expedited retrievals under all circumstances, you must purchase provisioned retrieval capacity.

Amazon S3 Glacier - Data retrieval settings

Hence, the correct answers are:
- Use Expedited Retrieval to access the financial data.
- Purchase provisioned retrieval capacity.

The option that says: Use Standard Retrieval for accessing the financial data is incorrect because standard retrieval typically takes 3–5 hours, which does not meet the audit's rapid retrieval time requirement.

The option that says: Use Bulk Retrieval to access the financial data is incorrect because bulk retrievals typically complete within 5–12 hours hence, this does not satisfy the requirement of retrieving the data within 15 minutes. The provisioned capacity option is also not compatible with Bulk retrievals.

The option that says: Specify a range, or portion, of the financial data archive to retrieve is incorrect because using ranged archive retrievals is not enough to meet the requirement of retrieving the whole archive in the given timeframe. In addition, it does not primarily provide additional retrieval capacity which is what the provisioned capacity option can offer.

## References
- https://docs.aws.amazon.com/amazonglacier/latest/dev/downloading-an-archive-two-steps.html
- https://docs.aws.amazon.com/AmazonS3/latest/userguide/restoring-objects-retrieval-options.html
- https://tutorialsdojo.com/amazon-glacier/
