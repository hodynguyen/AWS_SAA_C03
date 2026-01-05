# Question 34

Analyze call transcripts in S3 (JSON). Extract and visualize sentiments. Minimize overhead.

Which solution meets requirements?

## Options

A. Comprehend + OpenSearch + Grafana.

B. Comprehend + OpenSearch + OpenSearch Dashboard.

C. Textract + OpenSearch + Grafana.

D. SageMaker custom NLP + OpenSearch + OpenSearch Dashboard.

## Correct Answer

**B. Comprehend + OpenSearch + OpenSearch Dashboard.**

## Explanation

Sentiment analysis pipeline:
- **Comprehend**: ML for NLP, sentiment extraction
- **OpenSearch**: Index and search data
- **OpenSearch Dashboard**: Built-in visualization
- **Minimal overhead**: All managed services

### Why other options are incorrect:

- **A** - Grafana for time-series; Dashboard better for OpenSearch.

- **C** - Textract extracts text from images, not sentiment.

- **D** - Custom SageMaker model adds overhead.

## References

- https://aws.amazon.com/comprehend/
- https://tutorialsdojo.com/amazon-comprehend/

## Domain

Design High-Performing Architectures
