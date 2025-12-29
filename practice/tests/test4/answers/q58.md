# Question 58

A hospital application stores PDF reports in S3. The security team needs continuous S3 API monitoring and PHI (Protected Health Information) detection with minimal Lambda changes. HIPAA compliance is required.

Which solution has the least operational overhead?

## Options

A. Use Amazon Transcribe and CloudWatch Logs for PHI detection.

B. Use Textract Medical with PII redaction. Create new Lambda for Comprehend.

C. Use Amazon Textract to extract text. Integrate Comprehend Medical with existing Lambda.

D. Use Textract with custom PHI detection algorithm in Lambda.

## Correct Answer

**C. Use Amazon Textract to extract text. Integrate Comprehend Medical with existing Lambda.**

## Explanation

- **Amazon Textract**: Extracts text from PDFs and images
- **Amazon Comprehend Medical**: HIPAA-eligible NLP service that identifies PHI (names, dates, medical conditions, medications)
- **Minimal changes**: Integrate with existing Lambda function

### Why other options are incorrect:

- **A** - Transcribe is for audio-to-text, not PDF processing.

- **B** - Creating a new Lambda violates the minimal changes requirement.

- **D** - Custom PHI detection requires development and maintenance overhead.

## References

- https://aws.amazon.com/comprehend/medical/
- https://tutorialsdojo.com/amazon-comprehend/

## Domain

Design Secure Architectures
