# Question 7

## Topic
Design Resilient Architectures

## Question
Every week, an e-commerce company announces a sales promotion, causing its application hosted on an Auto Scaling group to experience intermittent downtime. Because of long initialization times, the application only becomes operational minutes before a new EC2 instance turns into RUNNING state. A solutions architect must devise a solution that launches capacity in advance based on a forecasted load in order to scale faster.

Which solution meets the requirements with the least amount of effort?

## Options
A. Use Amazon SageMaker Clarify to analyze and predict the workload pattern of the application. Create a scheduled scaling policy based on the prediction results.

B. Create a dynamic scaling policy based on the historical average CPU load of the application.

C. Configure the Auto Scaling group to use predictive scaling.

D. Create a Scheduled Amazon EventBridge (Amazon CloudWatch Events) Rule that runs a scaling job on a Lambda function every midnight.

## Correct Answer
C

## Explanation
Predictive scaling uses machine learning to predict capacity requirements based on historical data from CloudWatch. The machine learning algorithm consumes the available historical data and calculates capacity that best fits the historical load pattern, and then continuously learns based on new data to make future forecasts more accurate.

In general, if you have regular patterns of traffic increases and applications that take a long time to initialize, you should consider using predictive scaling. Predictive scaling can help you scale faster by launching capacity in advance of forecasted load, compared to using only dynamic scaling, which is reactive in nature. Predictive scaling can also potentially save you money on your EC2 bill by helping you avoid the need to overprovision capacity. You also don't have to spend time reviewing your application's load patterns and trying to schedule the right amount of capacity using scheduled scaling.

Hence, the correct answer is: Configure the Auto Scaling group to use predictive scaling.

References:

https://docs.aws.amazon.com/autoscaling/plans/userguide/how-it-works.html

https://aws.amazon.com/blogs/aws/new-predictive-scaling-for-ec2-powered-by-machine-learning/

Check out this AWS Auto Scaling Group Cheat Sheet:

https://tutorialsdojo.com/aws-auto-scaling/

**Why other options are incorrect:**

- The option that says: Use Amazon SageMaker Clarify to analyze and predict the workload pattern of the application. Create a scheduled scaling policy based on the prediction results is incorrect because SageMaker Clarify is a tool designed for detecting bias and providing explainability for machine learning models. Using SageMaker Clarify would only involve unnecessary complexity and does not directly solve the problem of predicting traffic for Auto Scaling.

- The option that says: Create a dynamic scaling policy based on the historical average CPU load of the applicationis incorrect. This solution alone is primarily useful if you want to adjust capacity when certain CPU thresholds are met. It won't be able to react to forecasted load patterns.

- The option that says: Create a Scheduled Amazon EventBridge (Amazon CloudWatch Events) Rule that runs a scaling job on a Lambda function every midnight is incorrect. This solution takes more effort to implement and is subjected to rescheduling since the schedule for a sales promotion can change.

