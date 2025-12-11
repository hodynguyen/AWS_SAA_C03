# Question 10

A company has an application that continually sends encrypted documents to Amazon S3. The company requires that the configuration for data access is in line with its strict compliance standards. It should also be alerted if there is any risk of unauthorized access or suspicious access patterns.

Which step is needed to meet the requirements?

## Options

A. Use Amazon GuardDuty to monitor malicious activity on S3.

B. Use Amazon Rekognition to monitor and recognize patterns on S3.

C. Use AWS CloudTrail to monitor and detect access patterns on S3.

D. Use Amazon Inspector to alert whenever a security violation is detected on S3.

## Correct Answer

**A. Use Amazon GuardDuty to monitor malicious activity on S3.**

## Explanation

Amazon GuardDuty can generate findings based on suspicious activities such as requests coming from known malicious IP addresses, changing of bucket policies/ACLs to expose an S3 bucket publicly, or suspicious API call patterns.

To detect possibly malicious behavior, GuardDuty uses anomaly detection, machine learning, and continuously updated threat intelligence.

### Why other options are incorrect:

- **B** - Rekognition identifies objects/people in images, not S3 access.

- **C** - CloudTrail tracks API calls but doesn't detect suspicious patterns.

- **D** - Inspector is for security assessment, not S3 monitoring.

## References

- https://aws.amazon.com/guardduty/
- https://tutorialsdojo.com/amazon-guardduty/

## Domain

Design Secure Architectures
