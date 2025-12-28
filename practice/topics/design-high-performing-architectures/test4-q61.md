# Question 61

## Topic
Design High-Performing Architectures

## Question
A company has a global news website hosted in a fleet of EC2 Instances. Lately, the load on the website has increased which resulted in slower response time for the site visitors. This issue impacts the revenue of the company as some readers tend to leave the site if it does not load after 10 seconds. The goal is to address the issue in a cost-effective manner.”

Which of the below services in AWS can be used to solve this problem? (Select TWO.)

## Options
A. For better read throughput, use AWS Storage Gateway to distribute the content across multiple regions.

B. Deploy the website to all regions in different VPCs for faster processing.

C. Use Amazon RDS Multi-AZ deployments for database read scalability.

D. Use Amazon ElastiCache for the website's in-memory data store or cache.

E. Use Amazon CloudFront with website as the custom origin.

## Correct Answer
D, E

## Explanation
The global news website has a problem with latency considering that there are a lot of readers of the site from all parts of the globe. In this scenario, you can use a content delivery network (CDN) which is a geographically distributed group of servers that work together to provide fast delivery of Internet content. And since this is a news website, most of its data are read-only, which can be cached to improve the read throughput and avoid repetitive requests from the server.

In AWS, Amazon CloudFront is the global content delivery network (CDN) service that you can use, and for web caching, Amazon ElastiCache is the suitable service.

Hence, the correct answers are:

- Use Amazon CloudFront with website as the custom origin.

- Use Amazon ElastiCache for the website's in-memory data store or cache.

References:

https://aws.amazon.com/elasticache/

http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html

Check out this Amazon CloudFront Cheat Sheet:

https://tutorialsdojo.com/amazon-cloudfront/

**Why other options are incorrect:**

- The option that says: For better read throughput, use AWS Storage Gateway to distribute the content across multiple regions is incorrect as AWS Storage Gateway is only used for storage.

- The option that says: Deploy the website to all regions in different VPCs for faster processing is incorrect as this typically would be costly and totally unnecessary, considering that you can use Amazon CloudFront and ElastiCache to improve the performance of the website.

- The option that says: Use Amazon RDS Multi-AZ deployments for database read scalability is incorrect. While Amazon RDS Multi-AZ deployments provide high availability and automatic failover, they primarily focus on database redundancy rather than improving website performance. Multi-AZ deployments are not directly related to reducing response times for the website.

