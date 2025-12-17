# Question 3

## Topic
Design High-Performing Architectures

## Question
A company deployed a high-performance computing (HPC) cluster that spans multiple Amazon EC2 instances across multiple Availability Zones and processes various wind simulation models. Currently, the Solutions Architect is experiencing a slowdown in their applications and upon further investigation, it was discovered that it was due to latency issues.

Which is the MOST suitable solution that the Solutions Architect should implement to provide low-latency network performance necessary for tightly-coupled node-to-node communication of the HPC cluster?

## Options
A. Set up a spread placement group across multiple Availability Zones in multiple AWS Regions.

B. Set up AWS Direct Connect connections across multiple Availability Zones for increased bandwidth throughput and more consistent network experience.

C. Use EC2 Dedicated Instances with elastic inference accelerator.

D. Set up a cluster placement group within a single Availability Zone in the same AWS Region.

## Correct Answer
D

## Explanation
When you launch a new EC2 instance, the EC2 service attempts to place the instance in such a way that all of your instances are spread out across underlying hardware to minimize correlated failures. You can use placement groups to influence the placement of a group of interdependent instances:

- **Cluster** – packs instances close together inside an Availability Zone. This strategy enables workloads to achieve the low-latency network performance necessary for tightly-coupled node-to-node communication that is typical of HPC applications.
- **Partition** – spreads your instances across logical partitions such that groups of instances in one partition do not share the underlying hardware with groups of instances in different partitions.
- **Spread** – strictly places a small group of instances across distinct underlying hardware to reduce correlated failures.

**Why other options are incorrect:**
- **Option A** is incorrect because you can only set up a placement group in a single AWS Region only.
- **Option B** is incorrect because Direct Connect is primarily used for hybrid architectures, not for low latency within your AWS network.
- **Option C** is incorrect because Dedicated Instances are not used for reducing latency.

## References
- http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html
- https://aws.amazon.com/hpc/
- https://tutorialsdojo.com/amazon-elastic-compute-cloud-amazon-ec2/
