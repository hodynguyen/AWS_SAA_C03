# Question 34

## Topic
Design Secure Architectures

## Question
A food company bought 50 licenses of Windows Server to be used by the developers when launching Amazon EC2 instances to deploy and test applications. The developers are free to provision EC2 instances as long as there is a license available. The licenses are tied to the total CPU count of each virtual machine. The company wants to ensure that developers won’t be able to launch new instances once the licenses are exhausted. The company wants to receive notifications when all licenses are in use.

Which of the following options is the recommended solution to meet the company's requirements?

## Options
A. Upload the licenses on AWS Systems Manager Fleet Manager to be encrypted and distributed to Amazon EC2 instances. Attach an IAM role on the EC2 instances to request a license from the Fleet Manager. Set up an Amazon SNS to send notifications and alerts once all licenses are used

B. Define license configuration rules on AWS Certificate Manager to track and control license usage. Enable the option to “Enforce certificate limit” to prevent going over the number of allocated licenses. Add an Amazon SQS queue with ChangeVisibility Timeout configured to send notifications and alerts.

C. Define licensing rules on AWS License Manager to track and control license usage. Enable the option to “Enforce license limit” to prevent going over the number of allocated licenses. Add an Amazon SNS topic to send notifications and alerts.

D. Configure AWS Resource Access Manager (AWS RAM) to track and control the licenses used by AWS resources. Configure AWS RAM to provide available licenses for Amazon EC2 instances. Set up an Amazon SNS to send notifications and alerts once all licenses are used.

## Correct Answer
C

## Explanation
AWS License Manager is a service that makes it easier for you to manage your software licenses from software vendors (for example, Microsoft, SAP, Oracle, and IBM) centrally across AWS and your on-premises environments. This provides control and visibility into the usage of your licenses, enabling you to limit licensing overages and reduce the risk of non-compliance and misreporting.

As you build out your cloud infrastructure on AWS, you can save costs by using Bring Your Own License model (BYOL) opportunities. That is, you can re-purpose your existing license inventory for use with your cloud resources.

If you are responsible for managing licenses in your organization, you can use License Manager to set up licensing rules, attach them to your launches, and keep track of usage. The users in your organization can then add and remove license-consuming resources without additional work.

License Manager reduces the risk of licensing overages and penalties with inventory tracking that is tied directly into AWS services. License Manager's built-in dashboards provide ongoing visibility into license usage and assistance with vendor audits.

You can prevent license usage when the available licenses are exhausted by selecting the “Enforce license limit” option in license configuration. When this limit exceeds, the instance launch is blocked to control overages.

Therefore, the correct answer is: Define licensing rules on AWS License Manager to track and control license usage. Enable the option to “Enforce license limit” to prevent going over the number of allocated licenses. Add an Amazon SNS topic to send notifications and alerts. You can use AWS License Manager to set up licensing rules, attach them to your EC2 launches, and keep track of usage.

References:

https://docs.aws.amazon.com/license-manager/latest/userguide/license-manager.html

https://docs.aws.amazon.com/license-manager/latest/userguide/license-manager-overview.html

https://aws.amazon.com/blogs/mt/mechanisms-to-govern-license-usage-with-aws-license-manager/

Check out this AWS License Manager Cheat Sheet:

https://tutorialsdojo.com/aws-license-manager/

**Why other options are incorrect:**

- The option that says: Define license configuration rules on AWS Certificate Manager to track and control license usage. Enable the option to “Enforce certificate limit” to prevent going over the number of allocated licenses. Add an Amazon SQS queue with ChangeVisibility Timeout configured to send notifications and alerts is incorrect. AWS Certificate Manager is used to provision, manage and deploy SSL certificates, not software licenses. In addition, you should use Amazon SNS for notification and not an Amazon SQS queue.

- The option that says: Upload the licenses on AWS Systems Manager Fleet Manager to be encrypted and distributed to Amazon EC2 instances. Attach an IAM role on the EC2 instances to request a license from the Fleet Manager. Set up an Amazon SNS to send notifications and alerts once all licenses are used is incorrect. The Fleet Manager is just one of the many capabilities of the AWS Systems Manager that provides a unified user interface (UI) experience in remotely managing your nodes/EC2 instances running on AWS or on-premises. This service is not capable of managing the software licenses of your EC2 instances.

- The option that says: Configure AWS Resource Access Manager (AWS RAM) to track and control the licenses used by AWS resources. Configure AWS RAM to provide available licenses for Amazon EC2 instances. Set up an Amazon SNS to send notifications and alerts once all licenses are used is incorrect. AWS RAM is used securely share your resources across AWS accounts in your AWS organization and not for tracking or controlling software licenses.

