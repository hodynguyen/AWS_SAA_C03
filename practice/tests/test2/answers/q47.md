# Question 47

A company is implementing a disaster recovery strategy. They need to ensure that data from an Amazon Aurora MySQL database can be recovered in a secondary AWS Region.

Which approach provides the MOST operationally efficient solution?

## Options

A. Create manual snapshots and copy them to the secondary region.

B. Configure an Aurora Global Database with a secondary read replica in another Region.

C. Use AWS DataSync to replicate the database.

D. Set up cross-region replication using Amazon S3.

## Correct Answer

**B. Configure an Aurora Global Database with a secondary read replica in another Region.**

## Explanation

Aurora Global Database enables a single Aurora database to span multiple AWS Regions with less than 1 second of replication lag. In disaster recovery, you can promote the secondary region in less than 1 minute.

### Why other options are incorrect:

- **A** - Manual snapshots require more operational effort.

- **C** - DataSync is for file data, not databases.

- **D** - S3 replication is for objects, not Aurora.

## References

- https://aws.amazon.com/rds/aurora/global-database/
- https://tutorialsdojo.com/amazon-aurora/

## Domain

Design Resilient Architectures
