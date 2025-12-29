# Question 31

A company wants to migrate on-premises Linux/Windows VMs to AWS using lift-and-shift with minimal downtime.

Which solution should be implemented?

## Options

A. Use AWS DataSync to migrate workloads. Deploy DataSync VM on-premises.

B. Export VMs to S3, use VM Import/Export to launch as EC2 instances.

C. Install AWS Replication Agent on VMs. Use AWS MGN for continuous replication and cutover.

D. Use AWS Application Discovery Service for migration. Deploy Discovery Agent on-premises.

## Correct Answer

**C. Install AWS Replication Agent on VMs. Use AWS MGN for continuous replication and cutover.**

## Explanation

AWS Application Migration Service (MGN) is the recommended lift-and-shift solution:
1. **Install Replication Agent**: Continuous block-level replication to AWS
2. **Launch Test Instances**: Validate before cutover
3. **Perform Cutover**: Minimal downtime—only final sync required

Supports physical, virtual, and cloud servers without application changes.

### Why other options are incorrect:

- **A** - DataSync transfers files/data, not VM workloads.

- **B** - VM Import/Export causes downtime during export and doesn't support continuous replication.

- **D** - Application Discovery Service discovers resources, it doesn't migrate them.

## References

- https://docs.aws.amazon.com/mgn/latest/ug/what-is-application-migration-service.html
- https://tutorialsdojo.com/aws-application-migration-service/

## Domain

Design High-Performing Architectures
