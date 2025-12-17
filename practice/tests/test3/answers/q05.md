# Question 5

## Topic
Design Secure Architectures

## Question
A travel company has a suite of web applications hosted in an Auto Scaling group of On-Demand EC2 instances behind an Application Load Balancer that handles traffic from various web domains such as i-love-manila.com, i-love-boracay.com, i-love-cebu.com and many others. To improve security and lessen the overall cost, you are instructed to secure the system by allowing multiple domains to serve SSL traffic without the need to reauthenticate and reprovision your certificate everytime you add a new domain. This migration from HTTP to HTTPS will help improve their SEO and Google search ranking.

Which of the following is the most cost-effective solution to meet the above requirement?

## Options
A. Use a wildcard certificate to handle multiple sub-domains and different domains.

B. Add a Subject Alternative Name (SAN) for each additional domain to your certificate.

C. Create a new CloudFront web distribution and configure it to serve HTTPS requests using dedicated IP addresses in order to associate your alternate domain names with a dedicated IP address in each CloudFront edge location.

D. Upload all SSL certificates of the domains in the ALB using the console and bind multiple certificates to the same secure listener on your load balancer. ALB will automatically choose the optimal TLS certificate for each client using Server Name Indication (SNI).

## Correct Answer
D

## Explanation
SNI Custom SSL relies on the SNI extension of the Transport Layer Security protocol, which allows multiple domains to serve SSL traffic over the same IP address by including the hostname which the viewers are trying to connect to.

You can host multiple TLS-secured applications, each with its own TLS certificate, behind a single load balancer. In order to use SNI, all you need to do is bind multiple certificates to the same secure listener on your load balancer. ALB will automatically choose the optimal TLS certificate for each client.

**Why other options are incorrect:**
- **Option A** is incorrect because a wildcard certificate can only handle multiple sub-domains but not different domains.
- **Option B** is incorrect because using SAN still requires you to reauthenticate and reprovision your certificate every time you add a new domain.
- **Option C** is incorrect because using dedicated IP addresses is not cost-effective. You incur additional monthly charges when using dedicated IP addresses.

## References
- https://aws.amazon.com/blogs/aws/new-application-load-balancer-sni/
- https://docs.aws.amazon.com/elasticloadbalancing/latest/application/create-https-listener.html
- https://tutorialsdojo.com/amazon-cloudfront/
