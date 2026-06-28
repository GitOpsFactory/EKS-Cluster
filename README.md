
<img width="1858" height="656" alt="image" src="https://github.com/user-attachments/assets/5e805b49-b2ec-4e04-adc9-b3e84891fee1" />

# Project: Deploying an Nginx Application on Amazon EKS Using AWS Application Load Balancer

## Project Overview

This project demonstrates how to deploy a containerized application on Amazon Elastic Kubernetes Service (EKS) and expose it to the internet using the AWS Load Balancer Controller. The controller automatically provisions an AWS Application Load Balancer (ALB) based on a Kubernetes Ingress resource.

## Objective

* Deploy a sample Nginx application on Amazon EKS.
* Expose the application using an internet-facing ALB.
* Understand the complete traffic flow from the client to the Kubernetes Pods.
* Learn how AWS resources are automatically created and managed by the AWS Load Balancer Controller.

## AWS Services Used

* Amazon EKS
* Amazon EC2 (Worker Nodes)
* IAM
* Amazon VPC
* Application Load Balancer (ALB)
* Target Groups
* Security Groups
* AWS Load Balancer Controller
* Kubernetes Ingress
* Kubernetes Service (ClusterIP)

## Implementation Steps

1. Created an Amazon EKS cluster.
2. Created a managed node group.
3. Configured IAM user access using EKS Access Entries.
4. Installed the AWS Load Balancer Controller.
5. Deployed an Nginx application using a Kubernetes Deployment.
6. Created a ClusterIP Service to expose the Pods internally.
7. Created an Ingress resource with ALB annotations.
8. The AWS Load Balancer Controller automatically created:

   * Application Load Balancer
   * Listener
   * Target Group
   * Security Groups
   * TargetGroupBinding
9. Verified the ALB DNS name and successfully accessed the Nginx application from a web browser.

## Traffic Flow

```text
Client
   │
Application Load Balancer
   │
Target Group
   │
TargetGroupBinding
   │
ClusterIP Service
   │
Nginx Pods
```

## Key Learning

* Kubernetes Deployments manage application Pods.
* ClusterIP Services provide a stable internal endpoint and load balance traffic to Pods.
* Ingress defines HTTP/HTTPS routing rules.
* AWS Load Balancer Controller watches Ingress resources and automatically creates AWS load balancing resources.
* Using `target-type: ip`, the ALB forwards requests directly to Pod IP addresses.
* Security Groups protect both the ALB and the worker nodes.
* EKS Access Entries are required to grant Kubernetes administrative access to IAM users.

## Outcome

The Nginx application was successfully deployed on Amazon EKS and accessed through an automatically provisioned AWS Application Load Balancer. The project demonstrated the integration between Kubernetes networking and AWS networking services, along with automated load balancer provisioning using the AWS Load Balancer Controller.
# EKS-Cluster
