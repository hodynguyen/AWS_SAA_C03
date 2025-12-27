# Question 46

## Topic
Design High-Performing Architectures

## Question
A startup plans to develop a multiplayer game that uses UDP as the protocol for communication between clients and game servers. The data of the users will be stored in a key-value store. As the Solutions Architect, you need to implement a solution that will distribute the traffic across a number of servers.

Which of the following could help you achieve this requirement?

## Options
A. Distribute the traffic using Application Load Balancer and store the data in Amazon RDS.

B. Distribute the traffic using Network Load Balancer and store the data in Amazon DynamoDB.

C. Distribute the traffic using Network Load Balancer and store the data in Amazon Aurora.

D. Distribute the traffic using Application Load Balancer and store the data in Amazon DynamoDB.

## Correct Answer
B

## Explanation
A Network Load Balancer functions at the fourth layer of the Open Systems Interconnection (OSI) model. It can handle millions of requests per second. After the load balancer receives a connection request, it selects a target from the target group for the default rule. For UDP traffic, the load balancer selects a target using a flow hash algorithm based on the protocol, source IP address, source port, destination IP address, and destination port. A UDP flow has the same source and destination, so it is consistently routed to a single target throughout its lifetime. Different UDP flows have a different source IP addresses and ports, so they can be routed to different targets.

In this scenario, a startup plans to create a multiplayer game that uses UDP as the protocol for communications. Since UDP is a Layer 4 traffic, we can limit the option that uses Network Load Balancer. The data of the users will be stored in a key-value store. This means that we should select Amazon DynamoDB since it supports both document and key-value store models.

Hence, the correct answer is: Distribute the traffic using Network Load Balancer and store the data in Amazon DynamoDB.

References:

https://aws.amazon.com/blogs/aws/new-udp-load-balancing-for-network-load-balancer/

https://docs.aws.amazon.com/elasticloadbalancing/latest/network/introduction.html

Check out this AWS Elastic Load Balancing (ELB) Cheat Sheet:

https://tutorialsdojo.com/aws-elastic-load-balancing-elb/

**Why other options are incorrect:**

- The option that says: Distribute the traffic using Application Load Balancer and store the data in Amazon DynamoDB is incorrect because UDP is not supported in Application Load Balancer. Remember that UDP is a Layer 4 traffic. Therefore, you should use a Network Load Balancer.

- The option that says: Distribute the traffic using Network Load Balancer and store the data in Amazon Aurora is incorrect because Amazon Aurora is a relational database service. Instead of Aurora, you should use Amazon DynamoDB.

- The option that says: Distribute the traffic using Application Load Balancer and store the data in Amazon RDS is incorrect because Application Load Balancer only supports application traffic (Layer 7). Also, Amazon RDS is not suitable as a key-value store. You should use DynamoDB since it supports both document and key-value store models.

