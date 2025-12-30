# Question 23

A microservices application needs efficient read/write from multiple DynamoDB tables without impacting baseline performance.

Which is the most operationally efficient solution?

## Options

A. Use AWS AppSync pipeline resolvers.

B. Use CloudFront functions.

C. Set up DynamoDB connector for Athena Federated Query.

D. Use Lambda with edge-optimized API Gateway.

## Correct Answer

**A. Use AWS AppSync pipeline resolvers.**

## Explanation

AppSync pipeline resolvers:
- **Single API call**: Aggregate data from multiple tables
- **Server-side orchestration**: Combine results before returning
- **DynamoDB integration**: Direct resolvers for DynamoDB
- **GraphQL**: Efficient data fetching

### Why other options are incorrect:

- **B** - CloudFront functions are for lightweight request processing, not data fetching.

- **C** - Athena is read-only for DynamoDB, no write support.

- **D** - Edge-optimized API improves latency, not multi-table operations.

## References

- https://aws.amazon.com/blogs/mobile/appsync-pipeline-resolvers-2/
- https://tutorialsdojo.com/aws-appsync/

## Domain

Design High-Performing Architectures
