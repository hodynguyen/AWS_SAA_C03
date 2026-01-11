# Question 1

## Topic
Design Resilient Architectures

## Question
You are automating the creation of EC2 instances in your VPC. Hence, you wrote a python script to trigger the Amazon EC2 API to request 50 EC2 instances in a single Availability Zone. However, you noticed that after 20 successful requests, subsequent requests failed.

What could be a reason for this issue and how would you resolve it?

## Options
A. By default, AWS allows you to provision a maximum of 20 instances per region. Select a different region and retry the failed request.

B. By default, AWS allows you to provision a maximum of 20 instances per Availability Zone. Select a different Availability Zone and retry the failed request.

C. There was an issue with the Amazon EC2 API. Just resend the requests and these will be provisioned successfully.

D. There is a vCPU-based On-Demand Instance limit per region which is why subsequent requests failed. Just submit the limit increase form to AWS and retry the failed requests once approved.

## Correct Answer
D

## Explanation
You are limited to running On-Demand Instances per your vCPU-based On-Demand Instance limit, purchasing 20 Reserved Instances, and requesting Spot Instances per your dynamic Spot limit per region. New AWS accounts may start with limits that are lower than the limits described here.

If you need more instances, complete the Amazon EC2 limit increase request form with your use case, and your limit increase will be considered. Limit increases are tied to the region they were requested for.

**Why other options are incorrect:**
- **Option A** is incorrect. There is no need to select a different region since this limit can be increased after submitting a request form to AWS.
- **Option B** is incorrect because the vCPU-based On-Demand Instance limit is set per region and not per Availability Zone.
- **Option C** is incorrect because you are limited to running On-Demand Instances per your vCPU-based On-Demand Instance limit. There is no problem with the EC2 API.

## References
- https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html#limits_ec2
- https://aws.amazon.com/ec2/faqs/#How_many_instances_can_I_run_in_Amazon_EC2
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/
