# Question 35

A Solutions Architect needs to make sure that the On-Demand Amazon EC2 instance can only be accessed from this IP address (110.238.98.71) via an SSH connection.

Which configuration below will satisfy this requirement?

## Options

A. Security Group Outbound Rule: Protocol – TCP, Port Range – 22, Destination 110.238.98.71/32

B. Security Group Outbound Rule: Protocol – UDP, Port Range – 22, Destination 0.0.0.0/0

C. Security Group Inbound Rule: Protocol – TCP. Port Range – 22, Source 110.238.98.71/32

D. Security Group Inbound Rule: Protocol – UDP, Port Range – 22, Source 110.238.98.71/32

## Correct Answer

**C. Security Group Inbound Rule: Protocol – TCP. Port Range – 22, Source 110.238.98.71/32**

## Explanation

A security group acts as a virtual firewall for your instance to control inbound and outbound traffic. The /32 CIDR notation denotes a single IP address. SSH protocol uses TCP (not UDP) and runs on port 22.

Security groups are stateful, meaning they automatically allow return traffic associated with the client who initiated the connection.

### Why other options are incorrect:

- **D** - SSH runs over the TCP protocol, not UDP.

- **A** - This is an outbound rule, not an inbound rule. We need to limit inbound traffic.

- **B** - This is an outbound rule rather than an inbound rule, and SSH requires TCP.

## References

- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html
- https://docs.aws.amazon.com/vpc/
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/

## Domain

Design Secure Architectures
