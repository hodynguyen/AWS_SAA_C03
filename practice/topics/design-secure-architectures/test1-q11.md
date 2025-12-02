# Question 11

A software development company is using serverless computing with AWS Lambda to build and run applications without having to set up or manage servers. The company has a Lambda function that connects to a MongoDB Atlas, which is a popular Database as a Service (DBaaS) platform, and also uses a third-party API to fetch certain data for its application. One of the developers was instructed to create the environment variables for the MongoDB database hostname, username, and password, as well as the API credentials that will be used by the Lambda function for DEV, SIT, UAT, and PROD environments.

Considering that the Lambda function is storing sensitive database and API credentials, how can this information be secured to prevent other developers on the team, or anyone, from seeing these credentials in plain text? Select the best option that provides maximum security.

## Options

A. There is no need to do anything because, by default, Lambda already encrypts the environment variables using the AWS Key Management Service.

B. Lambda does not provide encryption for the environment variables. Deploy your code to an Amazon EC2 instance instead.

C. Create a new AWS KMS key and use it to enable encryption helpers that leverage on AWS Key Management Service to store and encrypt the sensitive information.

D. Enable SSL encryption that leverages on AWS CloudHSM to store and encrypt the sensitive information.

## Correct Answer

**C. Create a new AWS KMS key and use it to enable encryption helpers that leverage on AWS Key Management Service to store and encrypt the sensitive information.**

## Explanation

When you create or update Lambda functions that use environment variables, AWS Lambda encrypts them using the AWS Key Management Service. When your Lambda function is invoked, those values are decrypted and made available to the Lambda code.

The first time you create or update Lambda functions that use environment variables in a region, a default service key is created for you automatically within AWS KMS. However, if you wish to use encryption helpers and use KMS to encrypt environment variables after your Lambda function is created, you must create your own AWS KMS key and choose it instead of the default key. Creating your own key gives you more flexibility, including the ability to create, rotate, disable, and define access controls, and to audit the encryption keys used to protect your data.

### Why other options are incorrect:

- **A** - Although Lambda encrypts the environment variables in your function by default, the sensitive information would still be visible to other users who have access to the Lambda console. This is because Lambda uses a default KMS key to encrypt the variables, which is usually accessible by other users.

- **D** - Enabling SSL would encrypt data only when in-transit. Your other teams would still be able to view the plaintext at-rest.

- **B** - Lambda does provide encryption functionality of environment variables.

## References

- https://docs.aws.amazon.com/lambda/latest/dg/env_variables.html#env_encrypt
- https://docs.aws.amazon.com/lambda/latest/dg/tutorial-env_console.html
- https://tutorialsdojo.com/aws-lambda/

## Domain

Design Secure Architectures
