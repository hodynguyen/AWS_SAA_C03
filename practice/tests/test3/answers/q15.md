# Question 15

## Topic
Design Secure Architectures

## Question
A solutions architect is writing an AWS Lambda function that will process encrypted documents from an Amazon FSx for NetApp ONTAP file system. The documents are protected by an AWS KMS customer key. After processing the documents, the Lambda function will store the results in an S3 bucket with an Amazon S3 Glacier Flexible Retrieval storage class. The solutions architect must ensure that the files can be decrypted by the Lambda function.

Which action accomplishes the requirement?

## Options
A. Attach the kms:decrypt permission to the Lambda function's execution role. Add a statement to the AWS KMS key's policy that grants the function's ARN the kms:decrypt permission.

B. Attach the kms:decrypt permission to the Lambda function's resource policy. Add a statement to the AWS KMS key's policy that grants the function's execution role the kms:decrypt permission.

C. Attach the kms:decrypt permission to the Lambda function's resource policy. Add a statement to the AWS KMS key's policy that grants the function's resource policy ARN the kms:decrypt permission.

D. Attach the kms:decrypt permission to the Lambda function's execution role. Add a statement to the AWS KMS key's policy that grants the function's execution role the kms:decrypt permission.

## Correct Answer
D

## Explanation
A key policy is a resource policy for an AWS KMS key. Key policies are the primary way to control access to KMS keys. Unless the key policy explicitly allows it, you cannot use IAM policies to allow access to a KMS key.

AWS Lambda interacts with other AWS services using the permissions associated with an execution role. Therefore, you must:
1. Attach the kms:decrypt permission to the Lambda function's execution role
2. Add a statement to the KMS key's policy that grants the function's execution role the kms:decrypt permission

**Why other options are incorrect:**
- **Option A** is incorrect because you must use the ARN of the function's execution role as the principal, not the function's ARN.
- **Option B** is incorrect because the decrypt permission must be added to the execution role, not the resource policy.
- **Option C** is incorrect because the resource policy specifies who can invoke the function, not which AWS operations it can use.

## References
- https://docs.aws.amazon.com/kms/latest/developerguide/key-policies.html
- https://docs.aws.amazon.com/fsx/latest/ONTAPGuide/encryption-at-rest.html
- https://tutorialsdojo.com/aws-key-management-service-aws-kms/
