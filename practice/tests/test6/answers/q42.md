# Question 42

EC2 Auto Scaling with SQL Server RDS. Secure in-flight data between web servers and RDS. (Select TWO.)

## Options

A. Download RDS Root CA cert and configure SSL.

B. Force SSL by setting rds.force_ssl to true.

C. Enable TDE in RDS option group.

D. Configure SG to allow only port 443.

E. Enable IAM DB authentication.

## Correct Answer

**A. Download RDS Root CA cert and configure SSL.**

**B. Force SSL by setting rds.force_ssl to true.**

## Explanation

SSL for SQL Server RDS:
- **Force SSL**: rds.force_ssl parameter = true
- **CA certificate**: Import to client for SSL
- **Encrypts in-flight**: Data between app and DB
- **Reboot required**: After changing parameter

### Why other options are incorrect:

- **C** - TDE encrypts data at rest, not in-flight.

- **D** - Port 443 alone doesn't encrypt traffic.

- **E** - IAM DB auth not supported for SQL Server.

## References

- https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/SQLServer.Concepts.General.SSL.Using.html
- https://tutorialsdojo.com/amazon-relational-database-service-amazon-rds/

## Domain

Design Secure Architectures
