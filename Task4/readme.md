# Rhombix Technologies – Task 4

## CI/CD Pipeline with Jenkins, Docker & Kubernetes

## 📌 Project Overview

This project demonstrates a complete CI/CD workflow for deploying a Python Flask application using **GitHub, Jenkins, Docker, Docker Registry, and Kubernetes**.

The project focuses on automating application building, testing, containerization, deployment, and rolling updates.

The application was successfully deployed and tested on a **local Kubernetes cluster using Docker Desktop Kubernetes**.

> **Note:** AWS cloud deployment was not completed because AWS account/payment verification could not be completed. The CI/CD, Docker, and Kubernetes implementation was successfully completed locally.

---

## 🛠️ Technologies Used

* Git & GitHub
* Jenkins
* Docker
* Docker Registry
* Kubernetes
* Docker Desktop Kubernetes
* Python
* Flask
* PowerShell

---

## 🔄 CI/CD Workflow

```text
GitHub Repository
       ↓
     Jenkins
       ↓
Docker Image Build
       ↓
Docker Image Test
       ↓
Local Docker Registry
       ↓
Kubernetes Deployment
       ↓
Kubernetes Service
       ↓
Running Application
```

---

## 📁 Project Structure

```text
Task4/
│
├── Dockerfile
├── app.py
├── requirements.txt
├── deployment.yaml
├── service.yaml
└── README.md
```

---

## 🐳 Docker Implementation

The Flask application was containerized using Docker.

### Build Docker Image

```bash
docker build -t rhombix-task4:latest .
```

A local Docker Registry was configured on:

```text
localhost:5001
```

The image was tagged and pushed to the registry:

```bash
docker tag rhombix-task4:latest localhost:5001/rhombix-task4:latest
docker push localhost:5001/rhombix-task4:latest
```

---

## 🔧 Jenkins CI/CD Pipeline

Jenkins was configured to automate the application workflow.

The pipeline performs the following stages:

1. Checkout source code from GitHub
2. Build Docker image
3. Test Docker image
4. Deploy Docker container
5. Complete the CI/CD pipeline

The Jenkins pipeline completed successfully with:

```text
CI/CD Pipeline completed successfully!
Finished: SUCCESS
```

---

## ☸️ Kubernetes Deployment

The application was deployed on Docker Desktop Kubernetes.

The deployment was configured with **2 replicas**.

Check deployment:

```bash
kubectl get deployment
```

Expected result:

```text
NAME            READY
rhombix-task4   2/2
```

Check pods:

```bash
kubectl get pods
```

Both application replicas successfully reached:

```text
1/1 Running
```

---

## 🌐 Kubernetes Service

A Kubernetes NodePort service was configured to expose the Flask application.

```text
Application Port: 5000
NodePort:         30500
```

Check the service:

```bash
kubectl get services
```

The service successfully connected to both application pods.

The endpoints were verified using:

```bash
kubectl get endpoints rhombix-task4-service
```

---

## 🚀 Application Verification

The application was successfully accessed using Kubernetes port forwarding:

```bash
kubectl port-forward service/rhombix-task4-service 5000:5000
```

The application was then opened in the browser:

```text
http://localhost:5000
```

Application response:

```text
Rhombix Technologies - CI/CD Pipeline is Working!
```

---

## 🔄 Rolling Update

A second version of the Docker image was created:

```text
localhost:5001/rhombix-task4:v2
```

### Build Version 2

```bash
docker build -t localhost:5001/rhombix-task4:v2 .
```

### Push Version 2

```bash
docker push localhost:5001/rhombix-task4:v2
```

### Update Kubernetes Deployment

```bash
kubectl set image deployment/rhombix-task4 rhombix-task4=localhost:5001/rhombix-task4:v2
```

### Verify Rollout

```bash
kubectl rollout status deployment/rhombix-task4
```

The rolling update completed successfully:

```text
deployment "rhombix-task4" successfully rolled out
```

---

## 🔄 Zero-Downtime Deployment

The Kubernetes deployment uses **2 replicas** to maintain application availability during updates.

During the rolling update, Kubernetes gradually replaces the old application pods with the new version while maintaining available replicas.

The deployment was successfully verified after the update:

```text
READY: 2/2
STATUS: Running
```

The service continued to have healthy application endpoints.

This demonstrates the basic concept of **rolling updates and zero-downtime deployment** using Kubernetes.

---

## 🧪 Final Verification

The following components were successfully tested:

| Component             | Status         |
| --------------------- | -------------- |
| GitHub Repository     | ✅ Completed    |
| Jenkins CI/CD         | ✅ Completed    |
| Docker Build          | ✅ Completed    |
| Docker Image Testing  | ✅ Completed    |
| Docker Registry       | ✅ Completed    |
| Kubernetes Cluster    | ✅ Completed    |
| Kubernetes Deployment | ✅ Completed    |
| Kubernetes Replicas   | ✅ 2/2 Running  |
| Kubernetes Service    | ✅ Completed    |
| Application Access    | ✅ Working      |
| Rolling Update        | ✅ Successful   |
| Zero-Downtime Concept | ✅ Demonstrated |
| AWS Cloud Deployment  | ⏳ Pending      |

---

## 📚 Learning Outcomes

This project provided practical experience with:

* CI/CD pipeline implementation
* Jenkins automation
* GitHub integration
* Docker containerization
* Docker image testing
* Docker Registry
* Kubernetes deployments
* Kubernetes services
* Replica management
* Rolling updates
* Application deployment
* Zero-downtime deployment concepts

---

## 👨‍💻 Author

**Ehtisham Javaid**

Computer Science Student
