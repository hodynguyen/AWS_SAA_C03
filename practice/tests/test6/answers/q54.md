# Question 54

Microservices with horizontal scaling. What's the difference between horizontal and vertical scaling?

## Options

A. Vertical = serverless Lambda. Horizontal = more servers.

B. Vertical = bigger machines. Horizontal = more servers.

C. Horizontal = bigger machines. Vertical = more servers.

D. Horizontal = smaller containers. Vertical = more servers.

## Correct Answer

**B. Vertical = bigger machines. Horizontal = more servers.**

## Explanation

Scaling definitions:
- **Vertical (scale up)**: Bigger instance, limited by max size
- **Horizontal (scale out)**: More instances, no limits
- **Microservices**: Horizontal scaling preferred
- **Decoupled**: Each service scales independently

### Why other options are incorrect:

- **A** - Lambda is serverless, not vertical scaling.

- **C, D** - Definitions are reversed or incorrect.

## References

- https://docs.aws.amazon.com/aws-technical-content/latest/microservices-on-aws/microservices-on-aws.pdf
- https://tutorialsdojo.com/aws-certified-solutions-architect-associate/

## Domain

Design High-Performing Architectures
