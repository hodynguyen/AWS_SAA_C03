# Question 47

## Topic
Design Resilient Architectures

## Question
A data analytics company, which uses machine learning to collect and analyze consumer data, is using Redshift cluster as their data warehouse. You are instructed to implement a disaster recovery plan for their systems to ensure business continuity even in the event of an AWS region outage.

Which of the following is the best approach to meet this requirement?

## Options
A. Enable Cross-Region Snapshots Copy in your Amazon Redshift Cluster.

B. Do nothing because Amazon Redshift is a highly available, fully-managed data warehouse which can withstand an outage of an entire AWS region.

C. Use Automated snapshots of your Redshift Cluster.

D. Create a scheduled job that will automatically take the snapshot of your Redshift Cluster and store it to an S3 bucket. Restore the snapshot in case of an AWS region outage.

## Correct Answer
A

## Explanation
You can configure Amazon Redshift to copy snapshots for a cluster to another region. To configure cross-region snapshot copy, you need to enable this copy feature for each cluster and configure where to copy snapshots and how long to keep copied automated snapshots in the destination region. When a cross-region copy is enabled for a cluster, all new manual and automatic snapshots are copied to the specified region.

Using Automated snapshots of your Redshift Cluster is incorrect because using automated snapshots is not enough and will not be available in case the entire AWS region is down.

Reference:

https://docs.aws.amazon.com/redshift/latest/mgmt/managing-snapshots-console.html

Amazon Redshift Overview:

https://youtu.be/jlLERNzhHOg

Check out this Amazon Redshift Cheat Sheet:

https://tutorialsdojo.com/amazon-redshift/

**Why other options are incorrect:**

- The option that says: Create a scheduled job that will automatically take the snapshot of your Redshift Cluster and store it to an S3 bucket. Restore the snapshot in case of an AWS region outage is incorrect. Although this option is possible, this entails a lot of manual work and hence, not the best option. You should configure cross-region snapshot copy instead.

- The option that says: Do nothing because Amazon Redshift is a highly available, fully-managed data warehouse which can withstand an outage of an entire AWS region is incorrect. Although Amazon Redshift is a fully-managed data warehouse, you will still need to configure cross-region snapshot copy to ensure that your data is properly replicated to another region.

