# Question 58

A company is using a combination of API Gateway and AWS Lambda for the web services of an online web portal that is accessed by hundreds of thousands of clients each day. The company will be announcing a new revolutionary product, and it is expected that the web portal will receive a massive number of visitors from all around the globe.

How can the back-end systems and applications be protected from traffic spikes?

## Options

A. Deploy Multi-AZ in API Gateway with Read Replica

B. Use throttling limits in API Gateway

C. API Gateway will automatically scale and handle massive traffic spikes so you do not have to do anything.

D. Manually upgrade the Amazon EC2 instances being used by API Gateway

## Correct Answer

**B. Use throttling limits in API Gateway**

## Explanation

Amazon API Gateway provides throttling at multiple levels including global and by service call. Throttling limits can be set for standard rates and bursts.

For example, API owners can set a rate limit of 1,000 requests per second and configure a burst of 2,000 requests per second. Requests over the limit receive a 429 HTTP response.

### Why other options are incorrect:

- **C** - While API Gateway scales automatically, you still need to configure throttling to manage bursts.

- **D** - API Gateway is a fully managed service; you don't have access to underlying EC2 instances.

- **A** - API Gateway doesn't have Multi-AZ with Read Replica features like RDS.

## References

- https://aws.amazon.com/api-gateway/faqs/#Throttling_and_Caching
- https://docs.aws.amazon.com/apigateway/
- https://tutorialsdojo.com/amazon-api-gateway/

## Domain

Design High-Performing Architectures
