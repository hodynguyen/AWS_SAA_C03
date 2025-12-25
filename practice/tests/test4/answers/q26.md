# Question 26

## Topic
Design Resilient Architectures

## Question
A solutions architect is tasked with designing a scalable infrastructure solution for a business that runs uses Amazon Elastic Kubernetes Service (Amazon EKS) to execute container applications. Since the company's workload varies throughout the day, they want to make sure that its underlying infrastructure automatically scales in and out in response to demand.

Which of the following would meet the requirements with the LEAST amount of operational overhead?

## Options
A. Integrate an edge-optimized API endpoint in Amazon API Gateway with Amazon EKS to manage and expose APIs for the containerized applications running on EKS.

B. Set up CloudWatch alarms for CPU utilization or request count to monitor the relevant metrics of the container applications running on Amazon EKS.

C. Use Amazon EC2 Auto Scaling Groups with custom scaling policies to manage the scaling of EKS worker nodes.

D. Use a combination of Kubernetes Metrics and Kubernetes Cluster Autoscaler to manage the number of nodes.

## Correct Answer
D

## Explanation
Autoscaling is a function that automatically scales your resources up or down to meet changing demands. This is a major Kubernetes function that would otherwise require extensive human resources to perform manually.

Amazon EKS supports two autoscaling solutions:

Karpenter is a flexible, high-performance Kubernetes cluster autoscaler that launches appropriately sized compute resources, like Amazon EC2 instances, in response to changing application load. It integrates with AWS to provision compute resources that precisely match workload requirements.

Cluster Autoscaler, on the other hand, automatically adjusts the number of nodes in a cluster based on pod failures or rescheduling. It utilizes Auto Scaling groups for managing the cluster's node capacity.

The Kubernetes Horizontal Pod Autoscaler (HPA) automatically scales the number of Pods based on CPU utilization, allowing applications to scale in or out to meet demand. It is a standard API resource in Kubernetes that requires a metrics source like the Kubernetes metrics server to be installed on the Amazon EKS cluster. The HPA does not need additional deployment or installation on the cluster to start scaling applications.

Hence, the correct answer is: Use a combination of Kubernetes Metrics and Kubernetes Cluster Autoscaler to manage the number of nodes.

References:

https://docs.aws.amazon.com/eks/latest/userguide/autoscaling.html

https://docs.aws.amazon.com/eks/latest/userguide/horizontal-pod-autoscaler.html

Check out this Amazon EKS Cheat Sheet:

https://tutorialsdojo.com/amazon-elastic-kubernetes-service-eks/

**Why other options are incorrect:**

- The option that says: Integrate an edge-optimized API endpoint in Amazon API Gateway with Amazon EKS to manage and expose APIs for the containerized applications running on EKS is incorrect because the question specifically asks for a solution that enables automatic scaling in response to demand. An edge-optimized API endpoint in Amazon API Gateway is primarily used for geographically distributed clients wherein the API requests are routed to the nearest CloudFront Point of Presence (POP). It doesn't specifically address the need for scaling.

- The option that says: Use Amazon EC2 Auto Scaling Groups with custom scaling policies to manage the scaling of EKS worker nodes is incorrect. While Amazon EC2 Auto Scaling Groups can be used to manage EKS worker nodes, this approach requires more configuration and management of scaling policies. It does not offer the same level of seamless integration and automation as Kubernetes Cluster Autoscaler, which is more optimized for Kubernetes workloads.

- The option that says: Set up CloudWatch alarms for CPU utilization or request count to monitor the relevant metrics of the container applications running on Amazon EKS is incorrect. While Amazon CloudWatch alarms can monitor the metrics of the Amazon EKS cluster, this approach alone does not enable automatic scaling of the EKS cluster in response to demand.

