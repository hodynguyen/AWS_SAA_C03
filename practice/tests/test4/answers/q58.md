# Question 58

## Topic
Design Secure Architectures

## Question
A hospital has a mission-critical application that uses a RESTful API powered by Amazon API Gateway and AWS Lambda. The medical officers upload PDF reports to the system which are then stored as static media content in an Amazon S3 bucket.

The security team wants to improve its visibility when it comes to cyber-attacks and ensure HIPAA (Health Insurance Portability and Accountability Act) compliance. The company is searching for a solution that continuously monitors object-level S3 API operations and identifies protected health information (PHI) in the reports, with minimal changes in the existing Lambda function.

Which of the following solutions will meet these requirements with the LEAST operational overhead?

## Options
A. Use Amazon Transcribe to read and analyze the PDF reports using the StartTranscriptionJob API operation. Use Amazon CloudWatch Logs to detect protected health information (PHI) content by tracking access logs and security events.

B. Use Amazon Textract Medical with PII redaction turned on to extract and filter sensitive text from the PDF reports. Create a new Lambda function that calls the regular Amazon Comprehend API to identify the PHI from the extracted text.

C. Use Amazon Textract to extract the text from the PDF reports. Integrate Amazon Comprehend Medical with the existing Lambda function to identify the PHI from the extracted text.

D. Use Amazon Textract with the StartDocumentTextDetection API operation to extract text from PDF reports. Analyze the extracted data with a custom-built PHI detection algorithm within the Lambda function.

## Correct Answer
C

## Explanation
Amazon Comprehend Medical is a natural language processing service that makes it easy to use machine learning to extract relevant medical information from unstructured text. Using Amazon Comprehend Medical, you can quickly and accurately gather information, such as medical conditions, medication, dosage, strength, and frequency from a variety of sources, like doctors’ notes, clinical trial reports, and patient health records.

Amazon Comprehend Medical uses advanced machine learning models to accurately and quickly identify medical information such as medical conditions and medication and determine their relationship to each other, for instance, medication and dosage. You access Comprehend Medical through a simple API call, no machine learning expertise is required, no complicated rules to write, and no models to train.

You can use the extracted medical information and their relationships to build applications for use cases, like clinical decision support, revenue cycle management (medical coding), and clinical trial management. Because Comprehend Medical is HIPAA-eligible and can quickly identify protected health information (PHI), such as name, age, and medical record number, you can also use it to create applications that securely process, maintain, and transmit PHI.

Hence, the correct answer is: Use Amazon Textract to extract the text from the PDF reports. Integrate Amazon Comprehend Medical with the existing Lambda function to identify the PHI from the extracted text.

References:

https://aws.amazon.com/comprehend/medical/

https://docs.aws.amazon.com/comprehend-medical/latest/dev/textanalysis-phi.html

Check out this Amazon Comprehend Cheat Sheet:

https://tutorialsdojo.com/amazon-comprehend

**Why other options are incorrect:**

- The option that says: Use Amazon Textract Medical with PII redaction turned on to extract and filter sensitive text from the PDF reports. Create a new Lambda function that calls the regular Amazon Comprehend API to identify the PHI from the extracted text is incorrect. The PII (Personally Identifiable Information) redaction feature of the Amazon Textract Medical service is not enough to identify all the Protected Health Information (PHI) in the PDF reports. Take note that PII is quite different from PHI. In addition, this option proposes to create a brand new Lambda function, which is contrary to what the company explicitly requires of having a minimal change in their existing Lambda function.

- The option that says: Use Amazon Transcribe to read and analyze the PDF reports using the StartTranscriptionJob API operation. Use Amazon CloudWatch Logs to detect protected health information (PHI) content by tracking access logs and security events is incorrect because Amazon Transcribe is an automatic speech recognition (ASR) service designed primarily to help developers integrate speech-to-text capability to their applications, and not for extracting text from image files or PDFs. Moreover, CloudWatch Logs cannot perform PHI detection directly.

- The option that says: Use Amazon Textract with the StartDocumentTextDetection API operation to extract text from PDF reports. Analyze the extracted data with a custom-built PHI detection algorithm within the Lambda function is incorrect because creating and maintaining a custom PHI detection algorithm typically increases operational overhead. This approach is inefficient compared to integrating a pre-built, HIPAA-compliant service like Amazon Comprehend Medical.

