# Question 60

A Docker application, which is running on an Amazon ECS cluster behind a load balancer, is heavily using Amazon DynamoDB. The application requires improved database performance by distributing the workload evenly and utilizing the provisioned throughput efficiently.

Which of the following should be implemented for the DynamoDB table?

## Options

A. Avoid using a composite primary key, which is composed of a partition key and a sort key.

B. Use partition keys with high-cardinality attributes, which have a large number of distinct values for each item.

C. Reduce the number of partition keys in the DynamoDB table.

D. Use partition keys with low-cardinality attributes, which have a few number of distinct values for each item.

## Correct Answer

**B. Use partition keys with high-cardinality attributes, which have a large number of distinct values for each item.**

## Explanation

The partition key determines the logical partitions where data is stored, affecting underlying physical partitions. Provisioned I/O capacity is divided evenly among physical partitions.

Using partition keys with high-cardinality (many distinct values) distributes I/O requests evenly, avoiding "hot" partitions that cause throttling.

### Why other options are incorrect:

- **C** - You should add more distinct partition key values, not reduce them.

- **D** - Low-cardinality means less even distribution, causing hot partitions.

- **A** - Composite primary keys provide more partitioning options, improving performance.

## References

- https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/bp-partition-key-uniform-load.html
- https://aws.amazon.com/blogs/database/choosing-the-right-dynamodb-partition-key/
- https://tutorialsdojo.com/amazon-dynamodb/

## Domain

Design High-Performing Architectures
