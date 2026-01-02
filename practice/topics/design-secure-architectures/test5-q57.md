# Question 57

ALB needs HTTP request logging including client IP and latencies. ECS Anywhere apps need troubleshooting.

Which solution has LEAST overhead?

## Options

A. Enable CloudTrail for ALB. Use CloudTrail Lake for analysis.

B. Enable ALB access logs. Use CloudWatch Application Insights for ECS.

C. Use EventBridge metrics for client IP. Use CloudWatch GetMetricData.

D. Run X-Ray daemon on ECS. Use CloudWatch ServiceLens.

## Correct Answer

**B. Enable ALB access logs. Use CloudWatch Application Insights for ECS.**

## Explanation

Solution components:
- **ALB Access Logs**: Captures client IP, latencies, request details
- **CloudWatch Application Insights**: Automated anomaly detection for ECS
- **Least overhead**: Both are managed services with minimal setup

### Why other options are incorrect:

- **A** - CloudTrail logs API calls, not HTTP requests through ALB.

- **C** - EventBridge doesn't capture client IPs; GetMetricData retrieves existing metrics.

- **D** - X-Ray requires code instrumentation; doesn't capture client IPs without access logs.

## References

- https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-access-logs.html
- https://tutorialsdojo.com/aws-elastic-load-balancing-elb/

## Domain

Design Secure Architectures
