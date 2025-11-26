Production-Grade EKS Automation with Jenkins and Terraform

This project demonstrates a full production-grade workflow for deploying and managing applications on Amazon EKS using Terraform for Infrastructure-as-Code and Jenkins for Continuous Integration and Delivery.
It follows real-world DevOps practices including automated cluster provisioning, containerization, CI/CD pipeline execution, and Kubernetes-based deployment.

1. Project Overview

This repository automates the complete lifecycle of a Kubernetes environment on AWS:

Provision EKS infrastructure using Terraform

Build and containerize the application using Docker

Push images to Amazon ECR

Deploy and update Kubernetes workloads using kubectl

Implement monitoring using Prometheus and Grafana

Automate all steps through a Jenkins pipeline

This workflow mirrors modern DevOps practices used in production systems.

2. Project Architecture

The solution includes:

Amazon EKS cluster

Elastic Container Registry (ECR) for image storage

Application deployment using Kubernetes manifests

Terraform modules for VPC, subnets, node groups, IAM roles

Jenkins pipeline for automated build, provision, and deploy

Prometheus and Grafana for monitoring and metrics

3. Repository Structure
├── terraform-eks-infra
│   ├── provider.tf
│   ├── eks.tf
│   ├── vpc.tf
│   ├── data.tf
│   ├── backend.tf
│   ├── variables.tf
│   └── variables/
│       ├── dev.tfvars
│       ├── prod.tfvars
│       └── test.tfvars
│
├── jenkins-config
│   └── scripts/
│       └── install_build_tools.sh
│
├── k8s-manifests
│   ├── deployment.yaml
│   └── service.yaml
│
├── monitoring
│   └── prometheus-config.yaml
│
├── CI-CD-pipeline.groovy
├── Dockerfile
├── changelog.txt
└── README.md

4. Features Implemented
Infrastructure (Terraform)

VPC provisioning

Public/private subnets

Internet gateway and route tables

EKS cluster creation

Node groups with scaling policies

IAM roles and permissions

Application Deployment

Docker container build

Kubernetes Deployment and Service

Namespace-based application isolation

CI/CD Pipeline (Jenkins)

Code checkout

Terraform init, plan, and apply

Docker image build and tagging

ECR authentication

Image push to ECR

Kubernetes deployment rollout

Monitoring

Prometheus configuration

Grafana-ready setup

5. Jenkins Pipeline Summary

The Jenkins pipeline automates:

Checking out source code

Provisioning or updating the EKS cluster using Terraform

Building and pushing Docker images to ECR

Applying Kubernetes manifests to deploy the application

Triggering automated rollouts for updated versions

All steps are defined in CI-CD-pipeline.groovy.

6. How to Use This Project
Prerequisites

AWS CLI configured

Terraform installed

kubectl installed

Docker installed

Jenkins (with required plugins)

IAM permissions for EKS and ECR operations

Steps

Update AWS values in variables.tf and *.tfvars

Run Terraform to create the cluster

Configure kubectl to connect to EKS

Build and push Docker images

Apply Kubernetes manifests

Trigger Jenkins pipeline to automate the entire process

7. Why This Project Is Important

This project demonstrates real-world DevOps capabilities:

Infrastructure-as-Code using Terraform

Kubernetes orchestration on Amazon EKS

Enterprise-grade CI/CD pipeline design

Cloud-native application deployment

Scalable and production-ready architecture

It represents the complete DevOps lifecycle from code to production.

