# Question 30

## Topic
Design Secure Architectures

## Question
A Solutions Architect is managing a company's AWS account of approximately 300 IAM users. They have a new company policy that requires changing the associated permissions of all 100 IAM users that control the access to Amazon S3 buckets.

What will the Solutions Architect do to avoid the time-consuming task of applying the policy to each user?

## Options
A. Create a new IAM role and add each user to the IAM role.

B. Create a new policy and apply it to multiple IAM users using a shell script.

C. Create a new S3 bucket access policy with unlimited access for each IAM user.

D. Create a new IAM group and then add the users that require access to the S3 bucket. Afterward, apply the policy to the IAM group.

## Correct Answer
D

## Explanation
In this scenario, the best option is to create a new IAM group and then add the users that require access to the S3 bucket. Afterward, apply the policy to the IAM group. This will enable you to easily add, remove, and manage the users instead of manually adding a policy to each and every 100 IAM users.

**Why other options are incorrect:**
- **Option A** is incorrect because you need to use an IAM Group, not an IAM role.
- **Option B** is incorrect because while this can save time, it will be difficult to manage users not contained in an IAM Group.
- **Option C** is incorrect because you need a new IAM Group, and the method is time-consuming.

## References
- http://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups.html
- https://tutorialsdojo.com/aws-identity-and-access-management-iam/
