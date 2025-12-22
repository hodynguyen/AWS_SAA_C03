# Question 59

## Topic
Design High-Performing Architectures

## Question
A large telecommunications company needs to run analytics against all combined log files from the Application Load Balancer as part of the regulatory requirements.

Which AWS services can be used together to collect logs and then easily perform log analysis?

## Options
A. Amazon S3 for storing ELB log files and Amazon EMR for analyzing the log files.

B. Amazon DynamoDB for storing and EC2 for analyzing the logs.

C. Amazon EC2 with EBS volumes for storing and analyzing the log files.

D. Amazon S3 for storing the ELB log files and an EC2 instance for analyzing the log files using a custom-built application.

## Correct Answer
A

## Explanation
In this scenario, it is best to use a combination of Amazon S3 and Amazon EMR: Amazon S3 for storing ELB log files and Amazon EMR for analyzing the log files. Access logging in the ELB is stored in Amazon S3 which means that the following are valid options:
- Amazon S3 for storing the ELB log files and an EC2 instance for analyzing the log files using a custom-built application.
- Amazon S3 for storing ELB log files and Amazon EMR for analyzing the log files.

However, log analysis can be automatically provided by Amazon EMR, which is more economical than building a custom-built log analysis application and hosting it in EC2. Hence, the option that says: Amazon S3 for storing ELB log files and Amazon EMR for analyzing the log files is the best answer between the two.

Access logging is an optional feature of Elastic Load Balancing that is disabled by default. After you enable access logging for your load balancer, Elastic Load Balancing captures the logs and stores them in the Amazon S3 bucket that you specify as compressed files. You can disable access logging at any time.

Amazon EMR provides a managed Hadoop framework that makes it easy, fast, and cost-effective to process vast amounts of data across dynamically scalable Amazon EC2 instances. It securely and reliably handles a broad set of big data use cases, including log analysis, web indexing, data transformations (ETL), machine learning, financial analysis, scientific simulation, and bioinformatics. You can also run other popular distributed frameworks such as Apache Spark, HBase, Presto, and Flink in Amazon EMR, and interact with data in other AWS data stores such as Amazon S3 and Amazon DynamoDB.

The option that says: Amazon DynamoDB for storing and EC2 for analyzing the logs is incorrect because DynamoDB is a noSQL database solution of AWS. It would be inefficient to store logs in DynamoDB while using EC2 to analyze them.

The option that says: Amazon EC2 with EBS volumes for storing and analyzing the log files is incorrect because using EC2 with EBS would be costly, and EBS might not provide the most durable storage for your logs, unlike S3.

The option that says: Amazon S3 for storing the ELB log files and an EC2 instance for analyzing the log files using a custom-built application is incorrect because using EC2 to analyze logs would be inefficient and expensive since you will have to program the analyzer yourself.

## References
- https://aws.amazon.com/emr/
- https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-access-logs.html
- https://tutorialsdojo.com/amazon-emr/
- https://tutorialsdojo.com/aws-elastic-load-balancing-elb/
