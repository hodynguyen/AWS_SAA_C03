# Question 41

A DevOps Engineer is required to design a cloud architecture in AWS. The Engineer is planning to develop a highly available and fault-tolerant architecture consisting of an Elastic Load Balancer and an Auto Scaling group of EC2 instances deployed across multiple Availability Zones. This will be used by an online accounting application that requires path-based routing, host-based routing, and bi-directional streaming using Remote Procedure Call (gRPC).

Which configuration will satisfy the given requirement?

## Options

A. Configure a Network Load Balancer in front of the auto-scaling group. Create an AWS Global Accelerator.

B. Configure a Network Load Balancer in front of the auto-scaling group. Use a UDP listener for routing.

C. Configure a Gateway Load Balancer in front of the auto-scaling group. Use the GENEVE protocol on port 6081.

D. Configure an Application Load Balancer in front of the auto-scaling group. Select gRPC as the protocol version.

## Correct Answer

**D. Configure an Application Load Balancer in front of the auto-scaling group. Select gRPC as the protocol version.**

## Explanation

Application Load Balancer operates at Layer 7, providing path-based routing, host-based routing, and gRPC support. ALBs can route and load balance gRPC traffic between microservices.

### Why other options are incorrect:

- **A, B** - NLB doesn't support gRPC.

- **C** - Gateway Load Balancer operates at Layer 3/4, not Layer 7.

## References

- https://aws.amazon.com/elasticloadbalancing/features
- https://tutorialsdojo.com/aws-elastic-load-balancing-elb/

## Domain

Design Resilient Architectures
