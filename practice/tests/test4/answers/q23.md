# Question 23

## Topic
Design Secure Architectures

## Question
A company has a regional API Gateway in the us-east-2 region that serves as a proxy to a backend service. Clients connect to the service using the invoke URL of the API stage. To improve usability, the company wants to associate a custom domain name (api.tutorialsdojo.com) with the API. Moreover, the domain name must support HTTPS to ensure secure connections. The company has an existing hosted zone for its domain on Amazon Route 53.

Which of the following would be the next step to achieve the company's objective?

## Options
A. Import an existing public certificate for api.tutorialsdojo.com into AWS Certificate Manager (ACM) in the us-east-2. In Route 53, create a CNAME record for api.tutorialsdojo.com that points to the invoke URL of the API Gateway stage.

B. Request a public certificate in the us-east-1 region for api.tutorialsdojo.com using AWS Certificate Manager (ACM). Create a regional API Gateway domain name and associate it with api.tutorialsdojo.com and the ACM certificate. In Route 53, create an alias record for api.tutorialsdojo.com that points to the API Gateway domain name.

C. Request a public certificate in the us-east-2 region for api.tutorialsdojo.com using AWS Certificate Manager (ACM). Create a regional API Gateway domain name and associate it with api.tutorialsdojo.com and the ACM certificate. In Route 53, create an alias record for api.tutorialsdojo.com that points to the API Gateway domain name.

D. Use the AWS Certificate Manager Private Certificate Authority (ACM PCA) to generate a private certificate for api.tutorialsdojo.com. Override the invoke URL using stage variables.

## Correct Answer
C

## Explanation
In API Gateway, A Regional API is an API deployed to a specified Region and intended to serve clients, such as EC2 instances, in the same AWS Region. API requests are targeted directly to the Region-specific API Gateway API without going through any CloudFront distribution. For in-Region requests, a Regional endpoint bypasses the unnecessary round trip to a CloudFront distribution.

When using a regional API, any custom domain name you choose is exclusive to the specific region where the API is deployed. If you deploy the same regional API in multiple regions, it can have the same custom domain name across all regions. Also, you must request or import the SSL certificate in the same Region as your API.

To meet the requirement in the scenario, you must first request a public certificate for your custom domain from the AWS Certificate Manager (ACM) in the same region as your API Gateway. This certificate will secure HTTPS connections to your API. Then, you configure a regional API Gateway domain name, and associate it with your custom domain and the ACM certificate. Finally, you create an alias record in Route 53, which maps your custom domain to the API Gateway's domain name. With this setup, client requests to your custom domain will be securely routed to the correct API Gateway.

Hence the correct answer is: Request a public certificate in the us-east-2 region for api.tutorialsdojo.com using AWS Certificate Manager (ACM). Create a regional API Gateway domain name and associate it with api.tutorialsdojo.com and the ACM certificate. In Route 53, create an alias record for api.tutorialsdojo.com that points to the API Gateway domain name.

References:

https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-api-endpoint-types.html

https://docs.aws.amazon.com/acm/latest/userguide/acm-overview.html

https://docs.aws.amazon.com/route53/

Tutorials Dojo's AWS Certified Solutions Architect Associate Exam – SAA-C03 Study Path:

https://tutorialsdojo.com/aws-certified-solutions-architect-associate-saa-c03/

**Why other options are incorrect:**

- The option that says: Use the AWS Certificate Manager Private Certificate Authority (ACM PCA) to generate a private certificate for api.tutorialsdojo.com. Override the invoke URL using stage variables is incorrect. Private certificates are used within an internal network. A public certificate is required to enable secure connections from the public internet to the API. Also, overriding the invoke URL using stage variables is not relevant to the scenario.

- The option that says: Import an existing public certificate for api.tutorialsdojo.com into AWS Certificate Manager (ACM) in the us-east-2. In Route 53, create a CNAME record for api.tutorialsdojo.com that points to the invoke URL of the API Gateway stage is incorrect. This won't work. To use a custom domain name with Amazon API Gateway, you should use API Gateway's Custom Domain Names feature. This will allow you to specify your desired domain name, map it to your API, and correctly configure an SSL/TLS certificate.

- The option that says: Request a public certificate in the us-east-1 region for api.tutorialsdojo.com using AWS Certificate Manager (ACM). Create a regional API Gateway domain name and associate it with api.tutorialsdojo.com and the ACM certificate. In Route 53, create an alias record for api.tutorialsdojo.com that points to the API Gateway domain name is incorrect because it suggests configuring the Regional API Gateway endpoint in the wrong region. For a regional API Gateway, the certificate must be requested/imported in the same region as your API.

