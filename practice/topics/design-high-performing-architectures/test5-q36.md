# Question 36

A research institute has simulation software requiring significant compute power (32 vCPUs, 256 GiB). They want to run simulations in parallel on AWS.

Which solution has LEAST operational overhead?

## Options

A. Use EC2 Spot Instances.

B. Use Lambda functions.

C. Use AWS Fargate.

D. Use AWS Batch.

## Correct Answer

**D. Use AWS Batch.**

## Explanation

AWS Batch:
- **Job management**: Automatically distributes workloads
- **Scaling**: Provisions compute resources as needed
- **Cost optimization**: Uses Spot Instances automatically
- **Minimal overhead**: No infrastructure management

### Why other options are incorrect:

- **A** - Spot can be interrupted; requires manual management.

- **B** - Lambda has 15-minute timeout; not for long simulations.

- **C** - Fargate lacks job scheduling; limited compute for heavy workloads.

## References

- https://aws.amazon.com/batch/
- https://tutorialsdojo.com/aws-batch/

## Domain

Design High-Performing Architectures
