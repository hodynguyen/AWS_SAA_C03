# Question 51

A company collects atmospheric data such as temperature, air pressure, and humidity from different countries. Each site location is equipped with various weather instruments and a high-speed Internet connection. The average collected data in each location is around 500 GB and will be analyzed by a weather forecasting application hosted in Northern Virginia. The Solutions Architect must determine the fastest way to aggregate all the data.

Which of the following options can satisfy the given requirement?

## Options

A. Set up a Site-to-Site VPN connection.

B. Use AWS Snowball Edge to transfer large amounts of data.

C. Enable Transfer Acceleration in the destination bucket and upload the collected data using Multipart Upload.

D. Upload the data to the closest Amazon S3 bucket. Set up a cross-region replication and copy the objects to the destination bucket.

## Correct Answer

**C. Enable Transfer Acceleration in the destination bucket and upload the collected data using Multipart Upload.**

## Explanation

With Amazon S3 Transfer Acceleration, you can speed up content transfers to and from Amazon S3 by as much as 50-500% for long-distance transfer of larger objects. Multipart upload allows you to upload a single object as a set of parts.

This approach is the fastest way to aggregate all the data.

### Why other options are incorrect:

- **D** - Cross-region replication typically takes about 15 minutes. Not the fastest option.

- **B** - AWS Snowball Edge end-to-end transfer time is approximately one week for 80 TB.

- **A** - VPN connection is not needed and is not the fastest method for data transfer.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/dev/transfer-acceleration.html
- https://docs.aws.amazon.com/AmazonS3/latest/dev/replication.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design High-Performing Architectures
