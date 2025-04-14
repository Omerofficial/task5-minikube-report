# 🚀 Task 5: Kubernetes Cluster with Minikube

This project demonstrates the setup of a local Kubernetes cluster using **Minikube**, deploying a simple NGINX application, exposing it with a service, and scaling it—all locally on Windows 11 as part of a DevOps internship.

---

## 🧰 Tools Used

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Minikube](https://minikube.sigs.k8s.io/)
- [kubectl (Kubernetes CLI)](https://kubernetes.io/docs/tasks/tools/)
- Windows 11 Terminal / Git Bash

---

## 📁 Project Structure

```bash
task5-minikube-report/
├── deployment.yaml         # Kubernetes Deployment file for NGINX
├── service.yaml            # Kubernetes NodePort Service to expose the app
├── screenshots/            # (Optional) Folder to store verification screenshots
└── README.md               # This documentation


1. Install Prerequisites
Installed Docker Desktop

Installed Minikube and kubectl using Chocolatey:

choco install minikube kubernetes-cli -y


![chocolatey install image 1 task 5](https://github.com/user-attachments/assets/a6016a2e-890e-4f67-ab6f-e1e2f39b7c9a)
![task 5 image 2 installing minikube](https://github.com/user-attachments/assets/b757a634-fde0-443c-9804-0ff7dbe8c514)

![task 5 image 3 installed successfully](https://github.com/user-attachments/assets/43baca9b-ed44-4d57-9ccf-204fcbf6aebb)

2. Start Minikube

minikube start

![task 5 image 4 minikube start](https://github.com/user-attachments/assets/0b156735-9806-4148-9ba3-7a51fe7d7704)

 3. Create a Deployment
Created deployment.yaml to deploy an NGINX web server:


apiVersion: apps/v1
kind: Deployment
metadata:
  name: hello-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: hello
  template:
    metadata:
      labels:
        app: hello
    spec:
      containers:
      - name: hello-container
        image: nginx
        ports:
        - containerPort: 80

Applied it with:

kubectl apply -f deployment.yaml
![task 5 image 6 deployment yaml ](https://github.com/user-attachments/assets/de3069ec-b88b-4ac9-9410-406ff1bd708c)

4. Create and Apply a Service
Created service.yaml to expose the deployment via NodePort:

apiVersion: v1
kind: Service
metadata:
  name: hello-service
spec:
  type: NodePort
  selector:
    app: hello
  ports:
    - port: 80
      targetPort: 80
      nodePort: 30007

Applied it with:
kubectl apply -f service.yaml
![task 5 image 8 service yaml](https://github.com/user-attachments/assets/392af52f-a604-4716-93ab-8a7c7e93f2a3)

5. Verify and Access the App
Checked pods: kubectl get pods
![task 5 image 7 pods verify](https://github.com/user-attachments/assets/184f614e-f0cc-44cd-908a-48350dd17766)

Checked services: kubectl get svc
Accessed NGINX in the browser:

minikube service hello-service

This opened the NGINX default welcome page.
![task 5 image 9 kubectl scale verify nginx is live](https://github.com/user-attachments/assets/95ded69f-baf9-404f-9f97-ecb306092e02)

✅ Outcome
Built a working local Kubernetes cluster using Minikube

Deployed and scaled an NGINX app

Verified service exposure and pod management using kubectl


📦 Final Checklist
Here’s your final submission checklist for Task 5:

✅	Task
✅	Created Minikube cluster locally
✅	Deployed app using deployment.yaml
✅	Exposed app using service.yaml
✅	Verified with kubectl get pods and minikube service
✅	Scaled pods using kubectl scale
✅	Created and committed a complete README.md
✅	Pushed all files to GitHub repo
✅	Ready to submit the repo link
