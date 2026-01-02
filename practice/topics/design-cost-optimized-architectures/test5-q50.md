# Question 50

Wearable device sends 1 MB/day to S3. Processing needs 512 MB memory and must complete in 10 seconds.

Which is the most cost-effective solution?

## Options

A. Lambda with Python library.

B. AWS Glue PySpark job.

C. Redshift with Lambda processing.

D. Firehose to S3, then EC2 processing.

## Correct Answer

**A. Lambda with Python library.**

## Explanation

Lambda advantages:
- **Pay per use**: Only pay for execution time
- **Millisecond billing**: Perfect for 10-second jobs
- **S3 integration**: Trigger on object upload
- **512 MB memory**: Within Lambda limits
- **No infrastructure**: Fully serverless

### Why other options are incorrect:

- **B** - Glue has 1-minute minimum billing; overkill for 1 MB.

- **C** - Redshift is data warehouse; expensive for small data.

- **D** - Firehose + EC2 adds complexity and cost.

## References

- https://aws.amazon.com/lambda/pricing/
- https://tutorialsdojo.com/aws-lambda/

## Domain

Design Cost-Optimized Architectures
