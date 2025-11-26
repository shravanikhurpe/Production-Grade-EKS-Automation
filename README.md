Production-Grade EKS Automation with Jenkins and Terraform

This repository demonstrates a production-ready workflow for provisioning Amazon EKS clusters, deploying containerized applications, and automating the CI/CD process using Jenkins and Terraform.

1. Overview

The project covers the complete DevOps pipeline:

Infrastructure provisioning with Terraform

Docker-based application containerization

Deployment to an Amazon EKS cluster

Image storage and versioning using Amazon ECR

Automated CI/CD workflow via Jenkins

Kubernetes manifests for application deployment

Monitoring setup using Prometheus and Grafana

2. Architecture Summary

This solution includes:

AWS VPC, subnets, routing, and networking resources

Elastic Kubernetes Service (EKS) cluster with node groups

IAM roles and permissions

Docker image build pipeline and ECR push

Kubernetes Deployment and Service configuration

Monitoring setup for cluster and application metrics

CI/CD pipeline written in Groovy

3. Repository Structure
.
├── terraform-eks-infra
│   ├── backend.tf
│   ├── data.tf
│   ├── eks.tf
│   ├── provider.tf
│   ├── vpc.tf
│   ├── variables.tf
│   └── variables
│       ├── dev.tfvars
│       ├── prod.tfvars
│       └── test.tfvars
│
├── jenkins-config
│   └── scripts
│       └── install_build_tools.sh
│
├── k8s-manifests
│   ├── deployment.yaml
│   └── service.yaml
│
├── monitoring
│   └── prometheus-config.yaml
│
├── Dockerfile
├── CI-CD-pipeline.groovy
├── changelog.txt
└── README.md

4. Features
Terraform Infrastructure

Automated creation of AWS VPC

Subnets, route tables, and IGW

EKS cluster provisioning

Node group configurations

IAM policies and roles

Application Deployment

Docker-based application build

Kubernetes Deployment and Service

Namespace-based isolation

Jenkins CI/CD Pipeline

Code checkout

Terraform init, plan, and apply

Docker build and tag

ECR authentication and push

kubectl apply for deployment rollouts

Monitoring

Prometheus rules and configurations

Grafana-compatible metrics export

5. Jenkins Pipeline Workflow

Clone repository

Initialize Terraform

Validate plan and apply infrastructure

Build and tag Docker image

Push image to Amazon ECR

Deploy/upgrade application on EKS

Apply Kubernetes manifests for services and rollouts

All logic is contained in:
CI-CD-pipeline.groovy

6. Prerequisites

Ensure the following are installed and configured:

AWS CLI

Terraform

kubectl

Docker

Jenkins with required plugins

IAM permissions for EKS, EC2, ECR, IAM

7. How to Run

Update Terraform variables inside variables.tf and .tfvars files

Run Terraform:

terraform init
terraform plan -var-file=variables/dev.tfvars
terraform apply -var-file=variables/dev.tfvars


Update kubeconfig:

aws eks update-kubeconfig --name <cluster-name>


Build and push Docker image:

docker build -t eks-app .
docker tag eks-app:latest <AWS_ACCOUNT_ID>.dkr.ecr.<region>.amazonaws.com/eks-app:latest
docker push <AWS_ACCOUNT_ID>.dkr.ecr.<region>.amazonaws.com/eks-app:latest


Deploy application:

kubectl apply -f k8s-manifests/deployment.yaml
kubectl apply -f k8s-manifests/service.yaml


Trigger Jenkins pipeline for automation



