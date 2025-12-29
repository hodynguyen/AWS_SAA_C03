# Question 65

A web application uses Auto Scaling, ALB, and DynamoDB. It must remain available during regional failures with minimal downtime. The solution should provide AWS best practice recommendations.

Which configuration meets these requirements?

## Options

A. CloudFormation template deployment after failure. Route 53 failover. Amazon Managed Service for Prometheus.

B. CloudFormation template deployment after failure. EventBridge + Lambda for DNS update. Amazon Managed Grafana.

C. DynamoDB Global Table in secondary region. Replicate ASG and ALB. Route 53 failover. AWS Well-Architected Tool.

D. DynamoDB Global Secondary Index in secondary region. Replicate ASG and ALB. Route 53 failover. AWS Compute Optimizer.

## Correct Answer

**C. DynamoDB Global Table in secondary region. Replicate ASG and ALB. Route 53 failover. AWS Well-Architected Tool.**

## Explanation

Multi-region DR with minimal downtime:
- **DynamoDB Global Tables**: Automatic multi-region replication
- **Pre-deployed infrastructure**: ASG + ALB ready in secondary region
- **Route 53 health checks**: Automatic failover to secondary region
- **Well-Architected Tool**: Reviews architecture against AWS best practices

### Why other options are incorrect:

- **A, B** - Deploying infrastructure after failure causes significant downtime.

- **D** - Global Secondary Index is local to a table, not multi-region. Compute Optimizer suggests instance types, not best practices.

## References

- https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover-configuring.html
- https://aws.amazon.com/well-architected-tool/

## Domain

Design Resilient Architectures
