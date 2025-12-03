# Question 24

A global IT company with offices around the world has multiple AWS accounts. To improve efficiency and drive costs down, the Chief Information Officer (CIO) wants to set up a solution that centrally manages their AWS resources. This will allow them to procure AWS resources centrally and share resources such as AWS Transit Gateways, AWS License Manager configurations, or Amazon Route 53 Resolver rules across their various accounts.

As the Solutions Architect, which combination of options should you implement in this scenario? (Select TWO.)

## Options

A. Consolidate all of the company's accounts using AWS ParallelCluster.

B. Consolidate all of the company's accounts using AWS Organizations.

C. Use the AWS Resource Access Manager (RAM) service to easily and securely share your resources with your AWS accounts.

D. Use the AWS Identity and Access Management service to set up cross-account access that will easily and securely share your resources with your AWS accounts.

E. Use AWS Control Tower to easily and securely share your resources with your AWS accounts.

## Correct Answers

**B. Consolidate all of the company's accounts using AWS Organizations.**

**C. Use the AWS Resource Access Manager (RAM) service to easily and securely share your resources with your AWS accounts.**

## Explanation

AWS Resource Access Manager (RAM) is a service that enables you to easily and securely share AWS resources with any AWS account or within your AWS Organization. You can share AWS Transit Gateways, Subnets, AWS License Manager configurations, and Amazon Route 53 Resolver rules resources with RAM.

RAM eliminates the need to create duplicate resources in multiple accounts, reducing the operational overhead of managing those resources in every single account you own. You can create resources centrally in a multi-account environment, and use RAM to share those resources across accounts.

AWS Organizations is an account management service that lets you consolidate multiple AWS accounts into an organization that you create and centrally manage.

### Why other options are incorrect:

- **D** - Although you can delegate access to resources in different AWS accounts using IAM, this process is extremely tedious. A better solution is to use AWS Resource Access Manager.

- **E** - AWS Control Tower offers the easiest way to set up and govern a new, secure, multi-account AWS environment. It's not the most suitable service to securely share resources across AWS accounts.

- **A** - AWS ParallelCluster is an AWS-supported open-source cluster management tool for High-Performance Computing (HPC) clusters on AWS.

## References

- https://aws.amazon.com/ram/
- https://docs.aws.amazon.com/ram/latest/userguide/shareable.html

## Domain

Design High-Performing Architectures
