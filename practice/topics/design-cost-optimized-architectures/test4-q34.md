# Question 34

A company has 50 Windows Server licenses tied to CPU count. They want to prevent launching instances when licenses are exhausted and receive notifications when all licenses are in use.

What is the recommended solution?

## Options

A. Upload licenses to Systems Manager Fleet Manager. Use IAM roles for license requests.

B. Define rules on AWS Certificate Manager. Enable "Enforce certificate limit."

C. Define licensing rules on AWS License Manager. Enable "Enforce license limit." Add SNS for alerts.

D. Configure AWS Resource Access Manager to track licenses. Add SNS for alerts.

## Correct Answer

**C. Define licensing rules on AWS License Manager. Enable "Enforce license limit." Add SNS for alerts.**

## Explanation

AWS License Manager tracks and enforces software license usage:
- **License configurations**: Define rules based on vCPUs, cores, or instances
- **Enforce license limit**: Prevents launching new resources when licenses exhausted
- **SNS integration**: Alerts when approaching or reaching license limits
- **BYOL support**: Works with existing licenses from Microsoft, Oracle, SAP, etc.

### Why other options are incorrect:

- **A** - Fleet Manager manages EC2 instances, not software licenses.

- **B** - ACM manages SSL/TLS certificates, not software licenses.

- **D** - RAM shares resources across accounts, not license management.

## References

- https://docs.aws.amazon.com/license-manager/latest/userguide/license-manager.html
- https://tutorialsdojo.com/aws-license-manager/

## Domain

Design Cost-Optimized Architectures
