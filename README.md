# 🚀 DevSecOps + GitOps Platform on AWS EKS

A production-style DevSecOps project demonstrating the deployment of a three-tier MERN application on Amazon EKS using Jenkins, SonarQube, OWASP Dependency Check, Trivy, Docker, ArgoCD, Prometheus, and Grafana.

---

## 📌 Project Deployment Flow

<p align="center">
  <img src="./Assets/DevSecOps+GitOps.gif" alt="DevSecOps GitOps Flow" width="100%">
</p>

---

## 🏗️ Architecture Overview

This project implements a complete DevSecOps and GitOps workflow:

```text
Developer
   │
   ▼
GitHub Repository
   │
   ▼
Jenkins CI Pipeline
   │
   ├── OWASP Dependency Check
   ├── SonarQube Analysis
   ├── Trivy Security Scan
   │
   ▼
Docker Build & Push
   │
   ▼
DockerHub
   │
   ▼
Jenkins CD Pipeline
   │
   ▼
Update Kubernetes Manifests
   │
   ▼
GitHub
   │
   ▼
ArgoCD Auto Sync
   │
   ▼
AWS EKS Cluster
   │
   ▼
Kubernetes Deployment
   │
   ▼
Prometheus + Grafana
   │
   ▼
Email Notifications
```

---

## 🛠️ Technology Stack

### Source Control
- GitHub

### CI/CD
- Jenkins
- ArgoCD

### Containerization
- Docker

### Security
- OWASP Dependency Check
- SonarQube
- Trivy

### Kubernetes & Cloud
- AWS EKS
- Kubernetes
- kubectl
- eksctl
- Redis

### Monitoring
- Prometheus
- Grafana

### Notifications
- Gmail SMTP

---

## ☁️ AWS Infrastructure

| Component | Configuration |
|------------|---------------|
| AWS Region | ap-south-1 (Mumbai) |
| Jenkins Master | t3.small |
| Jenkins Worker | t3.small |
| EKS Worker Nodes | t3.small |
| Storage | 30 GB |
| Kubernetes | Amazon EKS |

---

## 🔄 CI Pipeline (Jenkins)

### Stages

✅ Code Checkout

✅ OWASP Dependency Check

✅ SonarQube Analysis

✅ Trivy Filesystem Scan

✅ Docker Image Build

✅ Docker Image Push

✅ Trigger CD Pipeline

### Security Checks

#### OWASP Dependency Check

- Detect vulnerable dependencies
- Generate security reports

#### SonarQube

- Code Quality Analysis
- Bug Detection
- Vulnerability Detection
- Security Hotspots
- Quality Gate Validation

#### Trivy

- Filesystem Scan
- Vulnerability Detection
- Secret Scanning
- Misconfiguration Detection

---

## 🚀 CD Pipeline (GitOps)

### Stages

✅ Update Docker Image Version

✅ Commit Changes to GitHub

✅ ArgoCD Detects Changes

✅ Automatic Sync

✅ Kubernetes Rolling Deployment

✅ Zero Downtime Release

---

## 🔐 DevSecOps Workflow

```text
GitHub
   │
   ▼
Jenkins CI
   │
   ├── OWASP Scan
   ├── SonarQube Scan
   ├── Trivy Scan
   │
   ▼
Docker Build
   │
   ▼
DockerHub
   │
   ▼
Jenkins CD
   │
   ▼
Update Manifest
   │
   ▼
GitHub
   │
   ▼
ArgoCD
   │
   ▼
AWS EKS
```

---

## ☸️ Kubernetes Deployment

Application Components:

### Frontend

- React
- NodePort Service

### Backend

- Node.js
- Express.js
- REST APIs

### Database

- MongoDB

### Cache

- Redis

---

## 📊 Monitoring Stack

### Prometheus

Collects:

- Node Metrics
- Pod Metrics
- Deployment Metrics
- Cluster Metrics

### Grafana

Visualizes:

- CPU Usage
- Memory Usage
- Pod Health
- Node Health
- Cluster Status

---

## 📧 Email Notifications

Automatic email notifications are sent for:

- Successful Build
- Failed Build
- Deployment Status
- Pipeline Completion

Configured using:

- Gmail SMTP
- Jenkins Email Extension Plugin

---

## 🔧 Tools Used

| Tool | Purpose |
|--------|---------|
| GitHub | Source Code Management |
| Jenkins | Continuous Integration |
| Docker | Containerization |
| OWASP | Dependency Security Scan |
| SonarQube | Code Quality Analysis |
| Trivy | Vulnerability Scanning |
| ArgoCD | GitOps Deployment |
| EKS | Kubernetes Platform |
| Redis | Caching Layer |
| Helm | Package Management |
| Prometheus | Monitoring |
| Grafana | Visualization |

---

## 🎯 Key Features

✅ Production-Style DevSecOps Pipeline

✅ Automated Security Validation

✅ GitOps Deployment Strategy

✅ Continuous Delivery with ArgoCD

✅ Kubernetes Rolling Updates

✅ Zero Downtime Deployment

✅ Monitoring and Observability

✅ Email Notifications

✅ Secure Credential Management

✅ Fully Automated End-to-End Flow

---

## 🌍 Deployment Environment

```yaml
Cloud Provider: AWS
Region: ap-south-1
Kubernetes: Amazon EKS
Master Instance: t3.small
Worker Instance: t3.small
Monitoring: Prometheus + Grafana
CI Tool: Jenkins
CD Tool: ArgoCD
Container Registry: DockerHub
```

---

## 📈 End-to-End Flow

```text
Developer
   │
   ▼
GitHub
   │
   ▼
Jenkins CI
   │
   ├── OWASP
   ├── SonarQube
   ├── Trivy
   │
   ▼
Docker Build
   │
   ▼
DockerHub
   │
   ▼
Jenkins CD
   │
   ▼
Update Kubernetes Manifests
   │
   ▼
GitHub
   │
   ▼
ArgoCD
   │
   ▼
Amazon EKS
   │
   ▼
Application Deployment
   │
   ▼
Prometheus
   │
   ▼
Grafana
   │
   ▼
Email Notification
```

---

## 👨‍💻 Author

### DevSecOps + GitOps Platform on AWS EKS

Built using:

- Jenkins
- Docker
- SonarQube
- Trivy
- OWASP Dependency Check
- ArgoCD
- Kubernetes
- AWS EKS
- Prometheus
- Grafana
- Redis

---
⭐ If you found this project useful, consider giving it a star.