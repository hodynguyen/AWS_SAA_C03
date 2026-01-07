# Question 52

VR/AR games with RESTful APIs. Cost-effective and scalable migration.

Which solution?

## Options

A. Lambda + API Gateway.

B. Spot Fleet with EFA + ALB.

C. S3 static hosting + CloudFront.

D. ECS + ECR + Fargate.

## Correct Answer

**A. Lambda + API Gateway.**

## Explanation

Serverless for APIs:
- **Lambda**: Pay per request; scales automatically
- **API Gateway**: RESTful endpoint management
- **Cost-effective**: No idle costs
- **Scalable**: Handles any load

### Why other options are incorrect:

- **B** - Spot can be interrupted; EFA is for HPC.

- **C** - S3 is static only; no compute.

- **D** - ECS requires more management; costlier.

## References

- https://docs.aws.amazon.com/apigateway/latest/developerguide/getting-started-with-lambda-integration.html
- https://tutorialsdojo.com/aws-lambda/

## Domain

Design High-Performing Architectures
