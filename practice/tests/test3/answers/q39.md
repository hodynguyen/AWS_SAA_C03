# Question 39

## Topic
Design Cost-Optimized Architectures

## Question
A company is building an automation tool for generating custom reports on its AWS usage. The company must be able to programmatically access and forecast usage costs on specific services.

Which of the following would meet the requirements with the LEAST amount of operational overhead?

## Options
A. Utilize the downloadable AWS Cost Explorer report .csv files to access the cost-related data. Predict usage costs using AWS Budgets.

B. Configure AWS Budgets to send usage cost data to the company via Amazon SNS.

C. Generate AWS Budgets reports for usage cost data and deliver them via Amazon Simple Queue Service (SQS).

D. Use the AWS Cost Explorer API with pagination to programmatically retrieve the usage cost-related data.

## Correct Answer
D

## Explanation
The AWS Cost Explorer API lets you programmatically query your cost and usage data. You can query for aggregated data such as total monthly costs or total daily usage. You can also query for granular data.

By using the AWS Cost Explorer API, the company can programmatically access the usage cost-related data they need on specific services. The pagination feature allows for efficient retrieval of large datasets.

**Why other options are incorrect:**
- **Option A** is incorrect because manually downloading .csv files adds significant operational overhead.
- **Option B** is incorrect because AWS Budgets sends notifications on thresholds, not detailed cost data.
- **Option C** is incorrect because AWS Budgets reports don't provide detailed usage information.

## References
- https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html
- https://docs.aws.amazon.com/cost-management/latest/userguide/ce-api.html
- https://tutorialsdojo.com/aws-billing-and-cost-management/
