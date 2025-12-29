# Question 2

A company has 200 TB of backup files in Amazon S3 in a proprietary format. They need to use vendor software to convert files to a standard format and re-upload to S3. The solution must minimize data transfer costs.

Which option satisfies this requirement?

## Options

A. Deploy the EC2 instance in the same Region as Amazon S3. Install the file conversion software on the instance. Perform data transformation and re-upload it to Amazon S3.

B. Deploy the EC2 instance in a different Region. Install the conversion software on the instance. Perform data transformation and re-upload it to Amazon S3.

C. Install the file conversion software in Amazon S3. Use S3 Batch Operations to perform data transformation.

D. Export the data using AWS Snowball Edge device. Install the file conversion software on the device. Transform the data and re-upload it to Amazon S3.

## Correct Answer

**A. Deploy the EC2 instance in the same Region as Amazon S3. Install the file conversion software on the instance. Perform data transformation and re-upload it to Amazon S3.**

## Explanation

Data transfer between S3 and EC2 within the same AWS Region is free. By deploying the EC2 instance in the same region as the S3 bucket, the company avoids data transfer charges for both downloading and re-uploading the 200 TB of files.

### Why other options are incorrect:

- **B** - Deploying EC2 in a different region incurs cross-region data transfer charges.

- **C** - You cannot install custom software in S3. S3 Batch Operations cannot run proprietary conversion software.

- **D** - Snowball is for transferring data to/from on-premises. There's no on-premises data center mentioned in this scenario.

## References

- https://aws.amazon.com/s3/pricing/
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Cost-Optimized Architectures
