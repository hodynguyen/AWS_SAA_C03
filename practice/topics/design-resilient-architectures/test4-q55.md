# Question 55

A shell script on an EC2 instance needs to get the instance's public and private IP addresses.

What is the best way to get this information?

## Options

A. Use Curl to get metadata from http://169.254.169.254/latest/meta-data/

B. By using IAM.

C. By using a CloudWatch metric.

D. Use Curl to get user data from http://169.254.169.254/latest/user-data/

## Correct Answer

**A. Use Curl to get metadata from http://169.254.169.254/latest/meta-data/**

## Explanation

Instance metadata is available from within the running instance at:
- `http://169.254.169.254/latest/meta-data/local-ipv4` - Private IP
- `http://169.254.169.254/latest/meta-data/public-ipv4` - Public IP

No external API calls or credentials needed—accessible only from the instance itself.

### Why other options are incorrect:

- **B** - IAM manages permissions, not instance metadata.

- **C** - CloudWatch metrics don't include IP addresses.

- **D** - User data contains scripts provided at launch, not instance metadata.

## References

- http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/

## Domain

Design Resilient Architectures
