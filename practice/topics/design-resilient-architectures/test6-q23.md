# Question 23

Docker MEAN stack app needs auto load balancing, scaling, monitoring, container placement.

Which service can fulfill this?

## Options

A. AWS Elastic Beanstalk

B. AWS Compute Optimizer

C. Amazon ECS

D. AWS CloudFormation

## Correct Answer

**A. AWS Elastic Beanstalk**

## Explanation

Elastic Beanstalk for Docker:
- **Automatic**: Load balancing, scaling, monitoring
- **Container support**: Native Docker deployment
- **Easy port**: Just upload code
- **Managed**: No infrastructure management

### Why other options are incorrect:

- **B** - Compute Optimizer recommends resources, not deployment.

- **C** - ECS requires manual configuration of these features.

- **D** - CloudFormation is IaC, not deployment automation.

## References

- https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create_deploy_docker.html
- https://tutorialsdojo.com/aws-elastic-beanstalk/

## Domain

Design Resilient Architectures
