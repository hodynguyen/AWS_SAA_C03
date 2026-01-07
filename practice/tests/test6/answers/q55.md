# Question 55

ECS behind ALB loads slowly. Need auto scaling. (Select TWO.)

## Options

A. Scale ECS cluster on service's CPU utilization.

B. Scale ECS cluster on ALB target group CPU.

C. Scale ECS service on memory utilization.

D. Scale ECS service on ALB endpoint status.

E. Scale ECS service on ALB CPU utilization.

## Correct Answer

**A. Scale ECS cluster on service's CPU utilization.**

**C. Scale ECS service on memory utilization.**

## Explanation

ECS Auto Scaling metrics:
- **ECSServiceAverageCPUUtilization**: Scale cluster
- **ECSServiceAverageMemoryUtilization**: Scale service
- **ALBRequestCountPerTarget**: Valid for scaling
- **Custom CloudWatch metrics**: Can also be used

### Why other options are incorrect:

- **B** - ALB target group CPU not a valid metric.

- **D** - Unreachable endpoint is different issue.

- **E** - Can't track ALB CPU; ALB has no CPU metric.

## References

- https://docs.aws.amazon.com/AmazonECS/latest/developerguide/service-configure-auto-scaling.html
- https://tutorialsdojo.com/aws-auto-scaling/

## Domain

Design Resilient Architectures
