# Question 35

A company wants to organize the way it tracks its spending on AWS resources. A report that summarizes the total billing accrued by each department must be generated at the end of the month.

Which solution will meet the requirements?

## Options

A. Tag resources with the department name and enable cost allocation tags.

B. Use AWS Cost Explorer to view spending and filter usage data by Resource.

C. Create a Cost and Usage report for AWS services that each department is using.

D. Tag resources with the department name and configure a budget action in AWS Budget.

## Correct Answer

**A. Tag resources with the department name and enable cost allocation tags.**

## Explanation

Cost allocation tags help you track your AWS costs on a detailed level. After you activate tags, AWS generates a cost allocation report as a CSV file with usage and costs grouped by your active tags.

### Why other options are incorrect:

- **D** - AWS Budgets is for alerts, not reports.

- **B** - Cost Explorer's Resource filter is limited.

- **C** - CUR reports by service, not department.

## References

- https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-alloc-tags.html
- https://tutorialsdojo.com/aws-billing-and-cost-management/

## Domain

Design Cost-Optimized Architectures
