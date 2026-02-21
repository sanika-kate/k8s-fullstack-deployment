Student Registration Application Deployment on AWS EKS

This project demonstrates the containerization and deployment of a full-stack Student Registration application on AWS using Amazon EKS and Amazon RDS (MariaDB).

The objective is to implement production-oriented DevOps practices including infrastructure provisioning, containerization, secure configuration management, ingress routing, and troubleshooting deployment issues.

Project Overview

The application consists of:

Frontend (Vite-based application)
Backend (Spring Boot REST API)
Database (Amazon RDS MariaDB)
Kubernetes cluster (Amazon EKS)
NGINX Ingress Controller for external access

The deployment emphasizes:

Containerization using Docker
Kubernetes workloads and services
Secure configuration using ConfigMaps and Secrets
Ingress-based routing
SSL-secured database connectivity
Resource management

Architecture

User → AWS Load Balancer (NGINX Ingress Controller) → Frontend Service → Backend Service → Amazon RDS (MariaDB)

Core Components

Amazon EKS Cluster
Amazon EC2 (cluster access and management)
Docker Hub (container registry)
Amazon RDS MariaDB
NGINX Ingress Controller

Technology Stack

AWS EKS
AWS EC2
AWS RDS (MariaDB)
Docker
Kubernetes
kubectl
eksctl
NGINX Ingress Controller
Spring Boot
Vite

Deployment Process

EKS Cluster Setup
Provisioned EKS cluster using eksctl
Configured IAM roles and permissions
Accessed cluster via EC2 instance
Installed AWS CLI, kubectl, and eksctl

RDS Database Setup

Created Amazon RDS MariaDB instance
Configured networking and security groups
Enabled secure transport (SSL required)
Created application database and tables

Containerization

Implemented multi-stage Docker builds for backend and frontend
Built and tagged Docker images
Pushed images to Docker Hub

Kubernetes Configuration

Created and configured:
backend-deployment.yaml
frontend-deployment.yaml
backend-service.yaml
frontend-service.yaml
configmap.yaml
secret.yaml
ingress.yaml

Configured:
Resource requests and limits
Environment variables
Secure credential management using Secrets
SSL-enabled database connectivity
Internal service communication using ClusterIP

Ingress Configuration

Installed NGINX Ingress Controller
Provisioned AWS Load Balancer
Configured routing to frontend service
Verified end-to-end external access

Security Implementation

Database credentials managed via Kubernetes Secrets
Removed hardcoded credentials from application configuration
Enforced SSL for RDS connectivity
Backend service not exposed publicly
Defined resource limits for workload stability

Challenges and Resolutions

ImagePullBackOff
Cause: Incorrect image name or tag in deployment manifest
Resolution: Corrected image reference and redeployed workload

CrashLoopBackOff – Database Connectivity
Cause:
RDS security group misconfiguration

Network connectivity issues
Resolution:
Updated inbound security group rules

Verified connectivity between EKS nodes and RDS
RDS SSL Enforcement Error
Cause: Database required secure transport while application connection was not configured for SSL
Resolution: Configured proper SSL parameters in the datasource connection string

Outcome

The application was successfully deployed on Amazon EKS with secure database connectivity, ingress-based external routing, and production-style Kubernetes configuration. This project demonstrates practical implementation of containerized application deployment in a cloud-native environment.

Application code 
The application source code used in this project was leveraged for deployment and infrastructure demonstration purposes.
This repository focuses primarily on containerization, Kubernetes architecture, AWS infrastructure provisioning, and production-level troubleshooting.