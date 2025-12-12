# Question 17

A media company hosts large volumes of archive data that are about 250 TB in size on its internal servers. The company has decided to move this data to Amazon S3 because of its durability and redundancy. The company currently has a 100 Mbps dedicated line connecting its head office to the Internet.

Which of the following is the FASTEST and MOST COST-EFFECTIVE way to import all this data to S3?

## Options

A. Request several AWS Snowball devices to upload the data into S3.

B. Upload it directly to S3

C. Use S3 Transfer Acceleration to speed up the upload.

D. Establish a direct connection using AWS Direct Connect, then transfer the data over to S3.

## Correct Answer

**A. Request several AWS Snowball devices to upload the data into S3.**

## Explanation

AWS Snowball is a petabyte-scale data transport solution that uses secure appliances to transfer large amounts of data into and out of AWS.

As a rule of thumb, if it takes more than one week to upload your data to AWS using your existing Internet connection, you should consider using Snowball.

### Why other options are incorrect:

- **B** - Direct upload would take too long with slow Internet.

- **D** - Provisioning Direct Connect takes too much time.

- **C** - Transfer Acceleration doesn't significantly boost speeds for large datasets on limited bandwidth.

## References

- https://aws.amazon.com/snowball/
- https://tutorialsdojo.com/aws-snowball/

## Domain

Design Cost-Optimized Architectures
