# Question 19

An e-commerce company utilizes a regional Amazon API Gateway to host its public REST APIs. The API Gateway endpoint is accessed through a custom domain name set up with an Amazon Route 53 alias record. To support continuous improvement, the company intends to launch a new version of its APIs with enhanced features and performance optimizations.

How can the company reduce customer disruption and ensure MINIMAL data loss during the update process in the MOST cost-effective way?

## Options

A. Implement a canary release deployment strategy for the API Gateway. Deploy the latest version of the APIs to a canary stage and direct a portion of the user traffic to this stage. Verify the new APIs. Gradually increase the traffic percentage, monitor for any issues, and, if successful, promote the canary stage to production.

B. Implement a blue-green deployment strategy for the API Gateway, deploying the latest version of the APIs to the green environment. Route some user traffic to it, validate the new APIs, and once thoroughly validated, promote the green environment to production.

C. Create a new API Gateway with the updated version of the APIs in OpenAPI JSON or YAML file format, but keep the same custom domain name for the new API Gateway.

D. Modify the existing API Gateway with the updated version of the APIs, but keep the same custom domain name for the new API Gateway by using the import-to-update operation in either overwrite or merge mode.

## Correct Answer

**A. Implement a canary release deployment strategy for the API Gateway. Deploy the latest version of the APIs to a canary stage and direct a portion of the user traffic to this stage. Verify the new APIs. Gradually increase the traffic percentage, monitor for any issues, and, if successful, promote the canary stage to production.**

## Explanation

Implementing a canary release deployment strategy for the API Gateway is a great way to ensure your APIs remain stable and reliable. This strategy involves releasing a new version of your API to a small subset of users, allowing you to test the latest version in a controlled environment.

If the new version performs well, you can gradually roll out the update to the rest of your users. This approach lets you catch any issues before they affect your entire user base, minimizing the impact on your customers.

### Why other options are incorrect:

- **C** - Upgrading to a new API Gateway while keeping the same custom domain name can result in downtime due to DNS propagation delays, which can negatively affect users and lead to data loss.

- **D** - Using the import-to-update operation may not provide enough isolation and control testing for the new version. If something goes wrong, it could lead to data loss affecting all customers simultaneously.

- **B** - In a blue-green deployment, both environments must be provisioned and maintained, adding complexity and cost. This breaks the cost requirement mentioned in the scenario.

## References

- https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html
- https://docs.aws.amazon.com/apigateway/latest/developerguide/canary-release.html
- https://tutorialsdojo.com/amazon-api-gateway/

## Domain

Design Resilient Architectures
