# Question 16

## Topic
Design High-Performing Architectures

## Question
A web-based application must extract specific data from a large CSV file stored in an Amazon S3 bucket. The application requires filtering or transforming the data dynamically before returning it, ensuring that only the needed data is returned without downloading the entire object.

Which of the following actions should be implemented to achieve this?

## Options
A. Use S3 Object Lambda with a Lambda function that processes the data based on the bucket's name and object's metadata.

B. Use S3 Object Lambda with a Lambda function that processes the data based on the bucket's name and object's key.

C. Use S3 Object Lambda with a Lambda function that processes the data based on the bucket's name and object tags.

D. Use S3 Object Lambda with a Lambda function that processes the data based on the bucket's name.

## Correct Answer
B

## Explanation
Amazon S3 Object Lambda allows users to add custom code to process and transform data when retrieving it from S3. This means that applications can retrieve and modify the data dynamically without the need to create additional storage copies.

A Lambda function must be configured to process the data based on parameters, such as the object's key (file name) and bucket details, to properly identify and retrieve the specific file.

**Why other options are incorrect:**
- **Option A** is incorrect because metadata only provides additional information about the object, not the actual content.
- **Option C** is incorrect because object tags are for organizing and categorizing objects, not for data filtering.
- **Option D** is incorrect because the bucket name alone is insufficient to retrieve specific files.

## References
- https://aws.amazon.com/s3/features/object-lambda/
- https://docs.aws.amazon.com/AmazonS3/latest/userguide/transforming-objects.html
- https://tutorialsdojo.com/amazon-s3/
