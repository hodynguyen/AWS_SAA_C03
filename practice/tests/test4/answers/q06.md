# Question 6

## Topic
Design Secure Architectures

## Question
A startup is planning to set up and govern a secure, compliant, multi-account AWS environment in preparation for its upcoming projects. The IT Manager requires the solution to have a dashboard for continuous detection of policy non-conformance and non-compliant resources across the enterprise, as well as to comply with the AWS multi-account strategy best practices.

Which of the following offers the easiest way to fulfill this task?

## Options
A. Launch new AWS member accounts using the AWS CloudFormation StackSets. Use AWS Config to continuously track the configuration changes and set rules to monitor non-compliant resources. Set up a Multi-Account Multi-Region Data Aggregator to monitor compliance data for rules and accounts in an aggregated view

B. Use AWS Control Tower to launch a landing zone to automatically provision and configure new accounts through an Account Factory. Utilize the AWS Control Tower dashboard to monitor provisioned accounts across your enterprise. Set up preventive and detective guardrails for policy enforcement.

C. Use AWS Organizations to build a landing zone to automatically provision new AWS accounts. Utilize the AWS Personal Health Dashboard to see provisioned accounts across your enterprise. Enable preventive and detective guardrails enabled for policy enforcement.

D. Use AWS Service Catalog to launch new AWS member accounts. Configure AWS Service Catalog Launch Constraints to continuously track configuration changes and monitor non-compliant resources. Set up a Multi-Account Multi-Region Data Aggregator to monitor compliance data for rules and accounts in an aggregated view

## Correct Answer
B

## Explanation
AWS Control Tower offers a straightforward way to set up and govern an AWS multi-account environment, following prescriptive best practices. AWS Control Tower orchestrates the capabilities of several other AWS services, including AWS Organizations, AWS Service Catalog, and AWS Single Sign-On, to build a landing zone in less than an hour. It offers a dashboard to see provisioned accounts across your enterprise, guardrails enabled for policy enforcement, guardrails enabled for continuous detection of policy non-conformance, and non-compliant resources organized by accounts and OUs.

A guardrail is a high-level rule that provides ongoing governance for your overall AWS environment. It's expressed in plain language. Through guardrails, AWS Control Tower implements preventive or detective controls that help you govern your resources and monitor compliance across groups of AWS accounts.

A guardrail applies to an entire organizational unit (OU), and every AWS account within the OU is affected by the guardrail. Therefore, when users perform work in any AWS account in your landing zone, they're always subject to the guardrails that are governing their account's OU.

Hence, the correct answer in this scenario is: Use AWS Control Tower to launch a landing zone to automatically provision and configure new accounts through an Account Factory. Utilize the AWS Control Tower dashboard to monitor provisioned accounts across your enterprise. Set up preventive and detective guardrails for policy enforcement.

Use AWS Organizations to build a landing zone to automatically provision new AWS accounts. Utilize the AWS Personal Health Dashboard to see provisioned accounts across your enterprise. Enable preventive and detective guardrails enabled for policy enforcement is incorrect. The AWS Organizations service neither has the capability to build a landing zone nor a built-in dashboard for continuous detection of policy non-conformance and non-compliant resources across the enterprise. Moreover, the AWS Personal Health Dashboard simply provides alerts and remediation guidance when AWS is experiencing events that may impact your resources. This type of dashboard is not meant for monitoring the newly provisioned AWS accounts. The most suitable solution here is to use AWS Control Tower and its various features.

References:

https://docs.aws.amazon.com/controltower/latest/userguide/what-is-control-tower.html

https://docs.aws.amazon.com/controltower/latest/userguide/how-control-tower-works.html

https://docs.aws.amazon.com/controltower/latest/userguide/aws-multi-account-landing-zone.html#multi-account-guidance

Check out this AWS Control Tower Cheat Sheet:

https://tutorialsdojo.com/aws-control-tower/

**Why other options are incorrect:**

- The option that says: Launch new AWS member accounts using the AWS CloudFormation StackSets. Use AWS Config to continuously track the configuration changes and set rules to monitor non-compliant resources. Set up a Multi-Account Multi-Region Data Aggregator to monitor compliance data for rules and accounts in an aggregated view is incorrect. Although the solution might work to monitor non-compliant resources, this is not the easiest way to fulfill the multi-account requirement in the scenario. It still takes a lot of time to configure CloudFormation StackSets templates and set up AWS Config for all your AWS member accounts.

- The option that says: Use AWS Service Catalog to launch new AWS member accounts. Configure AWS Service Catalog Launch Constraints to continuously track configuration changes and monitor non-compliant resources. Set up a Multi-Account Multi-Region Data Aggregator to monitor compliance data for rules and accounts in an aggregated view is incorrect. AWS Service Catalog is not used to detect non-compliant resources and is only used to manage catalogs of IT services from virtual machine images, servers, software, databases, and other resources. This service is primarily used centrally to curate and share commonly deployed templates with their teams to achieve consistent governance and meet compliance requirements.

