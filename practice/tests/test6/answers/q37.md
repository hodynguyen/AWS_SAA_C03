# Question 37

SMS marketing campaign. Need replies stored for 1 year. Near real-time analysis.

Which solution has LEAST overhead?

## Options

A. SNS + Kinesis (default settings).

B. SQS + Step Functions + Lambda + Glacier.

C. Pinpoint journey + Kinesis with 365-day retention.

D. Amazon Connect + Lambda + Glacier.

## Correct Answer

**C. Pinpoint journey + Kinesis with 365-day retention.**

## Explanation

SMS marketing with Pinpoint:
- **Pinpoint journey**: Multi-engagement SMS campaigns
- **Kinesis stream**: Real-time event processing
- **365-day retention**: Store responses for a year
- **Event streaming**: Automatic to Kinesis

### Why other options are incorrect:

- **A** - Default Kinesis retention is 24 hours.

- **B** - SQS can't send SMS.

- **D** - Amazon Connect has high operational overhead.

## References

- https://docs.aws.amazon.com/pinpoint/latest/userguide/journeys-create.html
- https://docs.aws.amazon.com/pinpoint/latest/developerguide/event-streams.html

## Domain

Design Secure Architectures
