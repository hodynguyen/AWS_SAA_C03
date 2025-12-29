# Question 21

A company runs performance testing on a large RDS MySQL instance twice a week. They need to reduce operational costs without compromising test integrity.

What is the most cost-effective solution?

## Options

A. Perform mysqldump to a local machine and use MySQL Workbench for analysis.

B. Downgrade the database to a smaller instance.

C. Stop the database when testing is done and restart when necessary.

D. Take a snapshot of the database and terminate it. Restore from snapshot when necessary.

## Correct Answer

**D. Take a snapshot of the database and terminate it. Restore from snapshot when necessary.**

## Explanation

RDS snapshots capture the complete database state. By terminating the instance after testing:
- **No compute costs** during idle periods (5 days/week)
- **Snapshot storage** is inexpensive (~$0.05/GB-month)
- **Full restoration** preserves data and configurations for the next test

### Why other options are incorrect:

- **A** - Local testing doesn't replicate RDS environment/resources, compromising test integrity.

- **B** - Smaller instances may not handle the workload, affecting test accuracy.

- **C** - Stopped instances still incur storage costs. Terminating + snapshot is cheaper.

## References

- https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_CreateSnapshot.html
- https://tutorialsdojo.com/amazon-rds/

## Domain

Design Cost-Optimized Architectures
