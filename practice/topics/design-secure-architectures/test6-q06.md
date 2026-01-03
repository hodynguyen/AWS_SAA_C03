# Question 6

ElastiCache for Redis used for stock trading app. Need password authentication before executing Redis commands.

Which should you do?

## Options

A. Create Redis replication group with AtRestEncryptionEnabled.

B. Use Redis AUTH with --transit-encryption-enabled and --auth-token.

C. Enable in-transit encryption only.

D. Do nothing. Enabled by default.

## Correct Answer

**B. Use Redis AUTH with --transit-encryption-enabled and --auth-token.**

## Explanation

Redis AUTH:
- **Password protection**: Requires authentication before commands
- **--auth-token**: Sets the password
- **--transit-encryption-enabled**: Required for AUTH to work
- **Security**: Prevents unauthorized access to cache

### Why other options are incorrect:

- **A** - At-rest encryption protects stored data, not access control.

- **C** - In-transit encryption alone doesn't require password.

- **D** - Redis AUTH is disabled by default.

## References

- https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/auth.html
- https://tutorialsdojo.com/amazon-elasticache/

## Domain

Design Secure Architectures
