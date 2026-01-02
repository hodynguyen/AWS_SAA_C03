# Question 41

10 TB of infrequently accessed financial data for audits. Retrieval can take up to 24 hours.

Which is the most cost-effective solution?

## Options

A. S3 with lifecycle to S3 One Zone-IA.

B. S3 with lifecycle to Glacier after 0 days.

C. S3 with lifecycle to S3-IA.

D. Amazon FSx for Windows with SMB.

## Correct Answer

**B. S3 with lifecycle to Glacier after 0 days.**

## Explanation

Glacier archival:
- **Lowest cost**: Cheapest for infrequent access
- **Bulk retrieval**: 5-12 hours (within 24h requirement)
- **0-day transition**: Immediate archival
- **Durable**: 11 9's durability

### Why other options are incorrect:

- **A** - One Zone-IA less durable (single AZ); more expensive than Glacier.

- **C** - S3-IA more expensive than Glacier for infrequent access.

- **D** - FSx is for active file shares, not archival; more expensive.

## References

- https://aws.amazon.com/glacier/faqs/
- https://tutorialsdojo.com/amazon-glacier/

## Domain

Design Cost-Optimized Architectures
