# Question 36

AMI stores access keys in plain text for DynamoDB access.

How to make architecture more secure?

## Options

A. Remove keys. Create IAM role and assign to EC2.

B. Do nothing. Keys in AMI are secure.

C. Put keys in Glacier.

D. Put keys in S3.

## Correct Answer

**A. Remove keys. Create IAM role and assign to EC2.**

## Explanation

IAM roles for EC2:
- **No credentials stored**: Role provides temporary creds
- **Secure**: No long-term keys on instance
- **Best practice**: Always use roles
- **Auto-rotation**: Credentials refresh automatically

### Why other options are incorrect:

- **B** - Storing keys in AMI is insecure.

- **C, D** - Storage services aren't for credential management.

## References

- https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2.html
- https://tutorialsdojo.com/aws-identity-and-access-management-iam/

## Domain

Design Secure Architectures
