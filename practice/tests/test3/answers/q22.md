# Question 22

## Topic
Design Secure Architectures

## Question
A company has launched multiple Amazon EC2 instances inside a private subnet of a VPC. The Solutions Architect is reviewing the Network ACL (NACL) rules associated with that subnet to ensure security. The current Inbound Rules for the NACL are configured as follows:

A computer with the IP address 110.238.109.37 attempts to send a request to one of the EC2 instances in this subnet.

What will happen to the incoming request based on the NACL rules?

## Options
A. Initially, it will be denied and then after a while, the connection will be allowed.

B. It will be denied.

C. Initially, it will be allowed and then after a while, the connection will be denied.

D. It will be allowed.

## Correct Answer
D

## Explanation
When evaluating the incoming request, the Network ACL (NACL) processes rules sequentially, starting from the lowest rule number. NACLs are stateless, meaning they apply each rule independently and in the order defined.

Rule #100, which allows all traffic, is evaluated before Rule #101, which denies TCP port 4000 traffic from the specific IP. Since the request matches Rule #100, it will be allowed immediately, and Rule #101 will not be evaluated.

NACLs enforce a strict first-match policy.

**Why other options are incorrect:**
- **Option A** is incorrect because NACLs don't change decisions over time.
- **Option B** is incorrect because Rule #100 allows all traffic before Rule #101 which denies it.
- **Option C** is incorrect because NACLs don't dynamically reassess traffic.

## References
- https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html
- https://docs.aws.amazon.com/vpc/latest/userguide/nacl-rules.html
- https://tutorialsdojo.com/amazon-vpc/
