# Question 23

A company has a regional API Gateway in us-east-2. They want to associate custom domain `api.tutorialsdojo.com` with HTTPS support.

What is the next step?

## Options

A. Import certificate into ACM in us-east-2. Create a Route 53 CNAME record pointing to the API invoke URL.

B. Request certificate in us-east-1. Create regional API Gateway domain name. Create Route 53 alias record.

C. Request certificate in us-east-2. Create regional API Gateway domain name. Create Route 53 alias record.

D. Use ACM PCA for a private certificate. Override invoke URL using stage variables.

## Correct Answer

**C. Request certificate in us-east-2. Create regional API Gateway domain name. Create Route 53 alias record.**

## Explanation

For Regional API Gateway custom domains:
1. **Certificate in same region**: ACM certificate must be in the same region as the API (us-east-2)
2. **Custom Domain Name**: Create in API Gateway and associate with the certificate
3. **Route 53 Alias Record**: Points custom domain to the API Gateway domain name

### Why other options are incorrect:

- **A** - CNAME records don't work for root/apex domains. API Gateway requires Custom Domain Names feature.

- **B** - For Regional APIs, certificate must be in the same region (us-east-2, not us-east-1).

- **D** - Private certificates are for internal use only, not public HTTPS.

## References

- https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-api-endpoint-types.html
- https://docs.aws.amazon.com/acm/latest/userguide/acm-overview.html

## Domain

Design Secure Architectures
