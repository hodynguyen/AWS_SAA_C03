# Question 3

App on VMware Cloud on AWS needs DynamoDB access. Must follow least privilege for read, write, update, delete on specific table.

Which IAM policy is correct?

## Options

A. Policy with wildcards in Resource (table/*).

B. Policy with specific table and specific actions (GetItem, PutItem, etc.).

C. Policy with Action: "*" on specific table.

D. Policy with wildcards in Actions (Put*, Delete*, etc.).

## Correct Answer

**B. Policy with specific table and specific actions (GetItem, PutItem, etc.).**

## Explanation

Least privilege IAM policy:
- **Specific Resource**: `arn:aws:dynamodb:region:account:table/tablename`
- **Specific Actions**: GetItem, PutItem, UpdateItem, DeleteItem
- **No wildcards**: Avoids granting unintended permissions

### Why other options are incorrect:

- **A** - `table/*` allows access to ALL tables.

- **C** - `Action: "*"` allows ALL DynamoDB operations.

- **D** - `Update*` includes UpdateTable, UpdateGlobalTable, etc.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-policy-structure.html
- https://tutorialsdojo.com/aws-identity-and-access-management-iam/

## Domain

Design High-Performing Architectures
