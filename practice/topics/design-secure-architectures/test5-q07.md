# Question 7

An IAM policy allows lambda:CreateFunction and lambda:DeleteFunction on all resources but denies these plus InvokeFunction and TagResource from IP 187.5.104.11/32.

What is allowed by this policy?

## Options

A. Create Lambda function from 187.5.104.11/32

B. Delete Lambda function from 187.5.104.11/32

C. Create Lambda function from 100.220.0.11/32

D. Delete Lambda function from any network address

## Correct Answer

**C. Create Lambda function from 100.220.0.11/32**

## Explanation

Policy analysis:
- **Allow**: CreateFunction, DeleteFunction from any IP
- **Deny**: These actions from 187.5.104.11/32 specifically

Since 100.220.0.11/32 is not in the deny condition, you can create Lambda from this IP. But you can't delete/create from any address because 187.5.104.11 is excluded.

### Why other options are incorrect:

- **A, B** - IP 187.5.104.11/32 is explicitly denied.

- **D** - "Any address" includes the denied IP, so not all addresses work.

## References

- https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html
- https://tutorialsdojo.com/aws-identity-and-access-management-iam/

## Domain

Design Secure Architectures
