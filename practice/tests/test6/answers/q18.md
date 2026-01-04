# Question 18

Lambda function runs 15 minutes on average. Some invocations terminated throughout the day.

What is the most likely cause?

## Options

A. Recursive code running over 15 minutes.

B. Exceeded maximum execution time (15 minutes).

C. Concurrent execution limit reached.

D. ServiceException internal error.

## Correct Answer

**B. Exceeded maximum execution time (15 minutes).**

## Explanation

Lambda timeout:
- **Max timeout**: 15 minutes (900 seconds)
- **Default**: 3 seconds
- **Terminated**: When timeout reached
- **Configure**: Set based on expected execution time

### Why other options are incorrect:

- **A** - Recursive code causes throttling, not termination.

- **C** - Limit reached causes throttling, not termination.

- **D** - Internal errors are rare; unlikely throughout the day.

## References

- https://docs.aws.amazon.com/lambda/latest/dg/limits.html
- https://tutorialsdojo.com/aws-lambda/

## Domain

Design Resilient Architectures
