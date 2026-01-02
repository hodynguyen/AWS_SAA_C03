# Question 17

An EC2 application uses AWS SDK to communicate with AWS services. All API calls must be logged and durably stored for IT audit.

Which service is most suitable?

## Options

A. Amazon CloudWatch

B. Amazon API Gateway

C. AWS CloudTrail

D. AWS X-Ray

## Correct Answer

**C. AWS CloudTrail**

## Explanation

CloudTrail:
- **API logging**: Records all AWS API calls
- **User identity**: Who made the call
- **Source IP**: Where the call came from
- **Durable storage**: Logs stored in S3

### Why other options are incorrect:

- **A** - CloudWatch monitors metrics, not API calls.

- **B** - API Gateway manages APIs, doesn't log AWS service calls.

- **D** - X-Ray traces application requests, not AWS API calls.

## References

- https://aws.amazon.com/cloudtrail/
- https://tutorialsdojo.com/aws-cloudtrail/

## Domain

Design Secure Architectures
