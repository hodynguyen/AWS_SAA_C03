# Question 61

Healthcare company needs to migrate on-premises patient records to AWS. Records must be WORM, audited at all levels.

Which is the most suitable solution?

## Options

A. DataSync to S3, CloudTrail Data Events, S3 Object Lock.

B. Storage Gateway to S3, CloudTrail Management Events, S3 Object Lock.

C. DataSync to S3, CloudTrail Management Events, S3 Object Lock.

D. Storage Gateway to EBS, server access logging, Object Lock.

## Correct Answer

**A. DataSync to S3, CloudTrail Data Events, S3 Object Lock.**

## Explanation

Solution components:
- **AWS DataSync**: Migrate data (not replicate like Storage Gateway)
- **S3 Object Lock**: WORM storage for compliance
- **CloudTrail Data Events**: Audit object-level access (GetObject, PutObject)

### Why other options are incorrect:

- **B, C** - Management Events track control plane, not data access.

- **B** - Storage Gateway is for hybrid access, not migration.

- **D** - EBS isn't suitable for records archive; server access logging less granular.

## References

- https://aws.amazon.com/datasync/
- https://tutorialsdojo.com/aws-datasync/

## Domain

Design High-Performing Architectures
