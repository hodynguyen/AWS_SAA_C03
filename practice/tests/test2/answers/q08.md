# Question 8

A company plans to migrate all of their applications to AWS. The Solutions Architect suggested to store all the data to EBS volumes. The Chief Technical Officer is worried that EBS volumes are not appropriate for the existing workloads due to compliance requirements, downtime scenarios, and IOPS performance.

Which of the following are valid points in proving that EBS is the best service to use for migration? (Select TWO.)

## Options

A. EBS volumes can be attached to any EC2 Instance in any Availability Zone.

B. Amazon EBS provides the ability to create snapshots (backups) of any EBS volume and write a copy of the data in the volume to Amazon RDS, where it is stored redundantly in multiple Availability Zones.

C. An EBS volume is off-instance storage that can persist independently from the life of an instance.

D. EBS volumes support live configuration changes while in production which means that you can modify the volume type, volume size, and IOPS capacity without service interruptions.

E. When you create an EBS volume in an Availability Zone, it is automatically replicated on a separate AWS region to prevent data loss due to a failure of any single hardware component.

## Correct Answers

**C. An EBS volume is off-instance storage that can persist independently from the life of an instance.**

**D. EBS volumes support live configuration changes while in production which means that you can modify the volume type, volume size, and IOPS capacity without service interruptions.**

## Explanation

EBS volumes are durable, block-level storage devices. Key features:
- Persist independently from EC2 instance life
- Support live configuration changes (type, size, IOPS)
- Replicated within the same AZ
- Support encryption with AES-256
- Offer 99.999% SLA

### Why other options are incorrect:

- **A** - EBS can only attach to EC2 in the same AZ.

- **B** - Snapshots go to S3, not RDS.

- **E** - Replication is within the same AZ, not across regions.

## References

- http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSVolumes.html
- https://tutorialsdojo.com/amazon-ebs/

## Domain

Design Resilient Architectures
