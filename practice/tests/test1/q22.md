# Question 22

A payment processing company plans to migrate its on-premises application to an Amazon EC2 instance. An IPv6 CIDR block is attached to the company's Amazon VPC. Strict security policy mandates that the production VPC must only allow outbound communication over IPv6 between the instance and the internet but should prevent the internet from initiating an inbound IPv6 connection. The new architecture should also allow traffic flow inspection and traffic filtering.

What should a solutions architect do to meet these requirements?

## Options

A. Launch the EC2 instance to a private subnet and attach a NAT Gateway to the VPC to allow outbound IPv6 communication to the internet. Use AWS Firewall Manager to set up the required rules for traffic inspection and traffic filtering.

B. Launch the EC2 instance to a private subnet and attach AWS PrivateLink interface endpoint to the VPC to control outbound IPv6 communication to the internet. Use Amazon GuardDuty to set up the required rules for traffic inspection and traffic filtering.

C. Launch the EC2 instance to a private subnet and attach an Egress-Only Internet Gateway to the VPC to allow outbound IPv6 communication to the internet. Use AWS Network Firewall to set up the required rules for traffic inspection and traffic filtering.

D. Launch the EC2 instance to a public subnet and attach an Internet Gateway to the VPC to allow outbound IPv6 communication to the internet. Use Traffic Mirroring to set up the required rules for traffic inspection and traffic filtering.

## Correct Answer

**C. Launch the EC2 instance to a private subnet and attach an Egress-Only Internet Gateway to the VPC to allow outbound IPv6 communication to the internet. Use AWS Network Firewall to set up the required rules for traffic inspection and traffic filtering.**

## Explanation

An egress-only internet gateway is a horizontally scaled, redundant, and highly available VPC component that allows outbound communication over IPv6 from instances in your VPC to the internet and prevents it from initiating an IPv6 connection with your instances.

IPv6 addresses are globally unique and are therefore public by default. If you want your instance to be able to access the internet, but you want to prevent resources on the internet from initiating communication with your instance, you can use an egress-only internet gateway.

AWS Network Firewall is a managed service that makes it easy to deploy essential network protections for all of your Amazon VPCs. AWS Network Firewall's stateful firewall can incorporate context from traffic flows, like tracking connections and protocol identification.

### Why other options are incorrect:

- **B** - AWS PrivateLink is just a highly available, scalable technology to privately connect your VPC to AWS services. It's not capable of controlling outbound IPv6 communication. GuardDuty doesn't have features for traffic inspection or filtering.

- **D** - An Internet Gateway does not limit or control any outgoing IPv6 connection. This solution allows all kinds of traffic to initiate a connection to your EC2 instance.

- **A** - While NAT Gateway has a NAT64 feature, it will not prevent inbound IPv6 traffic. AWS Firewall Manager is neither capable of doing traffic inspection nor traffic filtering.

## References

- https://docs.aws.amazon.com/vpc/latest/userguide/egress-only-internet-gateway.html
- https://docs.aws.amazon.com/vpc/latest/userguide/configure-subnets.html
- https://tutorialsdojo.com/amazon-vpc/

## Domain

Design Secure Architectures
