# Question 44

Log files stored for 12 hours only. Unknown number of files.

Which is the most cost-effective S3 storage class?

## Options

A. S3 One Zone-IA.

B. S3 Standard-IA.

C. S3 Glacier Deep Archive.

D. S3 Standard.

## Correct Answer

**D. S3 Standard.**

## Explanation

S3 Standard for short-term:
- **No minimum duration**: Pay only for 12 hours
- **Other classes**: 30, 90, or 180 day minimums
- **Cost-effective**: For very short storage
- **High durability**: 99.999999999%

### Why other options are incorrect:

- **A, B** - 30-day minimum; charged for full period.

- **C** - 180-day minimum; expensive for 12 hours.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/dev/storage-class-intro.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Cost-Optimized Architectures
