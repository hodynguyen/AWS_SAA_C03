# Question 2

## Topic
Design Cost-Optimized Architectures

## Question
In Amazon EC2, you can manage your instances from the moment you launch them up to their termination. You can flexibly control your computing costs by changing the EC2 instance state. Which of the following statements is true regarding EC2 billing? (Select TWO.)

## Options
A. You will be billed when your Reserved instance is in terminated state.

B. You will not be billed for any instance usage while an instance is not in the running state.

C. You will be billed when your On-Demand instance is in pending state.

D. You will be billed when your Spot instance is preparing to stop with a stopping state.

E. You will be billed when your On-Demand instance is preparing to hibernate with a stopping state.

## Correct Answers
**A. You will be billed when your Reserved instance is in terminated state.**

**E. You will be billed when your On-Demand instance is preparing to hibernate with a stopping state.**

## Explanation
Below are the valid EC2 lifecycle instance states:

- **pending** - The instance is preparing to enter the running state.
- **running** - The instance is running and ready for use.
- **stopping** - The instance is preparing to be stopped. You will not be billed if it is preparing to stop; however, you will still be billed if it is preparing to hibernate.
- **stopped** - The instance is shut down and cannot be used.
- **shutting-down** - The instance is preparing to be terminated.
- **terminated** - The instance has been permanently deleted. Reserved Instances that applied to terminated instances are still billed until the end of their term.

**Why other options are incorrect:**
- **Option B** is incorrect because you can still be billed if your instance is preparing to hibernate with a stopping state.
- **Option C** is incorrect because you will not be billed if your instance is in pending state.
- **Option D** is incorrect because you will not be billed if your instance is preparing to stop with a stopping state.

## References
- https://github.com/awsdocs/amazon-ec2-user-guide/pull/45
- http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-lifecycle.html
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/
