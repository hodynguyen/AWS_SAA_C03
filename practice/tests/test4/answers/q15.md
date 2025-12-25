# Question 15

## Topic
Design Secure Architectures

## Question
A media company needs to configure an Amazon S3 bucket to serve static assets for the public-facing web application. Which methods ensure that all of the objects uploaded to the S3 bucket can be read publicly all over the Internet? (Select TWO.)

## Options
A. Grant public read access to the object when uploading it using the S3 Console.

B. Configure the cross-origin resource sharing (CORS) of the S3 bucket to allow objects to be publicly accessible from all domains.

C. Create an IAM role to set the objects inside the S3 bucket to public read.

D. Do nothing. Amazon S3 objects are already public by default.

E. Configure the S3 bucket policy to set all objects to public read.

## Correct Answer
A, E

## Explanation
By default, all Amazon S3 resources such as buckets, objects, and related subresources are private, which means that only the AWS account holder (resource owner) that created it has access to the resource. The resource owner can optionally grant access permissions to others by writing an access policy. In S3, you also set the permissions of the object during upload to make it public.

Amazon S3 offers access policy options broadly categorized as resource-based policies and user policies. Access policies you attach to your resources (buckets and objects) are referred to as resource-based policies.

For example, bucket policies and access control lists (ACLs) are resource-based policies. You can also attach access policies to users in your account. These are called user policies. You may choose to use resource-based policies, user policies, or some combination of these to manage permissions to your Amazon S3 resources.

You can also manage the public permissions of your objects during upload. Under Manage public permissions, you can grant read access to your objects to the general public (everyone in the world) for all of the files that you're uploading. Granting public read access is applicable to a small subset of use cases, such as when buckets are used for websites.

Hence, the correct answers are:

- Grant public read access to the object when uploading it using the S3 Console.

- Configure the S3 bucket policy to set all objects to public read.

References:

http://docs.aws.amazon.com/AmazonS3/latest/dev/s3-access-control.html

https://docs.aws.amazon.com/AmazonS3/latest/dev/BucketRestrictions.html

Check out this Amazon S3 Cheat Sheet:

https://tutorialsdojo.com/amazon-s3/

**Why other options are incorrect:**

- The option that says: Configure the cross-origin resource sharing (CORS) of the S3 bucket to allow objects to be publicly accessible from all domains is incorrect. CORS will only allow objects from one domain (travel.cebu.com) to be loaded and accessible to a different domain (palawan.com). It won't necessarily expose objects for public access all over the internet.

- The option that says: Creating an IAM role to set the objects inside the S3 bucket to public read is incorrect. You can create an IAM role and attach it to an EC2 instance in order to retrieve objects from the S3 bucket or add new ones. An IAM Role, in itself, cannot directly make the S3 objects public or change the permissions of each individual object.

- The option that says: Do nothing. Amazon S3 objects are already public by default is incorrect because, by default, all the S3 resources are private, so only the AWS account that created the resources can access them.

