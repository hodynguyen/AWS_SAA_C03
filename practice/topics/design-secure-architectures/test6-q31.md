# Question 31

On-premises SQL Server DR with RPO 60s, RTO 1hr. Most cost-effective solution?

## Options

A. Storage Gateway + EBS fast snapshot restore.

B. RDS warm standby + DMS with CDC.

C. AWS Elastic Disaster Recovery (DRS) pilot light.

D. SQL Server Always On multi-site active/active.

## Correct Answer

**C. AWS Elastic Disaster Recovery (DRS) pilot light.**

## Explanation

AWS DRS:
- **Pilot light**: Minimal resources until failover
- **RPO seconds**: Continuous block-level replication
- **RTO 5-20 min**: Rapid recovery
- **Cost-effective**: Cheaper than warm standby

### Why other options are incorrect:

- **A** - Storage Gateway lacks automated failover.

- **B** - Warm standby costs more (running RDS).

- **D** - Active/active is expensive (multiple servers).

## References

- https://aws.amazon.com/disaster-recovery/
- https://tutorialsdojo.com/aws-well-architected-framework-disaster-recovery

## Domain

Design Secure Architectures
