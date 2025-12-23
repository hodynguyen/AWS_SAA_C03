# Question 65

## Topic
Design High-Performing Architectures

## Question
A solutions architect is designing an infrastructure for a serverless application. The application is packaged as a Docker image stored in Amazon Elastic Container Registry (Amazon ECR) and must be deployed on a fully managed serverless compute service. Additionally, the application requires 5 GB of ephemeral storage for temporary data processing.

Which deployment option meets these requirements?

## Options
A. Deploy the application in an AWS Lambda function with Container image support. Set the function’s storage to 5 GB.

B. Deploy the application to an Amazon ECS cluster that uses AWS Fargate tasks.

C. Deploy the application Amazon ECS cluster with Amazon EC2 worker nodes and attach a 5 GB Amazon EBS volume.

D. Deploy the application in an AWS Lambda function with Container image support. Attach an Amazon Elastic File System (Amazon EFS) volume to the function.

## Correct Answer
A

## Explanation
AWS Lambda with Container Image Support is a fully managed, serverless compute service that allows you to run your applications without provisioning or managing servers. Traditionally, AWS Lambda functions were deployed using code written in supported programming languages, but with container image support, you can now package and deploy your application as a Docker container. This provides more flexibility, as it allows you to use custom runtimes or include dependencies that are difficult to manage in a traditional Lambda function deployment. Lambda functions with container images can be up to 10 GB in size, enabling you to deploy large, complex applications with ease.

One of the key features of AWS Lambda is the ability to allocate ephemeral storage for each function instance. By default, Lambda functions come with 512 MB of temporary storage, but you can configure up to 10 GB of storage. This ephemeral storage is used for temporary data processing and is wiped clean after the execution of the function. This makes it a great choice for applications that need to perform tasks like data processing, file manipulation, or caching during their execution, without needing persistent storage.

Lambda with container image support provides a fully managed environment that automatically scales based on the workload. You are only billed for the compute time your code actually uses, and there are no charges for idle time, making it a cost-effective solution for many workloads. It abstracts away infrastructure management, ensuring that developers can focus on building applications without worrying about scaling, patching, or maintaining servers.

Hence, the correct answer is: Deploy the application in an AWS Lambda function with Container image support. Set the function’s storage to 5 GB.

The option that says: Deploy the application to an Amazon ECS cluster that uses AWS Fargate tasks is incorrect because Amazon ECS with Fargate tasks is not a fully serverless solution. While Fargate allows you to run containers without managing the underlying EC2 instances, it still requires you to configure and manage ECS services, task definitions, and clusters. ECS with Fargate is primarily used for containerized applications that require more granular control over the environment, including network configurations and scaling.

The option that says: Deploy the application in an AWS Lambda function with Container image support. Attach an Amazon Elastic File System (Amazon EFS) volume to the function is incorrect because it uses Amazon EFS for persistent storage, which is typically used for shared file systems that need to persist data across function invocations. However, the question specifies a need for ephemeral storage, which is temporary and does not require persistence. Attaching an EFS volume introduces additional complexity and is unnecessary when the application only needs temporary, in-memory storage during execution.

The option that says: Deploy the application Amazon ECS cluster with Amazon EC2 worker nodes and attach a 5 GB Amazon EBS volume is incorrect because the scenario explicitly mentioned that the architecture must be serverless. Using Amazon EC2 instances for your worker nodes is not a serverless architecture.

## References
- https://docs.aws.amazon.com/lambda/latest/dg/images-create.html
- https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/deploy-lambda-functions-with-container-images.html
- https://tutorialsdojo.com/aws-fargate/
- https://tutorialsdojo.com/aws-lambda/
