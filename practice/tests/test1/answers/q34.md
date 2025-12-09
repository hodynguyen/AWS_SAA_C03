# Question 34

A business has recently migrated its applications to AWS. The audit team must be able to assess whether the services the company is using meet common security and regulatory standards. A solutions architect needs to provide the team with a report of all compliance-related documents for their account.

Which action should a solutions architect consider?

## Options

A. Run an Amazon Inspector assessment job to download all of the AWS compliance-related information.

B. View all of the AWS security compliance reports from AWS Security Hub.

C. Use AWS Artifact to view the security reports as well as other AWS compliance-related information.

D. Run an Amazon Macie job to view the Service Organization Control (SOC), Payment Card Industry (PCI), and other compliance reports from AWS Certificate Manager (ACM).

## Correct Answer

**C. Use AWS Artifact to view the security reports as well as other AWS compliance-related information.**

## Explanation

AWS Artifact is your go-to, central resource for compliance-related information. It provides on-demand access to AWS' security and compliance reports and select online agreements. Reports available in AWS Artifact include Service Organization Control (SOC) reports, Payment Card Industry (PCI) reports, and certifications from accreditation bodies.

### Why other options are incorrect:

- **A** - Amazon Inspector is a security tool for detecting vulnerabilities in AWS workloads, not for compliance documents.

- **D** - ACM is for managing SSL/TLS certificates. It does not store certifications or compliance-related documents.

- **B** - AWS Security Hub provides a view of security alerts and security posture, not compliance reports.

## References

- https://aws.amazon.com/artifact/getting-started/
- https://docs.aws.amazon.com/artifact/latest/ug/what-is-aws-artifact.html
- https://tutorialsdojo.com/aws-artifact/

## Domain

Design Secure Architectures
