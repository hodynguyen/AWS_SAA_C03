# Question 63

## Topic
Design High-Performing Architectures

## Question
A call center wants to use Artificial Intelligence(AI) to extract insights from audio recordings to assess the quality of its customer service. The calls are available in both English and Hindi. A sentiment analysis report in English must be generated for each recording to assess whether or not the customer had a positive experience. Once the solution is completed, new languages will eventually be supported, such as Arabic, Mandarin, and Spanish.

How can the solutions architect build the solution without maintaining any machine learning model?

## Options
A. Set up Amazon Comprehend to convert audio recordings into text. Use Amazon Kendra to translate Hindi texts into English and utilize the Amazon Detective service to automatically detect negative user behaviors for sentiment analysis.

B. Convert audio recordings into text using Amazon Transcribe. Set up Amazon Translate to translate Hindi texts into English and use Amazon Comprehend for sentiment analysis.

C. Utilize the Amazon Lex service to convert audio recordings into text. Call the Amazon Translate API to translate Hindi texts into English and use Amazon SageMaker Clarify for sentiment prediction and analysis.

D. Transcribe audio recordings into text using Amazon Polly's StartSpeechSynthesisTask operation. Set up Amazon Rekognition to recognize and automatically translate Hindi texts into English. Use the combination of Amazon Fraud Detector and Amazon SageMaker BlazingText algorithm for sentiment analysis.

## Correct Answer
B

## Explanation
Amazon Transcribe is an AWS service that makes it easy for customers to convert speech-to-text. Using Automatic Speech Recognition (ASR) technology, customers can choose to use Amazon Transcribe for a variety of business applications, including transcription of voice-based customer service calls, generation of subtitles on audio/video content, and conduct (text-based) content analysis on audio/video content.

Amazon Translate is a Neural Machine Translation (MT) service for translating text between supported languages.

Amazon Comprehend is a natural language processing (NLP) service that uses machine learning to find meaning and insights in text.

You can use Amazon Comprehend to determine the sentiment of a document. For example, you can use sentiment analysis to determine the sentiments of comments on a blog posting or a transcribed call to determine if your users loved or hated your content. You can determine sentiment for documents in any of the primary languages supported by Amazon Comprehend. All documents in one job must be in the same language.

In this scenario, you can use these three services to build the ML-pipeline needed to satisfy the requirements. First, you'd have to create a transcription job using Amazon Transcribe to transform the recordings into text. Then, translate non-English calls to English using Amazon Translate. Finally, use Amazon Comprehend for sentiment analysis.

There's no need to deploy or train your own model as all of these services are fully managed and are readily available through APIs.

Hence, the correct answer is: Convert audio recordings into text using Amazon Transcribe. Set up Amazon Translate to translate Hindi texts into English and use Amazon Comprehend for sentiment analysis.

The option that says: Transcribe audio recordings into text using Amazon Polly's StartSpeechSynthesisTask operation. Set up Amazon Rekognition to recognize and automatically translate Hindi texts into English. Use the combination of Amazon Fraud Detector and Amazon SageMaker BlazingText algorithm for sentiment analysis is incorrect. Although the use of the Amazon SageMaker BlazingText algorithm is technically valid, it still fails to meet the condition of not maintaining any ML-model. Using Amazon SageMaker would require you to train and deploy the model yourself. Added to that, the use of Amazon Fraud Detector is also unnecessary. Amazon Fraud Detector is commonly used to identify potentially fraudulent activities and not for running sentiment analysis. Do take note that Amazon Polly is not capable of transcribing audio recordings, and Amazon Rekognition is primarily used for image recognition service, not for translating foreign words into English.

The option that says: Utilize the Amazon Lex service to convert audio recordings into text. Call the Amazon Translate API to translate Hindi texts into English and use Amazon SageMaker Clarify for sentiment prediction and analysis is incorrect. Amazon Lex is a fully managed artificial intelligence (AI) service with advanced natural language models that can help you design, build, test, and deploy conversational interfaces or chatbots. This service is not capable of transcribing any audio recordings into a text format. Amazon Textract only extracts text from documents and does not convert audio to text. Also, you cannot use the Amazon SageMaker Clarify service for running sentiment prediction and analysis. Amazon SageMaker Clarify is meant for forecasting business outcomes using historical and related data.

The option that says: Set up Amazon Comprehend to convert audio recordings into text. Use Amazon Kendra to translate Hindi texts into English and utilize the Amazon Detective service to automatically detect negative user behaviors for sentiment analysis is incorrect. Amazon Comprehend is a natural-language processing (NLP) service that uses machine learning to uncover valuable insights and connections in text. This service is not capable of transcribing or converting audio recordings into text. Amazon Kendra is a highly accurate and easy-to-use enterprise search service for all unstructured data that you store in AWS, while Amazon Detective is a security service that analyzes and visualizes security data to rapidly get to the root cause of your potential security issues. Amazon Kendra is not capable of translating any foreign text into English, and Amazon Detective doesn't have the functionality to automatically detect negative user behaviors for sentiment analysis.

## References
- https://aws.amazon.com/transcribe/faqs/
- https://aws.amazon.com/translate/faqs/
- https://aws.amazon.com/comprehend/faqs/
- https://tutorialsdojo.com/amazon-transcribe/
- https://tutorialsdojo.com/amazon-translate/
