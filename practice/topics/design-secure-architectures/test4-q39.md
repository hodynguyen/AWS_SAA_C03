# Question 39

## Topic
Design Secure Architectures

## Question
A company has several web applications with users all around the world. Each application is hosted in an Auto Scaling group of EC2 instances in multiple AZs behind an Application Load Balancer (ALB). All applications have their own fully qualified domain name. For added security, the applications must use a publicly trusted SSL certificate.

Which solution will meet this requirement with the LEAST operational overhead?

## Options
A. Launch a self-hosted certificate authority (CA) using the Let's Encrypt tool in an Amazon EC2 instance. Utilize the built-in ISRG Root X1 trusted root CA certificate. Generate a new SSL/TLS certificate using the certbot CLI utility. Associate the new certificate on the HTTPS listener of the ALBs.

B. Issue an SSL/TLS certificate using the AWS Certificate Manager Private Certificate Authority. Associate the new certificate on the HTTPS listener of the ALBs.

C. Use OpenSSL to generate a self-signed certificate. Import the SSL/TLS certificate to the AWS Certificate Manager (ACM) and associate it with the HTTPS listener of the ALBs

D. Use the AWS Certificate Manager (ACM) to generate a public SSL/TLS certificate. Associate the new SSL/TLS certificate on the HTTPS listener of the ALBs.

## Correct Answer
D

## Explanation
There are two AWS services for issuing and deploying X.509 certificates. Choose the one that best fits your needs. Considerations include whether you need public- or private-facing certificates, customized certificates, certificates you want to deploy into other AWS services, or automated certificate management and renewal.

ACM Private CA—This service is for enterprise customers building a public key infrastructure (PKI) inside the AWS cloud and is intended for private use within an organization. With ACM Private CA, you can create your own CA hierarchy and issue certificates with it for authenticating internal users, computers, applications, services, servers, and other devices and for signing computer code. Certificates issued by a private CA are trusted only within your organization, not on the internet.

AWS Certificate Manager (ACM) — This service manages certificates for enterprise customers who need a publicly trusted secure web presence using TLS. You can deploy ACM certificates into AWS Elastic Load Balancing, Amazon CloudFront, Amazon API Gateway, and other integrated services. The most common application of this kind is a secure public website with significant traffic requirements.

With this service, you can use public certificates provided by ACM (ACM certificates) or certificates that you import into ACM. If you use ACM Private CA to create a CA, ACM can manage certificate issuance from that private CA and automate certificate renewals.

One of the key differences between the regular ACM and ACM Private Certificate Authority(PCA) is the ability to create a Root CA (for establishing new CA hierarchy). This enables the ACM PCA service to generate private certificates. ACM PCA can also generate a private subordinate CA.

In addition to requesting SSL/TLS certificates provided by AWS Certificate Manager (ACM), you can import certificates that you obtained outside of AWS. You might do this because you already have a certificate from a third-party certificate authority (CA) or because you have application-specific requirements that are not met by ACM issued certificates.

To renew an imported certificate, you can obtain a new certificate from your certificate issuer and then manually reimport it into ACM. This action preserves the certificate's association and its Amazon Resource Name (ARN). Alternatively, you can import a completely new certificate. Multiple certificates with the same domain name can be imported, but they must be imported one at a time.

Take note that the scenario asked for a publicly trusted SSL certificate and not a private certificate. Hence, the correct answer is: Use the AWS Certificate Manager (ACM) to generate a public SSL/TLS certificate. Associate the new SSL/TLS certificate on the HTTPS listener of the ALBs.

References:

https://docs.aws.amazon.com/acm/latest/userguide/acm-overview.html

https://docs.aws.amazon.com/acm-pca/latest/userguide/PcaWelcome.html

https://docs.aws.amazon.com/acm/latest/userguide/import-certificate.html

Check out this AWS Certificate Manager (ACM) Cheat Sheet:

https://tutorialsdojo.com/aws-certificate-manager/

**Why other options are incorrect:**

- The option that says: Launch a self-hosted certificate authority (CA) using the Let's Encrypt tool in an Amazon EC2 instance. Utilize the built-in ISRG Root X1 trusted root CA certificate. Generate a new SSL/TLS certificate using the certbot CLI utility. Associate the new certificate on the HTTPS listener of the ALBs is incorrect because you cannot directly associate an SSL/TLS certificate to an Application Load Balancer. The certificate must be first imported to ACM before it can be associated to the elastic load balancers in your account.

- The option that says: Use OpenSSL to generate a self-signed certificate. Import the SSL/TLS certificate to the AWS Certificate Manager (ACM) and associate it with the HTTPS listener of the ALBs is incorrect. Although this is a valid solution, this entails a lot of operational overhead since you have to generate multiple certificates yourself and manually import them to ACM. In addition, you have to manually reimport your certificate every year since self-signed certificates in ACM are not automatically renewed, unlike those generated from ACM.

- The option that says: Issue an SSL/TLS certificate using the AWS Certificate Manager Private Certificate Authority. Associate the new certificate on the HTTPS listener of the ALBs is incorrect because the scenario explicitly mentioned that you have to use a publicly trusted SSL certificate. Remember that the ACM PCA provides a private certificate, not a public one.

