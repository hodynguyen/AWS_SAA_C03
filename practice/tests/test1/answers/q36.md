# Question 36

An online learning company hosts its Microsoft .NET e-Learning application on a Windows Server in its on-premises data center. The application uses an Oracle Database Standard Edition as its backend database.

The company wants a high-performing solution to migrate this workload to the AWS cloud to take advantage of the cloud's high availability. The migration process should minimize development changes, and the environment should be easier to manage.

Which of the following options should be implemented to meet the company requirements? (Select TWO.)

## Options

A. Refactor the application to .NET Core and run it as a serverless container service using Amazon Elastic Kubernetes Service (Amazon EKS) with AWS Fargate.

B. Rehost the on-premises .NET application to an AWS Elastic Beanstalk Multi-AZ environment which runs in multiple Availability Zones.

C. Provision and replatform the application to Amazon Elastic Container Service (Amazon ECS) with Amazon EC2 worker nodes.

D. Perform a homogeneous migration by moving the Oracle database to Amazon RDS for Oracle in a Multi-AZ deployment using AWS Database Migration Service (AWS DMS).

E. Use AWS Application Migration Service (AWS MGN) to migrate the on-premises Oracle database server to a new Amazon EC2 instance.

## Correct Answers

**B. Rehost the on-premises .NET application to an AWS Elastic Beanstalk Multi-AZ environment which runs in multiple Availability Zones.**

**D. Perform a homogeneous migration by moving the Oracle database to Amazon RDS for Oracle in a Multi-AZ deployment using AWS Database Migration Service (AWS DMS).**

## Explanation

AWS Elastic Beanstalk for .NET makes it easier to deploy, manage, and scale your ASP.NET web applications. Simply upload your application, and Elastic Beanstalk automatically handles capacity provisioning, load balancing, scaling, and health monitoring.

AWS DMS makes it easy to migrate relational databases to AWS. For homogeneous migrations (Oracle to Oracle), no schema conversion is needed.

### Why other options are incorrect:

- **A** - Refactoring to .NET Core requires significant code changes, which contradicts the requirement to minimize development changes.

- **E** - RDS supports Oracle databases, so using AWS DMS is better than MGN for database migration.

- **C** - Replatforming to ECS requires managing EC2 instances and significant development changes.

## References

- https://docs.aws.amazon.com/dms/latest/userguide/Welcome.html
- https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create_deploy_NET.html
- https://tutorialsdojo.com/aws-elastic-beanstalk/

## Domain

Design High-Performing Architectures
