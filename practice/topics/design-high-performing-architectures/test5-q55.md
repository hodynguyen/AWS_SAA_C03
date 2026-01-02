# Question 55

Web application needs NoSQL database with no storage limit, fully managed and scalable.

Which is the most suitable service?

## Options

A. SimpleDB

B. DynamoDB

C. Amazon Aurora

D. Amazon Neptune

## Correct Answer

**B. DynamoDB**

## Explanation

DynamoDB:
- **Fully managed**: No infrastructure management
- **Unlimited storage**: No table size limits
- **Auto-scaling**: Adjusts capacity automatically
- **NoSQL**: Document and key-value store
- **Single-digit millisecond latency**: Fast performance

### Why other options are incorrect:

- **A** - SimpleDB has storage/request limits per table.

- **C** - Aurora is relational (SQL), not NoSQL.

- **D** - Neptune is graph database.

## References

- https://aws.amazon.com/dynamodb/
- https://tutorialsdojo.com/amazon-dynamodb/

## Domain

Design High-Performing Architectures
