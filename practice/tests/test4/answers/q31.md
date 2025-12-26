# Question 31

## Topic
Design High-Performing Architectures

## Question
A company hosts all its applications on its data center on the US East Coast. Most of the workloads are legacy applications that are hosted on individual virtual machines running in Linux and Windows operating systems. The company plans to migrate all of its VM workloads to the AWS cloud. To minimize changes in the applications during the migration process, it has been decided that the company will use a “lift-and-shift” strategy. The company also wants to minimize downtime during the migration process.

Which of the following options should the Solutions Architect implement for this scenario?

## Options
A. Utilize AWS DataSync to migrate the application workloads to AWS. Deploy the AWS DataSync VM on the on-premises data center. Once replication is completed, launch Amazon EC2 instances based on the created AMIs.

B. Export the on-premises VMs and upload the images to an Amazon S3 bucket. Use VM Import/Export service to import the images and launch them as Amazon EC2 instances.

C. Install the AWS Replication Agent on each of the on-premises VMs to continuously replicate the servers to AWS. Use AWS Migration Service (AWS MGN) to launch test instances and perform cutover once testing is completed.

D. Use the AWS Application Discovery Service for lift-and-shift migrations. Deploy the AWS Application Discovery Agent to the on-premises data center to start the replication process. After the replication task is completed, launch Amazon EC2 instances based on the created AMIs.

## Correct Answer
C

## Explanation
AWS Application Migration Service (AWS MGN) is the primary migration service recommended for lift-and-shift migrations to AWS. AWS encourages customers who are currently using AWS Elastic Disaster Recovery to switch to AWS MGN for future migrations. AWS MGN enables organizations to move applications to AWS without having to make any changes to the applications, their architecture, or the migrated servers.

AWS Application Migration Service minimizes time-intensive, error-prone manual processes by automatically converting your source servers from physical, virtual machines, and cloud infrastructure to run natively on AWS.

The service simplifies your migration by enabling you to use the same automated process for a wide range of applications. By launching non-disruptive tests before migrating, you can be confident that your most critical applications such as SAP, Oracle, and SQL Server, will work seamlessly on AWS.

Implementation begins by installing the AWS Replication Agent on your source servers. When you launch Test or Cutover instances, AWS Application Migration Service automatically converts your source servers to boot and runs natively on AWS.

Therefore, the correct answer is: Install the AWS Replication Agent on each of the on-premises VMs to continuously replicate the servers to AWS. Use AWS Migration Service (AWS MGN) to launch test instances and perform cutover once testing is completed.

References:

https://aws.amazon.com/blogs/aws/how-to-use-the-new-aws-application-migration-service-for-lift-and-shift-migrations/

https://docs.aws.amazon.com/mgn/latest/ug/what-is-application-migration-service.html

https://docs.aws.amazon.com/mgn/latest/ug/first-time-setup-gs.html

Check out this AWS Application Migration Service Cheat Sheet:

https://tutorialsdojo.com/aws-application-migration-service/

**Why other options are incorrect:**

- The option that says: Export the on-premises VMs and upload the images to an Amazon S3 bucket. Use VM Import/Export service to import the images and launch them as Amazon EC2 instances is incorrect. This approach will take a lot of downtime since you will need to import the VMs manually, and they will most likely be outdated if there are a lot of changes on the source VMs after the upload is complete.

- The option that says: Use the AWS Application Discovery Service for lift-and-shift migrations. Deploy the AWS Application Discovery Agent to the on-premises data center to start the replication process. After the replication task is completed, launch Amazon EC2 instances based on the created AMIs is incorrect. The AWS Application Discovery Service is primarily used to track the migration status of your on-premises applications from the Migration Hub console in your home Region. This service is not capable of doing the actual migration.

- The option that says: Utilize AWS DataSync to migrate the application workloads to AWS. Deploy the AWS DataSync VM on the on-premises data center. Once replication is completed, launch Amazon EC2 instances based on the created AMIs is incorrect. AWS DataSync is designed to facilitate data transfer from on-premises to AWS storage systems, not for migrating/syncing Virtual Machines.

