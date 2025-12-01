# Question 5

A company plans to host a web application in an Auto Scaling group of Amazon EC2 instances. The application will be used globally by users to upload and store several types of files. Based on user trends, files that are older than 2 years must be stored in a different storage class. The Solutions Architect of the company needs to create a cost-effective and scalable solution to store the old files yet still provide durability and high availability.

Which of the following approach can be used to fulfill this requirement? (Select TWO.)

## Options

A. Use a RAID 0 storage configuration that stripes multiple Amazon EBS volumes together to store the files. Configure the Amazon Data Lifecycle Manager (DLM) to schedule snapshots of the volumes after 2 years.

B. Use Amazon EBS volumes to store the files. Configure the Amazon Data Lifecycle Manager (DLM) to schedule snapshots of the volumes after 2 years.

C. Use Amazon S3 and create a lifecycle policy that will move the objects to S3 Standard-IA after 2 years.

D. Use Amazon S3 and create a lifecycle policy that will move the objects to S3 Glacier after 2 years.

E. Use Amazon EFS and create a lifecycle policy that will move the objects to EFS-IA after 2 years.

## Correct Answers

**C. Use Amazon S3 and create a lifecycle policy that will move the objects to S3 Standard-IA after 2 years.**

**D. Use Amazon S3 and create a lifecycle policy that will move the objects to S3 Glacier after 2 years.**

## Explanation

Amazon S3 stores data as objects within buckets. To move a file to a different storage class, you can use Amazon S3 or Amazon EFS. Both services have lifecycle configurations.

Take note that Amazon EFS can only transition a file to the IA storage class after 90 days. Since you need to move the files that are older than 2 years to a more cost-effective and scalable solution, you should use the Amazon S3 lifecycle configuration. With S3 lifecycle rules, you can transition files to S3 Standard IA or S3 Glacier.

### Why other options are incorrect:

- **E** - The maximum days of EFS lifecycle policies is only up to 365 days. Therefore, it still does not meet the requirement of moving files older than 2 years or 730 days.

- **B** - Amazon EBS simply costs more and is not as scalable as Amazon S3. It has limitations when accessed by multiple EC2 instances.

- **A** - RAID is just a data storage virtualization technology that combines multiple storage devices. It doesn't address the lifecycle management requirement.

## References

- https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html
- https://docs.aws.amazon.com/efs/latest/ug/lifecycle-management-efs.html
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Resilient Architectures
