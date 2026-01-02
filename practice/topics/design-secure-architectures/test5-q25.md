# Question 25

A CloudHSM was zeroized after 3 failed admin login attempts. No backup copy of keys exists.

How can you obtain a new copy of the keys?

## Options

A. Contact AWS Support for a copy.

B. Restore a snapshot of the HSM.

C. Keys are permanently lost without a copy.

D. Use Amazon CLI to get a copy.

## Correct Answer

**C. Keys are permanently lost without a copy.**

## Explanation

CloudHSM security:
- **Zeroization**: All keys permanently destroyed after failed logins
- **Customer-controlled**: AWS has no access to your keys
- **No recovery**: No backdoor or AWS copy exists

AWS recommends using multiple HSMs across AZs to prevent key loss.

### Why other options are incorrect:

- **A** - AWS doesn't have access to HSM keys—you control them.

- **B** - HSM snapshots don't exist; you must use cluster backups.

- **D** - CLI can't recover zeroized keys.

## References

- https://docs.aws.amazon.com/cloudhsm/latest/userguide/disaster-recovery.html
- https://tutorialsdojo.com/aws-cloudhsm/

## Domain

Design Secure Architectures
