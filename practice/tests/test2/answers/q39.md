# Question 39

A company owns a photo-sharing app that stores user uploads on Amazon S3. There has been an increase in explicit and offensive images being reported. The company wants to streamline moderation using Artificial Intelligence to flag images for review. Any communication with its resources on its Amazon VPC must not traverse the public Internet.

How can this task be accomplished with the LEAST amount of effort?

## Options

A. Use Amazon Detective to detect images with graphic nudity or violence in S3.

B. Use Amazon Rekognition to detect images with graphic nudity or violence in S3. Create an Interface VPC endpoint for Rekognition.

C. Use AWS Lambda to create custom image moderation logic. Deploy this Lambda function in a public VPC.

D. Use an image classification model in Amazon SageMaker. Set up Amazon GuardDuty.

## Correct Answer

**B. Use Amazon Rekognition to detect images with graphic nudity or violence in S3. Create an Interface VPC endpoint for Rekognition with the necessary policies to prevent any traffic from traversing the public Internet.**

## Explanation

Amazon Rekognition can detect inappropriate content containing nudity, suggestiveness, violence, and other categories. An interface VPC endpoint provides private connectivity to Rekognition without using the public internet.

### Why other options are incorrect:

- **A** - Detective is for security investigation, not image moderation.

- **D** - SageMaker requires training models; GuardDuty isn't for networking.

- **C** - Public VPC violates the private connectivity requirement.

## References

- https://aws.amazon.com/rekognition/content-moderation/
- https://tutorialsdojo.com/amazon-rekognition/

## Domain

Design High-Performing Architectures
