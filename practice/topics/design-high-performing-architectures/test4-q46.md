# Question 46

A multiplayer game uses UDP for communication. User data will be stored in a key-value store.

Which architecture helps achieve this requirement?

## Options

A. Distribute traffic using ALB and store data in RDS.

B. Distribute traffic using NLB and store data in DynamoDB.

C. Distribute traffic using NLB and store data in Aurora.

D. Distribute traffic using ALB and store data in DynamoDB.

## Correct Answer

**B. Distribute traffic using NLB and store data in DynamoDB.**

## Explanation

- **Network Load Balancer (NLB)**: Operates at Layer 4, supports UDP protocol
- **DynamoDB**: Native key-value store with single-digit millisecond latency

ALB operates at Layer 7 (HTTP/HTTPS only) and doesn't support UDP.

### Why other options are incorrect:

- **A, D** - ALB only supports HTTP/HTTPS traffic, not UDP.

- **C** - Aurora is a relational database, not a key-value store.

## References

- https://docs.aws.amazon.com/elasticloadbalancing/latest/network/introduction.html
- https://tutorialsdojo.com/amazon-dynamodb/

## Domain

Design High-Performing Architectures
