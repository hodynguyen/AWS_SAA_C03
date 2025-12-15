# Question 42

A company is running a dashboard application on a Spot EC2 instance inside a private subnet. The dashboard is reachable via a domain name that maps to the private IPv4 address of the instance's network interface. A solutions architect needs to increase network availability by allowing the traffic flow to resume in another instance if the primary instance is terminated.

Which solution accomplishes these requirements?

## Options

A. Use the AWS Transit Gateway to automatically move an EIP to a secondary instance.

B. Create a secondary elastic network interface and point its private IPv4 address to the application's domain name. Attach the new network interface to the primary instance. If the instance goes down, move the secondary network interface to another instance.

C. Set up AWS Transfer for FTPS service to disable the source/destination checks.

D. Use the AWS Network Firewall to detach the instance's primary elastic network interface.

## Correct Answer

**B. Create a secondary elastic network interface and point its private IPv4 address to the application's domain name. Attach the new network interface to the primary instance. If the instance goes down, move the secondary network interface to another instance.**

## Explanation

A secondary ENI can be moved between EC2 instances. Because the ENI maintains its private IP address, traffic continues flowing to the standby instance as soon as the interface is attached.

### Why other options are incorrect:

- **D** - Primary ENI cannot be detached.

- **C** - AWS Transfer is for file transfer, not ENI management.

- **A** - Transit Gateway is for VPC connectivity.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-eni.html
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/

## Domain

Design Resilient Architectures
