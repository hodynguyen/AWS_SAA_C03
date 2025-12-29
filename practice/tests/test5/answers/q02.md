# Question 2

A company stores irreproducible financial documents in S3. Files are retrieved quarterly but may need immediate access for surprise audits.

What is the most cost-effective storage solution?

## Options

A. Use Amazon S3 Standard

B. Use Amazon S3 Standard - Infrequent Access

C. Use Amazon S3 Intelligent-Tiering

D. Use Amazon Glacier Deep Archive

## Correct Answer

**B. Use Amazon S3 Standard - Infrequent Access**

## Explanation

S3 Standard-IA provides:
- **Low storage cost**: Cheaper than S3 Standard
- **Rapid retrieval**: Milliseconds access time
- **High durability**: Same 11 9's as S3 Standard

Perfect for infrequently accessed data that needs immediate access when requested.

### Why other options are incorrect:

- **A** - S3 Standard costs more, unnecessary for infrequent access.

- **C** - Intelligent-Tiering has monitoring fees; access pattern is already known.

- **D** - Glacier Deep Archive takes hours to retrieve, not suitable for surprise audits.

## References

- https://aws.amazon.com/s3/storage-classes/
- https://tutorialsdojo.com/amazon-s3/

## Domain

Design Cost-Optimized Architectures
