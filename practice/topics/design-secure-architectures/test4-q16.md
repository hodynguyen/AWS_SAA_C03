# Question 16

A monitoring application generates audit logs that must be retained for 5 years before deletion per compliance requirements.

How can the Architect meet this requirement?

## Options

A. Store audit logs in an EFS volume with NFSv4 file-locking.

B. Store audit logs in S3 and enable Multi-Factor Authentication Delete (MFA Delete).

C. Store audit logs in a Glacier vault and use the Vault Lock feature.

D. Store audit logs in an EBS volume and take monthly snapshots.

## Correct Answer

**C. Store audit logs in a Glacier vault and use the Vault Lock feature.**

## Explanation

Glacier Vault Lock allows you to create immutable compliance policies. Once locked, the policy cannot be changed—even by root. You can enforce retention periods (e.g., deny delete until archive is 5 years old), making it ideal for regulatory compliance. Archives in Glacier are immutable once uploaded.

### Why other options are incorrect:

- **A** - EFS file locks can be overridden. Data integrity is not guaranteed.

- **B** - MFA Delete requires MFA to delete, but someone with MFA access can still delete files.

- **D** - EBS volumes and snapshots can be deleted by anyone with proper permissions.

## References

- https://docs.aws.amazon.com/amazonglacier/latest/dev/vault-lock.html
- https://tutorialsdojo.com/amazon-glacier/

## Domain

Design Secure Architectures
