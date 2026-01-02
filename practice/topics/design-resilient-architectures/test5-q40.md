# Question 40

An AI medical app needs single-digit millisecond latency on 5G edge with EKS and RBAC for IAM authentication.

Which solution should be implemented?

## Options

A. EKS on Fargate with Wavelength node groups and Fargate execution role.

B. EKS with Wavelength node groups and aws-auth ConfigMap.

C. EKS with Wavelength node groups, EKS connector agent, and Control Tower.

D. EKS with VPC CNI in Wavelength and aws-iam-authenticator.

## Correct Answer

**B. EKS with Wavelength node groups and aws-auth ConfigMap.**

## Explanation

Solution components:
- **AWS Wavelength**: Deploy EKS nodes at 5G edge for ultra-low latency
- **aws-auth ConfigMap**: Maps IAM users/roles to Kubernetes RBAC
- **EKS integration**: IAM authentication built-in

### Why other options are incorrect:

- **A** - Fargate profile shouldn't share IAM role with EC2 node groups.

- **C** - EKS connector is for external clusters; Control Tower isn't for RBAC.

- **D** - VPC CNI is default networking; iam-authenticator already integrated.

## References

- https://aws.amazon.com/wavelength/
- https://tutorialsdojo.com/amazon-elastic-kubernetes-service-eks/

## Domain

Design Resilient Architectures
