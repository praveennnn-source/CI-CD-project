
# CI/CD Pipeline Automation Using Jenkins, Docker & AWS EC2

## Project Overview

Designed and implemented a complete Continuous Integration and Continuous Deployment (CI/CD) pipeline using Jenkins, Docker, GitHub, and AWS EC2. The pipeline automatically builds, deploys, and updates a containerized web application whenever changes are pushed to the GitHub repository.

---

# Architecture

```text
                   Developer
                       │
                 git push (Git)
                       │
                       ▼
              GitHub Repository
                       │
                GitHub Webhook
                       │
                       ▼
              Jenkins Pipeline
        ┌──────────────────────────┐
        │ Clone Repository         │
        │ Build Docker Image       │
        │ Stop Existing Container  │
        │ Deploy New Container     │
        └──────────────────────────┘
                       │
                       ▼
                Docker Engine
                       │
                       ▼
            Containerized Web Application
                       │
                       ▼
            AWS EC2 (Amazon Linux 2023)
```

---

# Technologies Used

| Technology         | Purpose                      |
| ------------------ | ---------------------------- |
| AWS EC2            | Hosting Jenkins and Docker   |
| Jenkins            | CI/CD Automation             |
| Git                | Version Control              |
| GitHub             | Source Code Repository       |
| GitHub Webhooks    | Automatic Build Trigger      |
| Docker             | Application Containerization |
| Apache HTTP Server | Web Server                   |
| Linux              | Server Administration        |

---

# Project Workflow

### 1. Developer writes code

The developer updates the application locally using Visual Studio Code.

↓

### 2. Push to GitHub

```bash
git add .
git commit -m "Updated website"
git push origin main
```

↓

### 3. GitHub Webhook

GitHub immediately sends a webhook request to Jenkins.

```
http://<JENKINS_IP>:8080/github-webhook/
```

↓

### 4. Jenkins Pipeline Starts

Jenkins automatically executes the pipeline.

Pipeline stages include:

* Clone Repository
* Build Docker Image
* Stop Existing Container
* Remove Existing Container
* Deploy New Container

↓

### 5. Docker Deployment

Docker creates a new image and launches a new container.

↓

### 6. Updated Website

The latest version of the website is available on the EC2 instance.

---

# Jenkins Pipeline

```groovy
pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                url: 'https://github.com/praveennnn-source/CI-CD-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t fashion-store .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop fashion-store || true
                docker rm fashion-store || true
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh '''
                docker run -d \
                --name fashion-store \
                -p 80:80 \
                fashion-store
                '''
            }
        }
    }
}
```

---

# Docker Workflow

```text
Dockerfile
      │
docker build
      │
Docker Image
      │
docker run
      │
Docker Container
      │
Application Running
```

---

# AWS Infrastructure

* Amazon EC2 (Amazon Linux 2023)
* Security Group

  * Port 22 (SSH)
  * Port 80 (HTTP)
  * Port 8080 (Jenkins)
* Elastic IP / Public IP
* Docker Engine
* Jenkins Server

---

# Project Features

* Automated CI/CD Pipeline
* GitHub Webhook Integration
* Dockerized Web Application
* Zero Manual Deployment
* Jenkins Declarative Pipeline
* Automatic Container Replacement
* AWS EC2 Deployment
* Linux-based Automation

---

# Learning Outcomes

* Continuous Integration (CI)
* Continuous Deployment (CD)
* Jenkins Pipeline Automation
* Docker Image Creation
* Container Lifecycle Management
* GitHub Webhooks
* AWS EC2 Administration
* Linux Commands
* DevOps Workflow

---

# Resume Project Description

### CI/CD Pipeline Automation using Jenkins, Docker & AWS

* Built an end-to-end CI/CD pipeline using Jenkins, GitHub, Docker, and AWS EC2.
* Automated application deployment using GitHub Webhooks and Jenkins Declarative Pipelines.
* Containerized a web application with Docker and deployed it on an Amazon EC2 instance.
* Configured Jenkins to build Docker images, stop old containers, and deploy updated application versions automatically.
* Managed Linux server administration, Docker installation, and Jenkins configuration on Amazon Linux 2023.

**Technologies:** AWS EC2, Jenkins, Docker, Git, GitHub, GitHub Webhooks, Linux, Apache

---

# LinkedIn Post

🚀 **Completed My CI/CD Pipeline Project Using Jenkins, Docker & AWS!**

I'm excited to share that I successfully built an end-to-end CI/CD pipeline that automates the deployment of a containerized web application.

### What I implemented:

* ✅ GitHub as the source code repository
* ✅ Jenkins Declarative Pipeline for automation
* ✅ GitHub Webhooks to trigger builds automatically
* ✅ Docker for application containerization
* ✅ AWS EC2 (Amazon Linux 2023) for hosting Jenkins and Docker
* ✅ Automated deployment by replacing the running container with the latest version

### CI/CD Workflow

```
Developer
   ↓
GitHub
   ↓
Webhook
   ↓
Jenkins
   ↓
Build Docker Image
   ↓
Deploy Docker Container
   ↓
AWS EC2
```

This project helped me gain hands-on experience with CI/CD automation, Docker containerization, Jenkins Pipelines, GitHub integration, and AWS deployment.

Looking forward to building more advanced DevOps projects involving Terraform, Kubernetes, monitoring, and cloud automation.

#DevOps #AWS #Jenkins #Docker #GitHub #CICD #Linux #CloudComputing #Automation #OpenToWork


