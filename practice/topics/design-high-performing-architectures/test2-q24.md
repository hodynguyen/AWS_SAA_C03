# Question 24

A business has a network of surveillance cameras installed within the premises of its data center. Management wants to leverage Artificial Intelligence to monitor and detect unauthorized personnel entering restricted areas. Should an unauthorized person be detected, the security team must be alerted via SMS.

Which solution satisfies the requirement?

## Options

A. Use Amazon Kinesis Video Streams to stream live feeds from the cameras. Use Amazon Rekognition to detect unauthorized personnel. Set the phone numbers of the security team as subscribers to an Amazon SNS topic.

B. Set up Amazon Managed Service for Prometheus to stream live feeds from the cameras. Use Amazon Fraud Detector to detect unauthorized personnel.

C. Configure Amazon Elastic Transcoder to stream live feeds from the cameras. Use Amazon Kendra to detect authorized personnel.

D. Utilize a custom containerized video processing application on Amazon EKS. Integrate AWS App2Container and Amazon SageMaker Autopilot.

## Correct Answer

**A. Use Amazon Kinesis Video Streams to stream live feeds from the cameras. Use Amazon Rekognition to detect unauthorized personnel. Set the phone numbers of the security team as subscribers to an Amazon SNS topic.**

## Explanation

Amazon Kinesis Video Streams makes it easy to securely stream video from connected devices to AWS. Amazon Rekognition Video can detect objects, scenes, faces, and celebrities in videos.

Combining these services creates an effective intruder alert system using face recognition.

### Why other options are incorrect:

- **C** - Elastic Transcoder is for media conversion; Kendra is for search.

- **D** - Custom EKS solution is complex and costly.

- **B** - Prometheus is for monitoring; Fraud Detector is for online fraud.

## References

- https://docs.aws.amazon.com/kinesisvideostreams/latest/dg/what-is-kinesis-video.html
- https://tutorialsdojo.com/amazon-rekognition/

## Domain

Design High-Performing Architectures
