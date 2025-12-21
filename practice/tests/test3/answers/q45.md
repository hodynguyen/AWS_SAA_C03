# Question 45

## Topic
Design Resilient Architectures

## Question
A company is using Amazon VPC that has a CIDR block of 10.31.0.0/27 that is connected to the on-premises data center. There was a requirement to create a Lambda function that will process massive amounts of cryptocurrency transactions every minute and then store the results to EFS. After setting up the serverless architecture and connecting the Lambda function to the VPC, the Solutions Architect noticed an increase in invocation errors with EC2 error types such as EC2ThrottledException at certain times of the day.

Which of the following are the possible causes of this issue? (Select TWO.)

## Options
A. The associated security group of your function does not allow outbound connections.

B. The Lambda function is placed in a VPC subnet with limited IP address capacity.

C. Your Lambda function exceeds the VPC quota for Elastic Network Interfaces (ENIs) or available IP addresses in the subnet.

D. The attached IAM execution role of your function does not have the necessary permissions to access the resources of your VPC.

E. Your VPC does not have a NAT gateway.

## Correct Answers
**B. The Lambda function is placed in a VPC subnet with limited IP address capacity.**

**C. Your Lambda function exceeds the VPC quota for Elastic Network Interfaces (ENIs) or available IP addresses in the subnet.**

## Explanation
When you configure a Lambda function to access resources within a VPC, AWS Lambda creates and manages ENIs on your behalf. If your VPC reaches its quota limit for ENIs or IP addresses, your Lambda function may fail to scale, leading to EC2ThrottledException errors.

The scenario mentions a /27 CIDR block which only provides 32 IP addresses (27 usable), which is very limited.

**Why other options are incorrect:**
- **Option A** is incorrect because security group issues would cause complete failure, not intermittent errors.
- **Option D** is incorrect because permission issues would cause EC2AccessDeniedException, not EC2ThrottledException.
- **Option E** is incorrect because NAT Gateway issues wouldn't cause throttling errors.

## References
- https://docs.aws.amazon.com/lambda/latest/dg/vpc.html
- https://docs.aws.amazon.com/lambda/latest/dg/configuration-vpc.html
- https://tutorialsdojo.com/aws-lambda/
