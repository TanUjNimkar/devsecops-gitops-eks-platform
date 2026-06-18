# 🚀 DevSecOps GitOps EKS Platform

Production-grade DevSecOps + GitOps platform for deploying a three-tier MERN application on AWS EKS using Jenkins, SonarQube, OWASP Dependency Check, Trivy, ArgoCD, Prometheus, and Grafana.

---

# 📖 Project Overview

This project demonstrates a complete end-to-end DevSecOps workflow:

1. Developer pushes code to GitHub
2. Jenkins triggers CI pipeline
3. Security and quality scans are executed
4. Docker images are built and pushed
5. Kubernetes manifests are updated automatically
6. ArgoCD detects Git changes
7. Application is deployed to AWS EKS
8. Prometheus and Grafana monitor workloads

---

# 🏗️ Architecture

## DevSecOps Workflow

```text
Developer
    │
    ▼
 GitHub Repository
    │
    ▼
 Jenkins CI Pipeline
    │
    ├── Trivy Scan
    ├── OWASP Dependency Check
    ├── SonarQube Analysis
    │
    ▼
 Docker Build
    │
    ▼
 DockerHub
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
 AWS EKS
    │
    ▼
 Production Deployment
    │
    ▼
 Prometheus + Grafana
```

---

# 🛠️ Technology Stack

## Source Control

- GitHub

## CI/CD

- Jenkins
- ArgoCD

## Security

- OWASP Dependency Check
- Trivy
- SonarQube

## Containerization

- Docker

## Kubernetes

- AWS EKS
- kubectl
- eksctl

## Monitoring

- Prometheus
- Grafana

## Cache

- Redis

---

# ✨ Key Features

✅ DevSecOps Integrated CI/CD

✅ Automated Security Scanning

✅ SonarQube Quality Gates

✅ Docker Image Management

✅ GitOps Deployment Strategy

✅ ArgoCD Auto Sync

✅ Kubernetes Rolling Updates

✅ Zero Downtime Deployment

✅ Prometheus Monitoring

✅ Grafana Dashboards

✅ Email Notifications

✅ Secure Credential Management

---

# 📋 Prerequisites

## AWS EC2 Instances

### Jenkins Master

| Resource | Value |
|----------|--------|
| Instance Type | t2.large |
| CPU | 2 vCPU |
| RAM | 8 GB |
| Storage | 30 GB |

### Jenkins Worker

| Resource | Value |
|----------|--------|
| Instance Type | t2.large |
| CPU | 2 vCPU |
| RAM | 8 GB |
| Storage | 30 GB |

### Region

```text
us-west-1
```

---

# 🐳 Install Docker

```bash
sudo apt update

sudo apt install docker.io -y

sudo usermod -aG docker ubuntu

newgrp docker
```

---

# 🔧 Install Jenkins

```bash
sudo apt update -y

sudo apt install fontconfig openjdk-21-jre -y

sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key

echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
https://pkg.jenkins.io/debian-stable binary/ \
| sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt update -y

sudo apt install jenkins -y
```

Access Jenkins:

```text
http://<JENKINS_IP>:8080
```

---

# ☁️ Install AWS CLI

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" \
-o "awscliv2.zip"

sudo apt install unzip

unzip awscliv2.zip

sudo ./aws/install

aws configure
```

Verify:

```bash
aws sts get-caller-identity
```

---

# ☸️ Install kubectl

```bash
curl -LO \
"https://dl.k8s.io/release/$(curl -L -s \
https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

chmod +x kubectl

sudo mv kubectl /usr/local/bin/

kubectl version --client
```

---

# 🚀 Install eksctl

```bash
curl --silent --location \
"https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" \
| tar xz -C /tmp

sudo mv /tmp/eksctl /usr/local/bin

eksctl version
```

---

# ☸️ Create EKS Cluster

## Create Cluster

```bash
eksctl create cluster \
--name=wanderlust \
--region=us-west-1 \
--version=1.34 \
--without-nodegroup
```

## Associate OIDC

```bash
eksctl utils associate-iam-oidc-provider \
--region us-west-1 \
--cluster wanderlust \
--approve
```

## Create Node Group

```bash
eksctl create nodegroup \
--cluster=wanderlust \
--region=us-west-1 \
--name=wanderlust \
--node-type=t3.medium \
--nodes=2 \
--nodes-min=2 \
--nodes-max=3 \
--node-volume-size=30
```

---

# 👷 Jenkins Worker Setup

Install Java:

```bash
sudo apt update -y

sudo apt install fontconfig openjdk-17-jre -y
```

Install Docker:

```bash
sudo apt install docker.io -y

sudo usermod -aG docker ubuntu

newgrp docker
```

Generate SSH Keys:

```bash
ssh-keygen
```

Add Jenkins Worker as a Jenkins Agent using SSH credentials.

---

# 🔍 Install Trivy

```bash
sudo apt-get install wget apt-transport-https gnupg lsb-release -y

wget -qO - \
https://aquasecurity.github.io/trivy-repo/deb/public.key \
| sudo apt-key add -

echo deb https://aquasecurity.github.io/trivy-repo/deb \
$(lsb_release -sc) main \
| sudo tee -a /etc/apt/sources.list.d/trivy.list

sudo apt-get update -y

sudo apt-get install trivy -y
```

Filesystem Scan:

```bash
trivy fs .
```

Image Scan:

```bash
trivy image username/app:latest
```

---

# 🔎 SonarQube Setup

Run SonarQube Container:

```bash
docker run -itd \
--name SonarQube-Server \
-p 9000:9000 \
sonarqube:community
```

Access:

```text
http://<SERVER_IP>:9000
```

Create:

- Project
- User Token

Configure Jenkins SonarQube Integration.

---

# 🛡️ Jenkins Plugins

Install:

- OWASP Dependency Check
- SonarQube Scanner
- Docker
- Docker Pipeline
- Pipeline Stage View
- Email Extension

---

# 🔐 Security Pipeline

## Trivy Scan

```bash
trivy fs .
```

## OWASP Dependency Check

```text
Scans application dependencies for known vulnerabilities.
```

## SonarQube Analysis

```text
Checks:
- Bugs
- Vulnerabilities
- Security Hotspots
- Code Smells
- Maintainability
```

---

# 🔄 CI Pipeline

Stages:

```text
Checkout Code
    ↓
Trivy Scan
    ↓
OWASP Dependency Check
    ↓
SonarQube Analysis
    ↓
Build Docker Image
    ↓
Push Docker Image
    ↓
Update Kubernetes Manifests
    ↓
Push Changes to GitHub
```

---

# 🚀 Install ArgoCD

Create Namespace:

```bash
kubectl create namespace argocd
```

Install:

```bash
kubectl apply -n argocd \
-f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

Check Pods:

```bash
kubectl get pods -n argocd
```

Expose ArgoCD:

```bash
kubectl patch svc argocd-server \
-n argocd \
-p '{"spec":{"type":"NodePort"}}'
```

Get Password:

```bash
kubectl -n argocd get secret \
argocd-initial-admin-secret \
-o jsonpath="{.data.password}" \
| base64 -d
```

Login:

```text
Username: admin
Password: <generated-password>
```

---

# 🔄 CD Pipeline

GitOps Flow:

```text
Jenkins
   ↓
Update Manifest
   ↓
GitHub
   ↓
ArgoCD Detects Change
   ↓
Auto Sync
   ↓
AWS EKS Deployment
```

Deployment Strategy:

```text
Rolling Update
Zero Downtime
```

---

# 📧 Email Notifications

Enable Gmail App Password.

Configure Jenkins:

```text
Manage Jenkins
→ System
→ Extended Email Notification
```

SMTP:

```text
smtp.gmail.com

Port: 465

SSL: Enabled
```

---

# 📊 Monitoring Setup

## Install Helm

```bash
curl -fsSL -o get_helm.sh \
https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3

chmod 700 get_helm.sh

./get_helm.sh
```

---

## Add Repository

```bash
helm repo add prometheus-community \
https://prometheus-community.github.io/helm-charts

helm repo update
```

---

## Create Namespace

```bash
kubectl create namespace prometheus
```

---

## Install Monitoring Stack

```bash
helm install monitoring \
prometheus-community/kube-prometheus-stack \
-n prometheus
```

Verify:

```bash
kubectl get pods -n prometheus
```

---

# 📈 Grafana

Get Password:

```bash
kubectl get secret \
-n prometheus \
monitoring-grafana \
-o jsonpath="{.data.admin-password}" \
| base64 --decode
```

Default Username:

```text
admin
```

---

# 📊 Monitoring Capabilities

Prometheus Monitors:

- Nodes
- Pods
- Deployments
- Services
- Cluster Health

Grafana Dashboards:

- Kubernetes Cluster
- Node Metrics
- Application Metrics
- Resource Usage
- Workload Health

---

# 📁 Deployment Flow

```text
Developer
   ↓
GitHub
   ↓
Jenkins CI
   ↓
Security Scans
   ↓
Docker Build
   ↓
DockerHub
   ↓
Manifest Update
   ↓
GitHub
   ↓
ArgoCD
   ↓
AWS EKS
   ↓
Production
   ↓
Prometheus
   ↓
Grafana
```

---

# ✅ Project Outcomes

- Fully Automated CI/CD
- DevSecOps Best Practices
- GitOps Deployment Model
- AWS EKS Production Deployment
- Automated Security Validation
- Continuous Monitoring
- Scalable Kubernetes Infrastructure
- Zero Downtime Releases

---

# 🧹 Cleanup

Delete EKS Cluster:

```bash
eksctl delete cluster \
--name=wanderlust \
--region=us-west-1
```

---

# 📌 Author

DevSecOps GitOps EKS Platform

Built using:

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
