# CI/CD Platform on Kubernetes

## Architecture Summary
- **CI/CD Pipeline:** GitHub → Jenkins → Argo CD → Kubernetes
- **Infrastructure:** 4 Ubuntu VMs on VirtualBox (Windows Host)
- **Infrastructure as Code:** Terraform (Argo CD Application Management)
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
  - Push images to the container registry (**Docker Hub**)

### 3. Argo CD (Continuous Deployment)
- Deployed inside the Kubernetes cluster
- GitOps-based deployment model
- Automatically syncs Kubernetes manifests from GitHub
- Ensures the cluster state continuously matches the desired state

### 4. Terraform (Argo CD Application Management)
- Terraform is used to **manage Argo CD Application resources**
- Argo CD applications are defined as **reusable Terraform modules**
- Responsibilities:
  - Create and update Argo CD Applications
  - Enforce consistent application configuration across environments
  - Avoid manual drift in Argo CD UI
- Terraform **does not deploy workloads directly**
  - Argo CD remains the single source of truth for Kubernetes state

---

## Kubernetes Deployment
- Applications deployed via Argo CD using:
  - Deployments
  - Services
  - ConfigMaps
  - Ingress
- Namespaces are isolated per application to avoid resource conflicts

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
  - **Calico:** pod-to-pod networking
  - **MetalLB:** load balancing external traffic
  - **Ingress:** exposes applications via HTTP/HTTPS
- **Ngrok** exposes Jenkins publicly, enabling GitHub webhooks to trigger builds securely

---

## 🚀 Ongoing Enhancements and Growth
- Extend Prometheus to monitor **pod-level metrics**
- Deploy Jenkins **inside the Kubernetes cluster**
- Migrate infrastructure to **cloud platforms (e.g., AWS)**
- Add **Alerting and Notifications** using Alertmanager
- Secure the cluster with **RBAC and Network Policies**
- Enhance Grafana dashboards for **application-level metrics**
- Implement **Persistent Volumes** for stateful workloads
- Introduce **multi-environment Argo CD applications** using Terraform modules

---

## Why This Design
- Cost-effective, hands-on on-prem Kubernetes setup
- Clear separation of responsibilities:
  - Terraform → Argo CD application lifecycle
  - Argo CD → Kubernetes state reconciliation
  - Jenkins → Continuous Integration
- Follows modern **enterprise GitOps patterns**
- Demonstrates real-world DevOps tooling integration
