# Question 41

## Topic
Design Resilient Architectures

## Question
A company is setting up a cloud architecture for an international money transfer service to be deployed in AWS which will have thousands of users around the globe. The service should be available 24/7 to avoid any business disruption and should be resilient enough to handle the outage of an entire AWS region. To meet this requirement, the Solutions Architect has deployed their AWS resources to multiple AWS Regions. He needs to use Route 53 and configure it to set all of the resources to be available all the time as much as possible. When a resource becomes unavailable, Route 53 should detect that it's unhealthy and stop including it when responding to queries.

Which of the following is the most fault-tolerant routing configuration that the Solutions Architect should use in this scenario?

## Options
A. Configure an Active-Active Failover with One Primary and One Secondary Resource.

B. Configure an Active-Passive Failover with Multiple Primary and Secondary Resources.

C. Configure an Active-Active Failover with Weighted routing policy.

D. Configure an Active-Passive Failover with Weighted Records.

## Correct Answer
C

## Explanation
**Active-Active Failover**

Use this failover configuration when you want all of your resources to be available the majority of the time. When a resource becomes unavailable, Route 53 can detect that it's unhealthy and stop including it when responding to queries.

In active-active failover, all the records that have the same name, the same type, and the same routing policy are active unless Route 53 considers them unhealthy. Route 53 can respond to a DNS query using any healthy record.

**Why other options are incorrect:**
- **Option A** is incorrect because Active-Active Failover doesn't have primary/secondary resources.
- **Options B and D** are incorrect because Active-Passive is for when you want primary resources available most of the time with standby secondary resources.

## References
- https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover-types.html
- https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html
- https://tutorialsdojo.com/amazon-route-53/
