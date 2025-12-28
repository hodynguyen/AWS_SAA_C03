# Question 54

## Topic
Design High-Performing Architectures

## Question
An Auto Scaling group (ASG) of Amazon EC2 Linux instances has an Amazon FSx for OpenZFS file system with basic monitoring enabled in Amazon CloudWatch. The Solutions Architect noticed that the legacy web application hosted in the ASG takes a long time to load. After checking the instances, the Architect noticed that the ASG is not launching more instances as it should be, even though the servers already have high memory usage.

Which of the following options should the Architect implement to solve this issue?

## Options
A. Install the CloudWatch unified agent to the EC2 instances. Set up a custom parameter in AWS Systems Manager Parameter Store with the CloudWatch agent configuration to create an aggregated metric on memory usage percentage. Scale the Auto Scaling group based on the aggregated metric.

B. Set up Amazon Rekognition to automatically identify and recognize the cause of the high memory usage. Use the AWS Well-Architected Tool to automatically trigger the scale-out event in the ASG based on the overall memory usage.

C. Enable detailed monitoring on the EC2 instances of the Auto Scaling group. Use Auto Scaling with custom metrics to scale out the Auto Scaling group based on the aggregated memory usage of EC2 instances.

D. Implement an AI solution that leverages Amazon Comprehend to track the near-real-time memory usage of each and every EC2 instance. Use Amazon SageMaker AI to automatically trigger the Auto Scaling event if there is high memory usage.

## Correct Answer
A

## Explanation
Amazon CloudWatch agent enables you to collect both system metrics and log files from Amazon EC2 instances and on-premises servers. The agent supports both Windows Server and Linux and allows you to select the metrics to be collected, including sub-resource metrics such as per-CPU core.

The premise of the scenario is that the EC2 servers have high memory usage, but since this specific metric is not tracked by the Auto Scaling group by default, the scaling out activity is not being triggered. Remember that by default, CloudWatch doesn't monitor memory usage but only the CPU utilization, Network utilization, Disk performance, and Disk Reads/Writes.

This is the reason why you have to install a CloudWatch agent in your EC2 instances to collect and monitor the custom metric (memory usage), which will be used by your Auto Scaling Group as a trigger for scaling activities.

The AWS Systems Manager Parameter Store is one of the capabilities of AWS Systems Manager. It provides secure, hierarchical storage for configuration data management and secrets management. You can store data such as passwords, database strings, Amazon Machine Image (AMI) IDs, and license codes as parameter values. You can store values as plain text or encrypted data. You can reference Systems Manager parameters in your scripts, commands, SSM documents, and configuration and automation workflows by using the unique name that you specified when you created the parameter.

Hence, the correct answer is: Install the CloudWatch unified agent to the EC2 instances. Set up a custom parameter in AWS Systems Manager Parameter Store with the CloudWatch agent configuration to create an aggregated metric on memory usage percentage. Scale the Auto Scaling group based on the aggregated metric

References:

https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Install-CloudWatch-Agent.html

https://aws.amazon.com/blogs/mt/create-amazon-ec2-auto-scaling-policy-memory-utilization-metric-linux/

https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html

Check out these Amazon EC2 and CloudWatch Cheat Sheets:

https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/

https://tutorialsdojo.com/amazon-cloudwatch/

**Why other options are incorrect:**

- The option that says: Implement an AI solution that leverages Amazon Comprehend to track the near-real-time memory usage of each and every EC2 instance. Use Amazon SageMaker AI to automatically trigger the Auto Scaling event if there is high memory usage is incorrect because Amazon Comprehend cannot track near-real-time memory usage in Amazon EC2. This is just a natural-language processing (NLP) service that uses machine learning to uncover valuable insights and connections in text. Also, the use of an Amazon SageMaker AI in this scenario is not warranted since there is no machine learning requirement involved.

- The option that says: Enable detailed monitoring on the EC2 instances of the Auto Scaling group. Use Auto Scaling with custom metrics to scale out the Auto Scaling group based on the aggregated memory usage of EC2 instances is incorrect because detailed monitoring in CloudWatch primarily enhances the granularity of standard metrics like CPU utilization. While custom metrics can be integrated with AWS Auto Scaling, setting this up requires more overhead compared to installing the CloudWatch unified agent, which directly handles memory metrics.

- The option that says: Set up Amazon Rekognition to automatically identify and recognize the cause of the high memory usage. Use the AWS Well-Architected Tool to automatically trigger the scale-out event in the ASG based on the overall memory usage is incorrect because Amazon Rekognition is simply an image recognition service that detects objects, scenes, and faces; extracts text; recognizes celebrities; and identifies inappropriate content in images. It can't be used to track the high memory usage of your Amazon EC2 instances. The AWS Well-Architected Tool, on the other hand, is designed to help you review the state of your applications and workloads. It merely provides a central place for architectural best practices in AWS and nothing more.

