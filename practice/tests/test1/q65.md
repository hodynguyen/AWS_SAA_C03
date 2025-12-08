# Question 65

A company is designing a banking portal that uses Amazon ElastiCache for Redis as its distributed session management component. To secure session data and ensure that Cloud Engineers must authenticate before executing Redis commands, specifically MULTI EXEC commands, the system should enforce strong authentication by requiring users to enter a password. Additionally, access should be managed with long-lived credentials while supporting robust security practices.

Which of the following actions should be taken to meet the above requirement?

## Options

A. Enable the in-transit encryption for Redis replication groups.

B. Authenticate the users using Redis AUTH by creating a new Redis Cluster with both the --transit-encryption-enabled and --auth-token parameters enabled.

C. Generate an IAM authentication token using AWS credentials and provide this token as a password.

D. Set up a Redis replication group and enable the AtRestEncryptionEnabled parameter.

## Correct Answer

**B. Authenticate the users using Redis AUTH by creating a new Redis Cluster with both the --transit-encryption-enabled and --auth-token parameters enabled.**

## Explanation

Using Redis AUTH command can improve data security by requiring the user to enter a password before they are granted permission to execute Redis commands on a password-protected Redis server.

To require users to enter a password, include the parameter --auth-token with the correct password when you create your replication group or cluster.

### Why other options are incorrect:

- **C** - IAM authentication tokens expire every 12 hours, not suitable for long-lived credentials.

- **D** - At-Rest Encryption only secures data inside the in-memory data store, not authentication.

- **A** - In-transit encryption is only part of the solution; Redis AUTH is needed for authentication.

## References

- https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/auth.html
- https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/encryption.html
- https://tutorialsdojo.com/amazon-elasticache/

## Domain

Design Secure Architectures
