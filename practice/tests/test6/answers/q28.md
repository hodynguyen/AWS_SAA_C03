# Question 28

EC2 app uploads photos to S3. Need API credentials for S3 API.

What is the best option?

## Options

A. Encrypt and store credentials in EC2 directory.

B. Store credentials in Glacier.

C. Create IAM role and assign to EC2.

D. Store credentials in root web directory.

## Correct Answer

**C. Create IAM role and assign to EC2.**

## Explanation

IAM roles for EC2:
- **No credentials needed**: Role provides temporary creds
- **Automatic rotation**: Credentials auto-refresh
- **Secure**: No long-term credentials on instance
- **Best practice**: Always use roles for EC2

### Why other options are incorrect:

- **A, D** - Storing credentials on EC2 is insecure.

- **B** - Glacier is for archive storage, not credentials.

## References

- http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/

## Domain

Design Secure Architectures
