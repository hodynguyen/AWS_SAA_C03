# Question 37

## Topic
Design High-Performing Architectures

## Question
A Data Analyst in a financial company is tasked to provide insights on stock market trends to the company's clients. The company uses AWS Glue extract, transform, and load (ETL) jobs in daily report generation, which involves fetching data from an Amazon S3 bucket. The analyst discovered that old data from previous runs were being reprocessed, causing the jobs to take longer to complete.

Which solution would resolve the issue in the most operationally efficient way?

## Options
A. Create a Lambda function that removes any data already processed. Then, use Amazon EventBridge to trigger this function whenever the ETL job's status switches to SUCCEEDED.

B. Parallelize the job by splitting the dataset into smaller partitions and processing them simultaneously using multiple EC2 instances.

C. Increase the size of the dataset used in the job to speed up the extraction and analysis process.

D. Enable job bookmark for the ETL job.

## Correct Answer
D

## Explanation
Job bookmarking is a mechanism that allows AWS Glue to keep track of where a job left off. This way, when the job is restarted, it can pick up from where it left off instead of starting from scratch.

Enabling job bookmarking keeps track of the last processed data, allowing succeeding jobs to run only to process new data. This eliminates the need to reprocess old data.

**Why other options are incorrect:**
- **Option A** is incorrect because removing processed data adds complexity and may cause issues if jobs need rerunning.
- **Option B** is incorrect because parallelization speeds up processing but doesn't address reprocessing old data.
- **Option C** is incorrect because increasing dataset size would increase processing time, not reduce it.

## References
- https://docs.aws.amazon.com/glue/latest/dg/what-is-glue.html
- https://docs.aws.amazon.com/glue/latest/dg/monitor-continuations.html
- https://tutorialsdojo.com/aws-glue/
