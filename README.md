# Doctor Office App

📌 **Note**: This project was developed as part of ENPM818R — to demonstrate skills in containerization, virtualization, cloud-native deployments, and DevOps practices using Docker, Kubernetes, and AWS EKS.

A cloud-native, microservices-based Doctor Appointment system designed to streamline scheduling between doctors and patients. Built with a React frontend, Node.js backend, and MongoDB database, the application is containerized using Docker and deployed on AWS EKS with full CI/CD support.

---

## 🧩 Project Structure

```
doctor-office-app-main/
│
├── doctor-office-frontend/      # React-based UI
├── doctor-office-backend/       # Node.js backend API
├── aws_infra/                   # EKS cluster setup YAML
├── .github/workflows/           # GitHub Actions CI/CD
├── docker-compose.yml           # Local dev orchestration
└── README.md                    # Project guide (this file)
```

---

## 🚀 Features

- Schedule and manage doctor appointments
- View and search patient records
- Responsive UI built with React
- RESTful APIs with Express and MongoDB
- Dockerized services for consistent deployment
- Kubernetes deployment with EKS
- GitHub Actions CI/CD pipeline

---

## 🛠️ Tech Stack

**Frontend**
- React.js
- Nginx (for static hosting)

**Backend**
- Node.js
- Express
- MongoDB

**Infrastructure**
- Docker & Docker Compose
- AWS EKS, ECR, EC2, ALB, ACM, Route 53
- Kubernetes (StatefulSets, Services, Ingress)
- CloudWatch (logging, monitoring)
- GitHub Actions for CI/CD

---

## ⚙️ Setup Instructions

### Prerequisites

- Docker + Docker Compose
- Node.js + npm
- AWS CLI + eksctl + kubectl
- Helm (for ALB Controller)

### Local Setup

```bash
# Clone the repo
git clone https://github.com/rgoel22/doctor-office-app.git
cd doctor-office-app

# Start using Docker Compose
docker-compose up --build
```

---

## ☁️ AWS EKS Deployment

### 1. Set Up Cluster
```bash
eksctl create cluster -f aws_infra/eks_cluster_setup.yaml
```

### 2. Install Add-ons
- ALB Controller (Helm)
- CloudWatch Agent
- Metrics Server (for HPA)

### 3. Push Docker Images to ECR
```bash
docker build -t frontend .
docker tag frontend <aws_account>.dkr.ecr.<region>.amazonaws.com/frontend
docker push <aws_account>.dkr.ecr.<region>.amazonaws.com/frontend
```

### 4. Deploy to EKS
```bash
kubectl apply -f k8s/
kubectl get ingress
```

> Note: Application is not currently hosted live.

---

## 🧠 Advanced Features

- ✅ Kubernetes Ingress with ALB
- ✅ SSL via AWS Certificate Manager
- ✅ DNS Routing via Route 53
- ✅ CloudWatch Observability & Container Insights
- ✅ Horizontal Pod Autoscaling (HPA)

---

## 🔁 CI/CD Pipeline

GitHub Actions automate the build and deployment:
- `check-prerequisites`: Tooling validation
- `build`: Docker build + push to ECR
- `deploy-eks-cluster`: Provision EKS via `eksctl`
- `prod-k8s-deploy`: Apply all manifests

Secrets are securely managed using GitHub Secrets.  
IAM Role: `CI_RUNNER_ROLE`

Workflow File:  
[deploy.yaml](https://github.com/rgoel22/doctor-office-app/blob/main/.github/workflows/deploy.yaml)

---

## 🤝 Contributors

- Rishabh Goel  
- Reuben Thomas  
- Jongho Lee  
- Praveen Kumar Masupatri  
- Ganesh P. More  
- Bhanu Teja Panguluri  
- Dhanushree Sidharamanagara Onkaramurthy  

---

## 📘 Full Report

This README is supplemented by a detailed deployment report which outlines the full infrastructure, application design, and DevOps practices.

📄 [Download Report (PDF)](./Report.pdf)

---
