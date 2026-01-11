# Question 38

## Topic
Design High-Performing Architectures

## Question
A Solutions Architect working for a startup is designing a High Performance Computing (HPC) application which is publicly accessible for their customers. The startup founders want to mitigate distributed denial-of-service (DDoS) attacks on their application.

Which of the following options are not suitable to be implemented in this scenario? (Select TWO.)

## Options
A. Use an Amazon CloudFront service for distributing both static and dynamic content.

B. Use AWS Shield and AWS WAF.

C. Use an Application Load Balancer with Auto Scaling groups for your EC2 instances. Prevent direct Internet traffic to your Amazon RDS database by deploying it to a new private subnet.

D. Use Dedicated EC2 instances to ensure that each instance has the maximum performance possible.

E. Add multiple Elastic Fabric Adapters (EFA) to each EC2 instance to increase the network bandwidth.

## Correct Answers
**D. Use Dedicated EC2 instances to ensure that each instance has the maximum performance possible.**

**E. Add multiple Elastic Fabric Adapters (EFA) to each EC2 instance to increase the network bandwidth.**

## Explanation
Dedicated EC2 instances are an instance billing option, not a DDoS mitigation technique. While it may ensure maximum performance, that alone is not enough to mitigate a DDoS attack.

Adding multiple Elastic Fabric Adapters (EFA) is for performance improvement in HPC, not for DDoS attack mitigation. Moreover, you can only attach one EFA per EC2 instance.

**Valid mitigation techniques include:**
- CloudFront for distributing content
- ALB with Auto Scaling
- AWS Shield and AWS WAF

## References
- https://aws.amazon.com/answers/networking/aws-ddos-attack-mitigation/
- https://d0.awsstatic.com/whitepapers/DDoS_White_Paper_June2015.pdf
