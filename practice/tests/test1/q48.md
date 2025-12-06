# Question 48

A company has recently migrated its microservices-based application to Amazon Elastic Kubernetes Service (Amazon EKS). As part of the migration, the company must ensure that all sensitive configuration data and credentials, such as database passwords and API keys, are stored securely and encrypted within the Amazon EKS cluster's etcd key-value store.

What is the most suitable solution to meet the company's requirements?

## Options

A. Use Amazon EKS default options and the Amazon Elastic Block Store (Amazon EBS) Container Storage Interface (CSI) driver as an add-on to securely store sensitive data within the Amazon EKS cluster.

B. Use AWS Secrets Manager with a new AWS KMS key to securely manage and store sensitive data within the EKS cluster's etcd key-value store.

C. Enable default Amazon EBS volume encryption for the account with a new AWS KMS key to ensure encryption of sensitive data within the Amazon EKS cluster.

D. Enable secret encryption with a new AWS KMS key on an existing Amazon EKS cluster to encrypt sensitive data stored in the EKS cluster's etcd key-value store.

## Correct Answer

**D. Enable secret encryption with a new AWS KMS key on an existing Amazon EKS cluster to encrypt sensitive data stored in the EKS cluster's etcd key-value store.**

## Explanation

Integrating AWS KMS with Amazon EKS allows for the encryption of secrets before they are saved in etcd. The process involves creating an AWS KMS key specifically for the EKS cluster and configuring the cluster to encrypt secrets.

By default, etcd secrets are not encrypted, posing potential security risks. Enabling secret encryption ensures all sensitive information within the etcd database is encrypted at rest.

### Why other options are incorrect:

- **B** - AWS Secrets Manager manages secrets but doesn't directly encrypt data within the etcd key-value store.

- **C** - EBS volume encryption is for worker node storage, not for etcd key-value store encryption.

- **A** - EBS CSI driver provides persistent storage, not etcd secret encryption.

## References

- https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html
- https://docs.aws.amazon.com/eks/latest/userguide/enable-kms.html
- https://tutorialsdojo.com/amazon-elastic-kubernetes-service-eks/

## Domain

Design Resilient Architectures
