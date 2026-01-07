# Question 56

Cluster placement group. Insufficient capacity error when adding instances.

How to fix?

## Options

A. Stop and restart all instances, then try again.

B. Submit capacity increase request to AWS.

C. Create another placement group.

D. Verify all instances are same size and type.

## Correct Answer

**A. Stop and restart all instances, then try again.**

## Explanation

Placement group capacity:
- **Stop and restart**: May move to new hardware
- **Hardware with capacity**: All instances fit
- **Best practice**: Launch all instances together
- **Same instance type**: Recommended

### Why other options are incorrect:

- **B** - No instance limit per placement group.

- **C** - New group loses enhanced networking benefit.

- **D** - Size mismatch isn't the capacity issue.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/

## Domain

Design High-Performing Architectures
