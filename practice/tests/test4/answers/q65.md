# Question 65

## Topic
Design Resilient Architectures

## Question
A company is running a web application on AWS. The application is made up of an Auto-Scaling group that sits behind an Application Load Balancer and an Amazon DynamoDB table where user data is stored. The solutions architect must design the application to remain available in the event of a regional failure. A solution to automatically monitor the status of your workloads across your AWS account, conduct architectural reviews and check for AWS best practices.

Which configuration meets the requirement with the least amount of downtime possible?

## Options
A. Write a CloudFormation template that includes the auto-scaling group, application load balancer, and DynamoDB table. In the event of a failure, deploy the template in a secondary region. Use Route 53 DNS failover to automatically route traffic to the resources in the secondary region. Set up and configure the Amazon Managed Service for Prometheus service to receive insights for improving your workloads based on the AWS best practices.

B. Write a CloudFormation template that includes the auto-scaling group, application load balancer, and DynamoDB table. In the event of a failure, deploy the template in a secondary region. Configure Amazon EventBridge (Amazon CloudWatch Events) to trigger a Lambda function that updates the application’s Route 53 DNS record. Launch an Amazon Managed Grafana workspace to automatically receive tips and action items for improving your workloads based on the AWS best practices

C. In a secondary region, create a global table of the DynamoDB table and replicate the auto-scaling group and application load balancer. Use Route 53 DNS failover to automatically route traffic to the resources in the secondary region. Set up the AWS Well-Architected Tool to easily get recommendations for improving your workloads based on the AWS best practices

D. In a secondary region, create a global secondary index of the DynamoDB table and replicate the auto-scaling group and application load balancer. Use Route 53 DNS failover to automatically route traffic to the resources in the secondary region. Set up the AWS Compute Optimizer to automatically get recommendations for improving your workloads based on the AWS best practices

## Correct Answer
C

## Explanation
When you have more than one resource performing the same function—for example, more than one HTTP serve—you can configure Amazon Route 53 to check the health of your resources and respond to DNS queries using only the healthy resources. For example, suppose your website, example.com, is hosted on six servers, two each in three data centers around the world. You can configure Route 53 to check the health of those servers and to respond to DNS queries for example.com using only the servers that are currently healthy.

In this scenario, you can replicate the process layer (EC2 instances, Application Load Balancer) to a different region and create a global table based on the existing DynamoDB table (data layer). Amazon DynamoDB will handle data synchronization between the tables in different regions. This way, the state of the application is preserved even in the event of an outage. Lastly, configure Route 53 DNS failover and set the DNS name of the backup application load balancer as a target.

You can also use the Well-Architected Tool to automatically monitor the status of your workloads across your AWS account, conduct architectural reviews and check for AWS best practices.

This tool is based on the AWS Well-Architected Framework, which was developed to help cloud architects build secure, high-performing, resilient, and efficient application infrastructures. The Framework has been used in tens of thousands of workload reviews by AWS solutions architects, and it provides a consistent approach for evaluating your cloud architecture and implementing designs that will scale with your application needs over time.

Hence, the correct answer is: In a secondary region, create a global table of the DynamoDB table and replicate the auto-scaling group and application load balancer. Use Route 53 DNS failover to automatically route traffic to the resources in the secondary region. Set up the AWS Well-Architected Tool to easily get recommendations for improving your workloads based on the AWS best practices

References:

https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover-configuring.html

https://aws.amazon.com/blogs/networking-and-content-delivery/creating-disaster-recovery-mechanisms-using-amazon-route-53/

https://aws.amazon.com/well-architected-tool

Check out this Amazon Route 53 Cheat Sheet:

https://tutorialsdojo.com/amazon-route-53/

**Why other options are incorrect:**

- The option that says: In a secondary region, create a global secondary index of the DynamoDB table and replicate the auto-scaling group and application load balancer. Use Route 53 DNS failover to automatically route traffic to the resources in the secondary region. Set up the AWS Compute Optimizer to automatically get recommendations for improving your workloads based on the AWS best practices is incorrect because this configuration is impossible to implement. A global secondary index can only be created in the region where its parent table resides. Moreover, the AWS Compute Optimizer simply helps you to identify the optimal AWS resource configurations, such as Amazon Elastic Compute Cloud (EC2) instance types, Amazon Elastic Block Store (EBS) volume configurations, and AWS Lambda function memory sizes. It is not capable of providing recommendations to improve your workloads based on AWS best practices.

- The option that says: Write a CloudFormation template that includes the auto-scaling group, application load balancer, and DynamoDB table. In the event of a failure, deploy the template in a secondary region. Use Route 53 DNS failover to automatically route traffic to the resources in the secondary region. Set up and configure the Amazon Managed Service for Prometheus service to receive insights for improving your workloads based on the AWS best practices is incorrect. This solution describes a situation in which the environment is provisioned only after a regional failure occurs. It won't work because to enable Route 53 DNS failover, you'd need to target an existing environment. The use of the Amazon Managed Service for Prometheus service is irrelevant as well. This is just a serverless, Prometheus-compatible monitoring service for container metrics that makes it easier to securely monitor container environments at scale.

- The option that says: Write a CloudFormation template that includes the auto-scaling group, application load balancer, and DynamoDB table. In the event of a failure, deploy the template in a secondary region. Configure Amazon EventBridge (Amazon CloudWatch Events) to trigger a Lambda function that updates the application’s Route 53 DNS record. Launch an Amazon Managed Grafana workspace to automatically receive tips and action items for improving your workloads based on the AWS best practices is incorrect. This could work, but it won't deliver the shortest downtime possible since resource provisioning takes minutes to complete. Switching traffic to a standby environment is a faster method, albeit more expensive. Amazon Managed Grafana is a fully managed service with rich, interactive data visualizations to help customers analyze, monitor, and alarm on metrics, logs, and traces across multiple data sources. This service does not provide recommendations based on AWS best practices. You have to use the AWS Well-Architected Tool instead.

