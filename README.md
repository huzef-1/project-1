CI/CD Pipeline on AWS using Terraform, EKS,
 Kubernetes, and ArgoCD
 Submitted by: Huzefa Makandar
 Project Objective
 This project implements a complete GitOps-based CI/CD pipeline using Terraform, AWS EKS,
 Kubernetes, ArgoCD, and GitHub. The goal is to fully automate infrastructure provisioning and
 application deployment.
 Architecture Overview
 Terraform provisions the AWS EKS cluster. Kubernetes runs the NGINX application. ArgoCD
 continuously syncs the application state from the GitHub repository following GitOps principles.
 Repository Structure
 project-1/
 terraform/
 provider.tf
 main.tf
 variables.tf
 outputs.tf
 manifests/
 nginx-deployment.yaml
 nginx-service.yaml
 argocd/
 application.yaml
 1. Provision AWS EKS using Terraform
 1 terraform init
 2 terraform validate
 3 terraform apply -auto-approve
 4 aws eks update-kubeconfig --region ap-south-1 --name assessment-eks-cluster
 5 kubectl get nodes
 2. Deploy NGINX Application
 The NGINX application is deployed using Kubernetes Deployment and Service manifests located
 inside the manifests folder.
3. ArgoCD Installation & GitOps Setup
 1 kubectl create namespace argocd
 2 kubectl apply -n argocd -f
 https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
 3 kubectl port-forward svc/argocd-server -n argocd 8081:443
 4 Access ArgoCD UI at: https://localhost:8081
 5 Login using admin and retrieved password
 4. Access NGINX Application
 The NGINX application is accessed using port-forwarding at http://localhost:8080 or through a
 LoadBalancer if configured.
 5. Project Deliverables
 1 Terraform Infrastructure Code
 2 Kubernetes NGINX Manifests
 3 ArgoCD Application YAML
 4 GitHub Repository
 5 NGINX Application Screenshot
 6 ArgoCD Synced & Healthy Screenshot
Conclusion
 This project successfully demonstrates a complete CI/CD pipeline implementation using Terraform,
 AWS EKS, Kubernetes, ArgoCD, and GitHub following GitOps methodology
