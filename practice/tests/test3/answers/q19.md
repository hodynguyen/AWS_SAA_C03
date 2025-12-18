# Question 19

## Topic
Design High-Performing Architectures

## Question
An on-premises server uses an SMB network file share to store application data. The application produces around 50 MB of data per day, but it only needs to access some of it for daily processes. To save on storage costs, the company plans to copy all the application data to AWS. However, the goal is to retain the ability to retrieve data with the same low-latency access as the local file share. The company does not have the capacity to develop the needed tools for this operation.

Which of the following should the company use?

## Options
A. AWS Snowball Edge

B. AWS Virtual Private Network (VPN)

C. Amazon FSx for Windows File Server

D. AWS Storage Gateway

## Correct Answer
D

## Explanation
AWS Storage Gateway is a hybrid cloud storage service that gives you on-premises access to virtually unlimited cloud storage. You can use the File Gateway configuration to support the SMB file share for the on-premises application. It also meets the requirement for low-latency access.

File Gateway helps accelerate your file-based storage migration to the cloud to enable faster performance, improved data protection, and reduced cost. It supports local caching without any development overhead.

**Why other options are incorrect:**
- **Option A** is incorrect because Snowball Edge is a data migration tool, not a storage service.
- **Option B** is incorrect because VPN is for establishing encrypted connections, not for storage.
- **Option C** is incorrect because FSx won't provide low-latency access since all files are stored on AWS.

## References
- https://aws.amazon.com/storagegateway/
- https://docs.aws.amazon.com/storagegateway/latest/userguide/CreatingAnSMBFileShare.html
- https://tutorialsdojo.com/aws-storage-gateway/
