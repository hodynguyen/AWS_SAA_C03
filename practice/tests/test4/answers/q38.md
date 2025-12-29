# Question 38

A company has 100+ Windows/Linux EC2 instances. They need to collect system logs monthly, analyze with AWS Analytics tools, and store results in S3.

What is the most efficient way to collect and analyze logs with minimal effort?

## Options

A. Install AWS Inspector Agent. Set up CloudWatch dashboard.

B. Install SSM Agent. Analyze logs with CloudWatch Logs Insights.

C. Install unified CloudWatch Logs agent. Analyze with CloudWatch Logs Insights.

D. Install AWS SDK with custom daemon script. Enable detailed monitoring.

## Correct Answer

**C. Install unified CloudWatch Logs agent. Analyze with CloudWatch Logs Insights.**

## Explanation

The unified CloudWatch agent:
- **Collects logs and metrics**: Single agent for both
- **Windows/Linux support**: Works on both OS types
- **Push to CloudWatch Logs**: Automatic log forwarding
- **CloudWatch Logs Insights**: SQL-like queries for log analysis

### Why other options are incorrect:

- **A** - Inspector is for security vulnerability scanning, not log collection.

- **B** - SSM Agent requires manual log viewing. CloudWatch agent is more efficient.

- **D** - Custom scripts require development and maintenance overhead.

## References

- https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/AnalyzingLogData.html
- https://tutorialsdojo.com/amazon-cloudwatch/

## Domain

Design High-Performing Architectures
