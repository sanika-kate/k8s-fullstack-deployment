# 🚀 Student Registration Application Deployment on AWS EKS

This project demonstrates the containerization and deployment of a full-stack **Student Registration Application** on AWS using **Amazon EKS** and **Amazon RDS (MariaDB)**.

The objective is to implement production-oriented DevOps practices including infrastructure provisioning, containerization, secure configuration management, ingress routing, and troubleshooting deployment issues.

---

## 📌 Project Overview

The application consists of:

- **Frontend** – Vite-based application  
- **Backend** – Spring Boot REST API  
- **Database** – Amazon RDS (MariaDB)  
- **Kubernetes Cluster** – Amazon EKS  
- **Ingress** – NGINX Ingress Controller for external access  

---

## 🎯 Key Implementation Highlights

- Containerization using Docker  
- Kubernetes Deployments and Services  
- Secure configuration using ConfigMaps and Secrets  
- Ingress-based routing  
- SSL-secured database connectivity  
- Resource requests and limits for stability  
- Production-style troubleshooting  

---

## 🏗 Architecture

```
User
   ↓
AWS Load Balancer (NGINX Ingress Controller)
   ↓
Frontend Service (ClusterIP)
   ↓
Backend Service (ClusterIP)
   ↓
Amazon RDS (MariaDB with SSL)
```

---

## 🧩 Core Components

- Amazon EKS Cluster  
- Amazon EC2 (Cluster access & management)  
- Docker Hub (Container Registry)  
- Amazon RDS (MariaDB)  
- NGINX Ingress Controller  

---

## 🛠 Technology Stack

- AWS EKS  
- AWS EC2  
- AWS RDS (MariaDB)  
- Docker  
- Kubernetes  
- kubectl  
- eksctl  
- NGINX Ingress Controller  
- Spring Boot  
- Vite  

---

# ⚙ Deployment Process

---

## 1️⃣ EKS Cluster Setup

- Provisioned EKS cluster using `eksctl`
- Configured IAM roles and permissions
- Accessed cluster via EC2 instance
- Installed AWS CLI, kubectl, and eksctl
- Verified node group and cluster health

---

## 2️⃣ RDS Database Setup

- Created Amazon RDS MariaDB instance
- Configured VPC networking and security groups
- Enabled secure transport (SSL required)
- Created application database and required tables

---

## 3️⃣ Containerization

- Implemented multi-stage Docker builds
- Built and tagged backend and frontend images
- Pushed images to Docker Hub
- Verified image pull from Kubernetes nodes

---

## 4️⃣ Kubernetes Configuration

Created and configured the following manifests:

```
backend-deployment.yaml  
frontend-deployment.yaml  
backend-service.yaml  
frontend-service.yaml  
configmap.yaml  
secret.yaml  
ingress.yaml
```

Configured:

- Resource requests and limits
- Environment variables via ConfigMaps
- Secure credential management using Kubernetes Secrets
- SSL-enabled database connectivity
- Internal communication using ClusterIP services

---

## 🌐 Ingress Configuration

- Installed NGINX Ingress Controller
- Provisioned AWS Load Balancer
- Configured host/path routing to frontend service
- Verified end-to-end external access

Backend service remains internal (ClusterIP only).

---

# 🔐 Security Implementation

- Database credentials managed via Kubernetes Secrets
- Removed hardcoded credentials from application properties
- Enforced SSL for RDS connectivity
- Restricted RDS inbound traffic to EKS node security group
- Defined CPU and memory limits for workload stability
- Backend service not exposed publicly

---

# 🛠 Challenges and Resolutions

## ❌ ImagePullBackOff

**Cause:** Incorrect image name or tag in deployment manifest  
**Resolution:** Corrected image reference and redeployed workload  

---

## ❌ CrashLoopBackOff – Database Connectivity

**Cause:**
- RDS security group misconfiguration  
- Network connectivity issues  

**Resolution:**
- Updated inbound security group rules  
- Verified connectivity between EKS nodes and RDS  

---

## ❌ RDS SSL Enforcement Error

**Cause:**  
Database required secure transport while application connection was not configured for SSL  

**Resolution:**  
Configured proper SSL parameters in the datasource connection string  

---

# ✅ Outcome

The application was successfully deployed on **Amazon EKS** with:

- Secure database connectivity  
- Ingress-based external routing  
- Production-style Kubernetes configuration  
- Secure credential management  
- Resource optimization  

This project demonstrates practical implementation of containerized application deployment in a cloud-native environment.

---

# 📂 Application Code Note

The application source code used in this project was leveraged for deployment and infrastructure demonstration purposes.

This repository focuses primarily on:

- Containerization  
- Kubernetes architecture  
- AWS infrastructure provisioning  
- Production-level troubleshooting  
- Secure cloud-native deployment practices  

---

## 📌 Author

**Sanika Kate**  
DevOps | Cloud | Kubernetes | AWS  
Building production-grade cloud-native solutions 🚀
