# Kubernetes Container Orchestration

## Objective

Deploy a simple web application on a local Kubernetes cluster using Docker Desktop Kubernetes. Learn how to manage Deployments, Pods, Services, and Scaling.

## Tools Used

* Kubernetes
* Docker Desktop
* kubectl
* Nginx

## Project Files

* deployment.yaml
* service.yaml

## Steps Performed

1. Enabled Kubernetes in Docker Desktop.
2. Verified the cluster using `kubectl cluster-info`.
3. Created an Nginx Deployment using `deployment.yaml`.
4. Verified the running Pod.
5. Created a NodePort Service using `service.yaml`.
6. Accessed the application in the browser.
7. Scaled the deployment from 1 replica to 3 replicas.
8. Verified all Pods were running successfully.

## Commands Used

* kubectl cluster-info
* kubectl get nodes
* kubectl apply -f deployment.yaml
* kubectl apply -f service.yaml
* kubectl get deployments
* kubectl get pods
* kubectl get services
* kubectl scale deployment nginx-deployment --replicas=3

## Result

Successfully deployed an Nginx application on Kubernetes, exposed it using a NodePort Service, verified browser access, and scaled the application from one Pod to three Pods.
