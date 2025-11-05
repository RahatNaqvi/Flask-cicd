# 🚀 Flask CI/CD Pipeline using Jenkins, Docker & Kubernetes

[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)](https://github.com/RahatNaqvi/Flask-cicd/actions)
[![Docker Image](https://img.shields.io/badge/docker-ready-blue.svg)](https://hub.docker.com/)
[![Kubernetes](https://img.shields.io/badge/deploys-on%20Kubernetes-326ce5.svg?logo=kubernetes)](https://kubernetes.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 🧩 Overview
This project demonstrates a **complete End-to-End CI/CD pipeline** for a simple Flask application.  
The pipeline automates:
- **Code integration** via GitHub  
- **Continuous Integration** with Jenkins  
- **Containerization** using Docker  
- **Continuous Deployment** on a Kubernetes cluster  

It’s designed to reflect a real-world DevOps workflow integrating modern cloud-native tools.

---

## 🏗️ Tech Stack
| Component | Description |
|------------|-------------|
| **Flask** | Lightweight Python web framework |
| **GitHub** | Version control and source repository |
| **Jenkins** | Automates the CI/CD pipeline |
| **Docker** | Builds and runs the app in containers |
| **Kubernetes (Minikube / Cluster)** | Deploys and manages containerized apps |

---

## 🔄 CI/CD Workflow Diagram

```mermaid
flowchart LR
A[👨‍💻 Developer Pushes Code to GitHub] --> B[🧩 Jenkins Pulls Code via Webhook]
B --> C[🐳 Build Docker Image]
C --> D[📦 Push Image to DockerHub]
D --> E[☸️ Deploy Image to Kubernetes]
E --> F[✅ Application Live & Monitored]
````

---

## ⚙️ Pipeline Stages

### 1️⃣ **Build Stage**

* Jenkins pulls code from GitHub
* Python virtual environment setup
* Unit tests (if defined)
* Docker image is built from `Dockerfile`

### 2️⃣ **Test Stage**

* Run basic Flask application tests (future expansion point)

### 3️⃣ **Deploy Stage**

* Docker image is pushed to DockerHub
* Kubernetes deployment manifest (`deployment.yaml`) applies to the cluster
* The new version is automatically rolled out

---

## 🧠 How It Works

1. You push new code to the `main` branch.
2. Jenkins, via a GitHub Webhook, detects the change.
3. Jenkins builds and tests the app, then creates a Docker image.
4. The image is pushed to your DockerHub repository.
5. Jenkins triggers a rolling update deployment on Kubernetes.
6. The latest app version becomes live without downtime.

---

## 🗂️ Project Structure

```
flask-cicd/
│
├── app.py               # Main Flask app
├── requirements.txt     # Python dependencies
├── Dockerfile           # Docker image instructions
├── Jenkinsfile          # Jenkins pipeline script
├── deployment.yaml      # Kubernetes deployment config
├── service.yaml         # Kubernetes service config
└── README.md            # Documentation (this file)
```

---

## 🧰 Setup Instructions

### 🔹 Clone the repository

```bash
git clone https://github.com/RahatNaqvi/Flask-cicd.git
cd Flask-cicd
```

### 🔹 Create and activate virtual environment

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### 🔹 Run locally

```bash
python app.py
```

Access it at 👉 [http://127.0.0.1:5000/](http://127.0.0.1:5000/)

---

## 🚀 Jenkins Configuration

* Install Jenkins on your server or VM
* Install these plugins:

  * GitHub Integration
  * Docker
  * Kubernetes
  * Pipeline
* Add your GitHub repo as a Jenkins pipeline (Multibranch or Freestyle)
* Connect Docker and K8s credentials via Jenkins **Manage Credentials**
* Trigger the pipeline automatically using a **GitHub Webhook**

---

## 📦 Docker Commands

Build image manually (if needed):

```bash
docker build -t flask-cicd:latest .
```

Run container:

```bash
docker run -p 5000:5000 flask-cicd
```

---

## ☸️ Kubernetes Deployment

Apply the manifests:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

Check the service:

```bash
kubectl get svc
```

---


## 👤 Author

**Rahat Naqvi**
🌐 [GitHub Profile](https://github.com/RahatNaqvi)
💼 DevOps | Cloud | Automation Enthusiast

---

## 💬 Feedback

Got ideas or improvements?
Feel free to open an issue or a pull request!
