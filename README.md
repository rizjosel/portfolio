# 👋 Hi, I’m Riz

I’m a **DevOps enthusiast** with hands-on experience in **CI/CD pipelines, GitOps workflows with Argo CD, and Kubernetes deployments**.  

This platform runs on a **self-hosted Kubernetes cluster** provisioned on multiple Ubuntu VMs using VirtualBox on a Windows host. This project emphasizes **hands-on DevOps skills** and infrastructure management.

In this portfolio, you’ll find projects where I’ve:

- Built **CI/CD pipelines using Jenkins**  
- Deployed applications with **Argo CD and GitOps principles**  
- Managed **Kubernetes clusters on Ubuntu VMs**  
- Containerized applications with **Docker**

---


## Repositories

**Application code repo:** Contains the actual application code) (Java Spring Boot
- https://github.com/rizjosel/spring-petclinic (forked form [spring projects](https://github.com/spring-projects/spring-petclinic))<br>

**Application config repo:** Stores Kubernetes manifests for deployment and environment configuration
- [https://github.com/rizjosel/petclinic-config](https://github.com/rizjosel/petclinic-config)

**Docker Registry:** Container registry for storing Docker images
- https://hub.docker.com/r/rizjosel/petclinic
---

## Tools & Technologies
- **Version Control:** GitHub  
- **Infrastructure as Code:** Terraform  
- **CI/CD & GitOps:** Jenkins, Argo CD  
- **Containers & Orchestration:** Docker, Kubernetes, Helm  
- **Networking:** Calico (CNI), MetalLB (Load Balancer), NGINX Ingress  
- **Logging & Monitoring:** Filebeat, Elasticsearch, Kibana, Prometheus, Grafana  
- **OS & Infrastructure:** Ubuntu, VirtualBox, Windows


---
## Quick Start

1. Provision **4 Ubuntu VMs** on VirtualBox using **Bridged Adapter**
2. Initialize a **Kubernetes cluster** with `kubeadm` (1 control plane, 2 workers)
3. Install **Calico** (CNI) and **MetalLB** (LoadBalancer)
4. Set up **Jenkins** on a dedicated VM and expose it via **Ngrok**
5. Configure **GitHub webhooks** for PR and push triggers
6. Deploy **Argo CD** for GitOps-based continuous deployment
7. Install **Prometheus & Grafana** for monitoring
8. Deploy **ELK stack** for centralized logging

## Quick Start

- Provision **4 Ubuntu virtual machines** on **VirtualBox** using a **Bridged Adapter**
- Initialize a **Kubernetes cluster with kubeadm**
- Install **Calico** as the CNI for pod networking
- Install **MetalLB** to enable `LoadBalancer` services in the on-prem cluster
- Set up **Jenkins** on a dedicated VM and expose it securely using **Ngrok**
- Configure **GitHub Webhooks** to trigger pipelines on **push and pull request** events
- Deploy **Argo CD** inside the Kubernetes cluster for **GitOps-based continuous deployment**
- Use **Terraform to manage Argo CD Applications**
- Install **Prometheus and Grafana** for cluster and application monitoring
- Deploy the **ELK Stack (Elasticsearch, Logstash/Filebeat, Kibana)** for centralized logging and observability


---

## Project Documentation

- **CI/CD Platform Overview** → [cicd_platform.md](cicd_platform.md)  
- **CI/CD & Git Flow Details** → [cicd_gitflow.md](cicd_gitflow.md)  
- **Platform Screenshots** → [project_screenshots.md](project_screenshots.md)
