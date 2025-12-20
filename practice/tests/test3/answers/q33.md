# Question 33

## Topic
Design Secure Architectures

## Question
A company requires that all AWS resources be tagged with a standard naming convention for better access control. The company's solutions architect must implement a solution that checks for untagged AWS resources.

Which solution requires the least amount of effort to implement?

## Options
A. Use tag policies in AWS Organizations to standardize the naming of tags. Store all the tags in an Amazon S3 bucket with the S3 Object Lock feature enabled.

B. Create a Lambda function that runs compliance checks on tagged resources. Schedule the function using Amazon EventBridge.

C. Use service control policies (SCP) to detect resources that are not tagged properly.

D. Use an AWS Config rule to detect non-compliant tags.

## Correct Answer
D

## Explanation
You can use the require-tags managed rule in AWS Config. This rule checks if a resource contains the tags that you specify. This provides an easy way to check for non-compliant tags without writing custom code.

**Why other options are incorrect:**
- **Option A** is incorrect because tag policies won't report resources with non-compliant tags. Also, S3 Object Lock is unrelated.
- **Option B** is incorrect because writing custom Lambda code requires more effort than using a managed Config rule.
- **Option C** is incorrect because SCPs are guardrails for setting maximum permissions, not for checking tags.

## References
- https://docs.aws.amazon.com/config/latest/developerguide/required-tags.html
- https://docs.aws.amazon.com/general/latest/gr/aws_tagging.html
- https://tutorialsdojo.com/aws-config/
