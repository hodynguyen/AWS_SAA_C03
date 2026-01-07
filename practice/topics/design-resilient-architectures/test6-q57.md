# Question 57

1TB MySQL 8.0 on-premises. Monthly copy to staging takes hours, causes downtime. Need resilience. (Select TWO.)

## Options

A. Manual snapshot and restore.

B. mysqldump to replicate.

C. Aurora with Multi-AZ Replicas.

D. RDS Multi-AZ.

E. Aurora cloning.

## Correct Answer

**C. Aurora with Multi-AZ Replicas.**

**E. Aurora cloning.**

## Explanation

Aurora for resilience + fast copy:
- **Multi-AZ Replicas**: High availability
- **Aurora cloning**: Fast, space-efficient copy
- **Shared storage**: Clone uses same volume
- **No performance impact**: Unlike mysqldump

### Why other options are incorrect:

- **A** - Snapshot restore is slower than cloning.

- **B** - mysqldump impacts performance.

- **D** - RDS doesn't have fast cloning feature.

## References

- https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Managing.Clone.html
- https://tutorialsdojo.com/amazon-aurora/

## Domain

Design Resilient Architectures
