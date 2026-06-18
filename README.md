# 🚀 DevSecOps + GitOps Platform on AWS EKS

A production-grade DevSecOps project demonstrating the deployment of a three-tier MERN application on Amazon EKS using Jenkins, SonarQube, OWASP Dependency Check, Trivy, Docker, ArgoCD, Prometheus, and Grafana.

---

# 📌 Project Deployment Flow

![DevSecOps GitOps Flow](Assets/DevSecOps+GitOps.gif)

---

# 🏗️ Architecture

![Architecture](Assets/architectures.png)

---

# 🔄 CI/CD Workflow

![CI-CD Workflow](Assets/flow.png)

---

# 🛠️ Tech Stack

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
- Redis

### Monitoring
- Prometheus
- Grafana

---

# ☁️ AWS Infrastructure

| Component | Configuration |
|------------|--------------|
| AWS Region | ap-south-1 (Mumbai) |
| Jenkins Master | t3.small |
| Jenkins Worker | t3.small |
| EKS Worker Nodes | t3.small |
| Storage | 30 GB |
| Kubernetes Platform | Amazon EKS |

---

# 🎯 Project Features

✅ End-to-End DevSecOps Pipeline

✅ GitOps Deployment with ArgoCD

✅ Automated Security Scanning

✅ SonarQube Quality Gates

✅ Dockerized Application Deployment

✅ AWS EKS Kubernetes Deployment

✅ Prometheus Monitoring

✅ Grafana Dashboards

✅ Email Notifications

✅ Zero Downtime Deployments

---

# 🔐 CI Pipeline (Jenkins)

### Stages

```text
Code Checkout
     ↓
OWASP Dependency Check
     ↓
SonarQube Analysis
     ↓
Trivy Filesystem Scan
     ↓
Docker Image Build
     ↓
Docker Image Push
     ↓
Trigger CD Pipeline
```

---

# 📸 Jenkins CI Pipeline

![Jenkins CI Pipeline](Assets/jenkins-ci-pipeline.png)

---

# 🔍 SonarQube Analysis

![SonarQube Analysis](Assets/Sonar.png)

---

# 🚀 CD Pipeline (GitOps)

### Stages

```text
Update Docker Image Version
          ↓
Push Updated Manifest
          ↓
GitHub Repository
          ↓
ArgoCD Detects Change
          ↓
Auto Sync
          ↓
AWS EKS Deployment
```

---

# 📸 ArgoCD Deployment

![ArgoCD Deployment](Assets/argocd-application.png)

---

# ☸️ Kubernetes Deployment

Application Components:

### Frontend
- React.js

### Backend
- Node.js
- Express.js

### Database
- MongoDB

### Cache Layer
- Redis

Deployment Strategy:

```text
Rolling Updates
Zero Downtime
GitOps Based Delivery
```

---

# 📊 Monitoring Stack

### Prometheus

Monitors:

- Kubernetes Cluster
- Nodes
- Pods
- Deployments
- Services

### Grafana

Visualizes:

- CPU Usage
- Memory Usage
- Cluster Health
- Pod Health
- Node Metrics

---

# 📸 Grafana Dashboard

![Grafana Dashboard](Assets/grafana-dashboard.png)

---

# 📸 Prometheus Dashboard

![Prometheus Dashboard](Assets/Prometheus.png)

---

# 📧 Email Notifications

Configured Jenkins Email Extension Plugin for:

- Build Success Alerts
- Build Failure Alerts
- Deployment Notifications
- Security Scan Notifications

---

# 🔄 End-to-End Workflow

```text
Developer
    │
    ▼
GitHub
    │
    ▼
Jenkins CI
    │
    ├── OWASP Dependency Check
    ├── SonarQube Analysis
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
Update Kubernetes Manifest
    │
    ▼
GitHub
    │
    ▼
ArgoCD Auto Sync
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
```

---

# 📸 Application Deployment

![Application Homepage](Assets/application-homepage.png)

---

# 📂 Repository Structure

```text
devsecops-gitops-eks-platform
│
├── Assets
│   ├── application-homepage.png
│   ├── architectures.png
│   ├── argocd-application.png
│   ├── DevSecOps+GitOps.gif
│   ├── flow.png
│   ├── grafana-dashboard.png
│   ├── jenkins-ci-pipeline.png
│   ├── Prometheus.png
│   └── Sonar.png
│
├── kubernetes
├── jenkins
├── monitoring
└── README.md
```

---

# 🏆 Key Learnings

- DevSecOps Implementation
- Jenkins CI/CD Pipelines
- SonarQube Integration
- Trivy Security Scanning
- OWASP Dependency Check
- Docker Containerization
- GitOps with ArgoCD
- AWS EKS Administration
- Kubernetes Deployments
- Prometheus Monitoring
- Grafana Visualization

---

# 👨‍💻 Author

### Tanuj Nimkar

DevOps Engineer | Cloud Enthusiast | Kubernetes Practitioner

### Built Using

- GitHub
- Jenkins
- Docker
- SonarQube
- Trivy
- OWASP Dependency Check
- ArgoCD
- AWS EKS
- Kubernetes
- Prometheus
- Grafana
- Redis

---

⭐ If you found this project useful, consider giving it a Star.