# Question 4

## Topic
Design High-Performing Architectures

## Question
A document sharing website is using AWS as its cloud infrastructure. Free users can upload a total of 5 GB data while premium users can upload as much as 5 TB. Their application uploads the user files, which can have a max file size of 1 TB, to an S3 Bucket.

In this scenario, what is the best way for the application to upload the large files in S3?

## Options
A. Use a single PUT request to upload the large file

B. Use Multipart Upload

C. Use AWS Import/Export

D. Use AWS Snowball

## Correct Answer
B

## Explanation
The total volume of data and number of objects you can store are unlimited. Individual Amazon S3 objects can range in size from a minimum of 0 bytes to a maximum of 5 terabytes. The largest object that can be uploaded in a single PUT is 5 gigabytes. For objects larger than 100 megabytes, customers should consider using the Multipart Upload capability.

The Multipart upload API enables you to upload large objects in parts. You can use this API to upload new large objects or make a copy of an existing object. Multipart uploading is a three-step process: you initiate the upload, you upload the object parts, and after you have uploaded all the parts, you complete the multipart upload.

**Why other options are incorrect:**
- **Option A** is incorrect because the largest file size you can upload using a single PUT request is 5 GB.
- **Option C** is incorrect because Import/Export is meant to be used as a migration tool, not for multiple customer consumption.
- **Option D** is incorrect because Snowball is a migration tool for transferring large amounts of data from on-premises to AWS, not suitable for ongoing customer uploads.

## References
- https://docs.aws.amazon.com/AmazonS3/latest/dev/mpuoverview.html
- https://aws.amazon.com/s3/faqs/
- https://tutorialsdojo.com/amazon-s3/
