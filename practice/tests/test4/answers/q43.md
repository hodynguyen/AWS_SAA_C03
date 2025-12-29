# Question 43

A company uses AWS Directory Service with an AD connector. The following identity-based policy is attached:

```json
{
  "Statement": [{
    "Sid": "DirectoryTutorialsDojo1234",
    "Effect": "Allow",
    "Action": ["ds:*"],
    "Resource": "arn:aws:ds:us-east-1:987654321012:directory/d-1234567890"
  }]
}
```

What does this policy allow?

## Options

A. Allows all ds calls for directory ID: 987654321012

B. Allows all ds calls for directory ID: DirectoryTutorialsDojo1234

C. Allows all ds calls for directory name: DirectoryTutorialsDojo1234

D. Allows all ds calls for directory ID: d-1234567890

## Correct Answer

**D. Allows all ds calls for directory ID: d-1234567890**

## Explanation

The ARN structure is: `arn:aws:ds:region:account-id:directory/directory-id`
- **987654321012**: AWS account ID
- **d-1234567890**: Directory ID (the actual resource identifier)
- **DirectoryTutorialsDojo1234**: Just the Sid (Statement ID) for policy management

The policy allows all Directory Service actions on the specific directory `d-1234567890`.

### Why other options are incorrect:

- **A** - 987654321012 is the AWS account ID, not the directory ID.

- **B, C** - DirectoryTutorialsDojo1234 is a Sid identifier for the policy statement, not a directory ID or name.

## References

- https://docs.aws.amazon.com/directoryservice/latest/admin-guide/what_is.html
- https://tutorialsdojo.com/aws-directory-service/

## Domain

Design Secure Architectures
