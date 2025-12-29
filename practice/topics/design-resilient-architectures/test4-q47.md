# Question 47

A company uses Redshift for their data warehouse. They need a disaster recovery plan that ensures business continuity even during an AWS region outage.

What is the best approach?

## Options

A. Enable Cross-Region Snapshots Copy in Redshift.

B. Do nothing because Redshift is highly available and can withstand region outages.

C. Use Automated snapshots of your Redshift Cluster.

D. Create a scheduled job to take snapshots and store in S3.

## Correct Answer

**A. Enable Cross-Region Snapshots Copy in Redshift.**

## Explanation

Cross-region snapshot copy:
- **Automatic replication**: Snapshots copied to another region automatically
- **Region failure protection**: Restore cluster in another region if primary fails
- **Configurable retention**: Control how long snapshots are kept in destination region

### Why other options are incorrect:

- **B** - Redshift is highly available within a region, but won't survive a complete region outage without cross-region replication.

- **C** - Automated snapshots stay in the same region. They won't survive a region failure.

- **D** - Manual jobs are error-prone. Cross-region snapshot copy is built-in.

## References

- https://docs.aws.amazon.com/redshift/latest/mgmt/managing-snapshots-console.html
- https://tutorialsdojo.com/amazon-redshift/

## Domain

Design Resilient Architectures
