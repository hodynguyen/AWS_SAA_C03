# Question 1

Financial firm needs secure key management. Comparing CloudHSM vs KMS.

Which statement is correct about CloudHSM and KMS?

## Options

A. Use CloudHSM if you require keys in dedicated, third-party validated HSMs under your exclusive control.

B. Use CloudHSM for managed service without operating your own HSM.

C. CloudHSM should always be used for payment transactions.

D. No major difference. They both do the same thing.

## Correct Answer

**A. Use CloudHSM if you require keys in dedicated, third-party validated HSMs under your exclusive control.**

## Explanation

CloudHSM vs KMS:
- **CloudHSM**: Dedicated HSM, you manage keys, FIPS 140-2 Level 3
- **KMS**: Managed service, AWS manages HSM, FIPS 140-2 Level 2
- **Control**: CloudHSM = exclusive control; KMS = shared infrastructure

### Why other options are incorrect:

- **B** - Reversed: KMS is the managed service.

- **C** - Not always; depends on compliance requirements.

- **D** - Different services with different use cases.

## References

- https://docs.aws.amazon.com/kms/latest/developerguide/overview.html
- https://tutorialsdojo.com/aws-key-management-service-aws-kms/

## Domain

Design High-Performing Architectures
