# Question 63

## Topic
Design Secure Architectures

## Question
A company has an Application Load Balancer (ALB) that accepts HTTP and HTTPS traffic on ports 80 and 443, respectively. Recently, the company associated a new domain for its website, and they want to ensure that all HTTP traffic for this new domain is automatically redirected to HTTPS to improve security.

Which ALB configuration should be done to satisfy the requirement?

## Options
A. Configure the existing on port 443 and add a redirect action to HTTP on port 80.

B. Configure the existing HTTP listener to redirect traffic to port 443.

C. Create a new HTTP listener on port 80 and add a redirect action to the HTTPS protocol on port 443.

D. Create a new ALB listener on port 443 and configure it to redirect HTTP traffic to HTTPS.

## Correct Answer
B

## Explanation
Application Load Balancer operates at the application layer (layer 7), routing traffic to targets such as EC2 instances, containers, IP addresses, and Lambda functions based on the requested content. It is ideal for advanced load balancing of HTTP and HTTPS traffic, providing enhanced request routing for modern application architectures like microservices and container-based applications. Additionally, it simplifies and improves application security by always utilizing the latest SSL/TLS ciphers and protocols.

Configuring the existing ALB listener on port 80 to redirect traffic to port 443 is the most appropriate solution for redirecting HTTP to HTTPS traffic. This can be achieved by setting up a redirect rule for the listener. By doing this, all HTTP traffic will be automatically redirected to HTTPS, thus improving the security of the website.

Hence, the correct answer in this scenario is: Configure the existing HTTP listener to redirect traffic to port 443.

References:

https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html

https://aws.amazon.com/elasticloadbalancing/application-load-balancer/

Check out this AWS Elastic Load Balancing Cheat Sheet:

https://tutorialsdojo.com/aws-elastic-load-balancing-elb/

**Why other options are incorrect:**

- The option that says: Create a new HTTP listener on port 80 and add a redirect action to the HTTPS protocol on port 443 while this is the correct way of redirecting HTTP to HTTPS, creating a new HTTP listener on port 80 is not possible because there is already an existing listener assigned to that port.

- The option that says: Create a new ALB listener on port 443 and configure it to redirect HTTP traffic to HTTPS is not possible because you can’t have duplicate ports opened in ALB. Take note that there’s already an existing HTTPS listener on port 443.

- The option that says: Configure the existing on port 443 and add a redirect action to HTTP on port 80 is incorrect as this configuration goes against the objective stated in the question. The requirement is to automatically redirect HTTP traffic to HTTPS, not the other way around.

