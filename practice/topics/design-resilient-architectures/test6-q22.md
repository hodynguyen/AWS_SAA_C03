# Question 22

Three-tier app with static web, single EC2 for long-running processes, MySQL. Need HA and decoupling.

Which solution satisfies the requirement?

## Options

A. S3 + ECS with Auto Scaling + RDS Multi-AZ.

B. S3 + Lambda with concurrency limit + DynamoDB.

C. Larger EC2 + Auto Scaling + Aurora.

D. CloudFront + EC2 Auto Scaling + RDS Multi-AZ.

## Correct Answer

**A. S3 + ECS with Auto Scaling + RDS Multi-AZ.**

## Explanation

Decoupled architecture:
- **S3**: Static assets and web pages
- **ECS**: Container-based, scalable, long-running tasks
- **RDS Multi-AZ**: Highly available database
- **Auto Scaling**: Handle varying load

### Why other options are incorrect:

- **B** - Lambda max 15 min; can't handle long-running.

- **C** - Static assets on EC2 is expensive.

- **D** - CloudFront is CDN, can't store static files.

## References

- https://docs.aws.amazon.com/AmazonECS/latest/developerguide/service-auto-scaling.html
- https://tutorialsdojo.com/amazon-elastic-container-service-amazon-ecs/

## Domain

Design Resilient Architectures
