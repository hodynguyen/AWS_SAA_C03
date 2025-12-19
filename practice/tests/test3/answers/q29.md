# Question 29

## Topic
Design Resilient Architectures

## Question
A production MySQL database hosted on Amazon RDS is running out of disk storage. The management has consulted its solutions architect to increase the disk space without impacting the database performance.

How can the solutions architect satisfy the requirement with the LEAST operational overhead?

## Options
A. Change the default_storage_engine of the DB instance's parameter group to MyISAM.

B. Modify the DB instance storage type to Provisioned IOPS.

C. Modify the DB instance settings and enable storage autoscaling.

D. Increase the allocated storage for the DB instance.

## Correct Answer
C

## Explanation
RDS Storage Auto Scaling automatically scales storage capacity in response to growing database workloads, with zero downtime. Under-provisioning could result in application downtime, and over-provisioning could result in underutilized resources and higher costs.

With RDS Storage Auto Scaling, you simply set your desired maximum storage limit, and Auto Scaling takes care of the rest. There is no additional cost for RDS Storage Auto Scaling.

**Why other options are incorrect:**
- **Option A** is incorrect because changing the storage engine won't increase disk space.
- **Option B** is incorrect because this may improve disk performance but won't solve the storage issue.
- **Option D** is incorrect because this requires monitoring and manual intervention, adding operational overhead.

## References
- https://aws.amazon.com/about-aws/whats-new/2019/06/rds-storage-auto-scaling/
- https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PIOPS.StorageTypes.html#USER_PIOPS.Autoscaling
- https://tutorialsdojo.com/amazon-relational-database-service-amazon-rds/
