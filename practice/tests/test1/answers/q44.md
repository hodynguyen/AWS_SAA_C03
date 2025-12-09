# Question 44

A startup is using Amazon RDS to store data from a web application. Most of the time, the application has low user activity but it receives bursts of traffic within seconds whenever there is a new product announcement. The Solutions Architect needs to create a solution that will allow users around the globe to access the data using an API.

What should the Solutions Architect do meet the above requirement?

## Options

A. Create an API using Amazon API Gateway and use Amazon Elastic Beanstalk with Auto Scaling to handle the bursts of traffic in seconds.

B. Create an API using Amazon API Gateway and use the Amazon ECS cluster with Service Auto Scaling to handle the bursts of traffic in seconds.

C. Create an API using Amazon API Gateway and use an Auto Scaling group of Amazon EC2 instances to handle the bursts of traffic in seconds.

D. Create an API using Amazon API Gateway and use AWS Lambda to handle the bursts of traffic in seconds.

## Correct Answer

**D. Create an API using Amazon API Gateway and use AWS Lambda to handle the bursts of traffic in seconds.**

## Explanation

AWS Lambda can scale faster than regular Auto Scaling features because Lambda is more lightweight. Under the hood, Lambda can run code to thousands of available AWS-managed EC2 instances within seconds to accommodate traffic.

Lambda functions' cumulative concurrency in a Region can reach an initial burst level of 500-3000. For bursts of traffic within seconds, Lambda is the best option.

### Why other options are incorrect:

- **A, B, C** - Auto Scaling for EC2, ECS, or Elastic Beanstalk takes minutes to provision new resources, not seconds. Lambda can handle burst traffic almost instantly.

## References

- https://aws.amazon.com/blogs/startups/from-0-to-100-k-in-seconds-instant-scale-with-aws-lambda/
- https://docs.aws.amazon.com/lambda/latest/dg/invocation-scaling.html
- https://tutorialsdojo.com/aws-lambda/

## Domain

Design High-Performing Architectures
