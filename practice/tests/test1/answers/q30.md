# Question 30

A government entity is conducting a population and housing census in the city. Each household information uploaded on their online portal is stored in encrypted files in Amazon S3. The government assigned its Solutions Architect to set compliance policies that verify data containing personally identifiable information (PII) in a manner that meets their compliance standards. They should also be alerted if there are potential policy violations with the privacy of their S3 buckets.

Which of the following should the Architect implement to satisfy this requirement?

## Options

A. Set up and configure Amazon Fraud Detector to send out alert notifications whenever a security violation is detected on their Amazon S3 data.

B. Set up and configure Amazon Kendra to monitor malicious activity on their Amazon S3 data

C. Set up and configure Amazon Polly to scan for usage patterns on Amazon S3 data

D. Set up and configure Amazon Macie to monitor their Amazon S3 data.

## Correct Answer

**D. Set up and configure Amazon Macie to monitor their Amazon S3 data.**

## Explanation

Amazon Macie is an ML-powered security service that helps you prevent data loss by automatically discovering, classifying, and protecting sensitive data stored in Amazon S3. Amazon Macie uses machine learning to recognize sensitive data such as personally identifiable information (PII) or intellectual property, assigns a business value, and provides visibility into where this data is stored and how it is being used in your organization.

Amazon Macie generates two categories of findings: policy findings and sensitive data findings. A policy finding is a detailed report of a potential policy violation or issue with the security or privacy of an Amazon S3 bucket.

### Why other options are incorrect:

- **C** - Amazon Polly is a service that turns text into lifelike speech. It can't scan usage patterns on S3 data.

- **B** - Amazon Kendra is an enterprise search service that allows developers to add search capabilities to their applications. It doesn't monitor malicious activity on S3 buckets.

- **A** - Amazon Fraud Detector is a fully managed service for identifying potentially fraudulent activities. It does not check S3 data containing PII.

## References

- https://docs.aws.amazon.com/macie/latest/userguide/what-is-macie.html
- https://aws.amazon.com/macie/faq/
- https://tutorialsdojo.com/amazon-macie/

## Domain

Design Secure Architectures
