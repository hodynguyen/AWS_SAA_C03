# Question 63

ASG terminates instances on health check failure, losing ephemeral logs. Need to collect logs before termination.

What is the EASIEST automation approach?

## Options

A. Lifecycle hook to Terminating:Wait, CloudWatch Events with Lambda, Systems Manager Run Command.

B. Lifecycle hook to Terminating:Wait, Step Functions, CloudWatch Logs.

C. Lifecycle hook to Pending:Wait, CloudWatch Events with Lambda, Systems Manager Automation.

D. Lifecycle hook to Terminating:Wait, CloudWatch Events with Lambda, trigger CloudWatch agent.

## Correct Answer

**D. Lifecycle hook to Terminating:Wait, CloudWatch Events with Lambda, trigger CloudWatch agent.**

## Explanation

Solution flow:
1. **Lifecycle hook**: Pauses termination at Terminating:Wait
2. **CloudWatch Events**: Triggers Lambda on terminate lifecycle action
3. **CloudWatch agent**: Pushes logs automatically
4. **Resume termination**: After logs sent

### Why other options are incorrect:

- **A** - Run Command requires custom scripts; more effort.

- **B** - Step Functions can't directly collect logs.

- **C** - Pending:Wait is for launch, not termination.

## References

- https://docs.aws.amazon.com/autoscaling/ec2/userguide/AutoScalingGroupLifecycle.html
- https://tutorialsdojo.com/aws-auto-scaling/

## Domain

Design High-Performing Architectures
