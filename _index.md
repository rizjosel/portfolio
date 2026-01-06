# DevOps Portfolio – CI/CD Platform on Kubernetes

## Overview
Designed and implemented an end-to-end **CI/CD platform** to automate application build, deployment, monitoring, and logging.  
The platform runs on a **self-hosted Kubernetes cluster** provisioned on multiple Ubuntu VMs using VirtualBox on a Windows host. This project emphasizes **hands-on DevOps skills** and infrastructure management.

---

## Architecture Summary
- **CI/CD Pipeline:** GitHub → Jenkins → Argo CD → Kubernetes
- **Infrastructure:** 4 Ubuntu VMs on VirtualBox (Windows Host)
- **Container Orchestration:** Kubernetes
- **GitOps:** Argo CD
- **Logging:** Filebeat → Elasticsearch → Kibana
- **Monitoring:** Prometheus → Grafana

---

## Infrastructure Setup
- Host OS: **Windows**  
- Virtualization: **VirtualBox**  
- Virtual Machines:
  - 4 × Ubuntu Linux VMs  
- Kubernetes Cluster:
  - 1 Control Plane Node
  - 2 Worker Nodes  
- Networking configured using **Bridged Adapter** mode in VirtualBox to enable inter-VM and host-to-VM communication

---

## CI/CD Pipeline Implementation

### 1. Source Control
- GitHub hosts application and configuration repositories
- Webhooks trigger Jenkins builds on **push and Pull Request (PR) events**

### 2. Jenkins (Continuous Integration)
- Installed on a **dedicated VM**
- Pipelines implemented using **Jenkinsfile**
- Integrated with GitHub PRs for automated validation
- Responsibilities:
  - Checkout code from GitHub
  - Trigger builds on **PR creation or updates**
  - Run automated tests as part of **PR validation**
  - Report build/test status back to GitHub
  - Build Docker images **after PR merge** into the main branch
  - Push images to the container registry(Docker hub)

### 3. Argo CD (Continuous Deployment)
- GitOps-based deployment in Kubernetes
- Automatically syncs manifests from GitHub
- Ensures the cluster state matches the desired state

---

## Kubernetes Deployment
- Applications deployed using manifests with:
  - Deployments
  - Services
  - ConfigMaps
  - Ingress

---

## Logging & Observability

### ELK Stack
- **Filebeat:** Collects logs from pods and nodes (DaemonSet)  
- **Elasticsearch:** Stores and indexes logs  
- **Kibana:** Visualizes logs for troubleshooting and auditing

---

## Monitoring & Metrics

### Prometheus
- Collects **Kubernetes node-level metrics**

### Grafana
- Integrated with Prometheus for visualization
- Dashboards monitor:
  - CPU usage
  - Memory usage
  - Network traffic (sent/received)

---

## Networking
- Windows host runs **four Ubuntu VMs** via **VirtualBox Bridged Adapter**
- Kubernetes cluster networking:
  - **Calico**: pod-to-pod networking  
  - **MetalLB**: load balancing external traffic  
  - **Ingress**: exposes applications via HTTP/HTTPS
- **Ngrok** exposes Jenkins URL publicly, enabling GitHub webhooks to trigger builds securely

---

## Tools & Technologies
- **Version Control:** GitHub  
- **CI/CD:** Jenkins, Argo CD  
- **Containers & Orchestration:** Docker, Kubernetes  
- **Logging & Monitoring:** Filebeat, Elasticsearch, Kibana, Prometheus, Grafana  
- **OS & Infrastructure:** Ubuntu, VirtualBox, Windows

---

## 🚀 Ongoing Enhancements and Growth
- Extend Prometheus to monitor **pod-level metrics** using Custom Resources (CRs)  
- Deploy Jenkins **inside the Kubernetes cluster** for containerized CI  
- Migrate infrastructure to **cloud platforms (e.g., AWS)** for scalability and reliability  
- Add **Alerting and Notifications** with Prometheus Alertmanager  
- Secure the cluster with **RBAC and Network Policies**  
- Enhance Grafana dashboards for **application-level metrics and SLA monitoring**  
- Implement **Persistent Volumes** to retain data across pod restarts

---

## Why This Design
- Cost-effective, hands-on setup using local resources  
- Builds practical **Linux, Kubernetes, and DevOps skills**  
- Full ownership of infrastructure and deployments  
- Mirrors common **enterprise on-premise architectures**  
