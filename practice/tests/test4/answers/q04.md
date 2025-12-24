# Question 4

## Topic
Design High-Performing Architectures

## Question
A company plans to migrate a NoSQL database to an EC2 instance. The database is configured to replicate the data automatically to keep multiple copies of data for redundancy. The Solutions Architect needs to launch an instance that has a high IOPS and sequential read/write access.

Which of the following options fulfills the requirement if I/O throughput is the highest priority?

## Options
A. Use Memory optimized instances with EBS volume.

B. Use Storage optimized instances with instance store volume.

C. Use Compute optimized instance with instance store volume.

D. Use General purpose instances with EBS volume.

## Correct Answer
B

## Explanation
Amazon EC2 provides a wide selection of instance types optimized to fit different use cases. Instance types comprise varying combinations of CPU, memory, storage, and networking capacity and give you the flexibility to choose the appropriate mix of resources for your applications. Each instance type includes one or more instance sizes, allowing you to scale your resources to the requirements of your target workload.

A storage optimized instance is designed for workloads that require high, sequential read and write access to very large data sets on local storage. They are optimized to deliver tens of thousands of low-latency, random I/O operations per second (IOPS) to applications. Some instance types can drive more I/O throughput than what you can provision for a single EBS volume. You can join multiple volumes together in a RAID 0 configuration to use the available bandwidth for these instances.

Based on the given scenario, the NoSQL database will be migrated to an EC2 instance. The suitable instance type for NoSQL database is I3 and I3en instances. Also, the primary data storage for I3 and I3en instances is non-volatile memory express (NVMe) SSD instance store volumes. Since the data is replicated automatically, there will be no problem using an instance store volume.

Hence, the correct answer is: Use Storage optimized instances with instance store volume.

References:

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/storage-optimized-instances.html

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html

Check out this Amazon EC2 Cheat Sheet:

https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/

**Why other options are incorrect:**

- The option that says: Use Compute optimized instances with instance store volume is incorrect because this type of instance is ideal for compute-bound applications that benefit from high-performance processors. It is not suitable for a NoSQL database.

- The option that says: Use General purpose instances with EBS volume is incorrect because this instance only provides a balance of computing, memory, and networking resources. Take note that the requirement in the scenario is high sequential read and write access. Therefore, you must use a storage optimized instance.

- The option that says: Use Memory optimized instances with EBS volume is incorrect. Although this type of instance is suitable for a NoSQL database, it is not designed for workloads that require high, sequential read and write access to very large data sets on local storage.

