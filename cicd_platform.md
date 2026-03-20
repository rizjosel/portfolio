# CI/CD Platform on Kubernetes

## Quick Start

- Provision **4 Ubuntu virtual machines** on **VirtualBox** using a **Bridged Adapter**
- Initialize a **Kubernetes cluster with kubeadm**
- Install **Calico** as the CNI for pod networking
- Install **MetalLB** to enable `LoadBalancer` services in the on-prem cluster
- Set up **Jenkins** on a dedicated VM and expose it securely using **Ngrok**
- Configure **GitHub Webhooks** to trigger pipelines on **push and pull request** events
- Deploy **Argo CD** inside the Kubernetes cluster to manage **observability applications** (e.g., logging, monitoring)
- Use **Terraform** to manage **Argo CD Application resources** as reusable modules, with state stored in an **encrypted S3 backend**
- Deploy **FluxCD** to manage **application workloads**, continuously reconciling Helm releases and manifests from Git
- Install **Prometheus and Grafana** for cluster and application monitoring
- Deploy the **ELK Stack (Elasticsearch, Logstash/Filebeat, Kibana)** for centralized logging and observability

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
  - Run **SonarQube analysis** for code quality and security checks
  - Report build/test and code quality status back to GitHub
  - Build Docker images **after PR merge** into the main branch
  - Push images to the container registry (**Docker Hub**)

### 3. SonarQube (Code Quality & Compliance)
- Integrated into Jenkins CI pipelines
- Provides **static code analysis**, detects bugs, vulnerabilities, and code smells
- Ensures that only high-quality code is merged into main branches
- Dashboards provide team-wide visibility into code health

### 4. Argo CD (Continuous Deployment)
- Deployed inside the Kubernetes cluster
- GitOps-based deployment model
- Automatically syncs Kubernetes manifests from GitHub
- Ensures the cluster state continuously matches the desired state

### 5. Terraform (Argo CD Application Management)
- Terraform is used to **manage Argo CD Application resources**
- Argo CD applications are defined as **reusable Terraform modules**
- Responsibilities:
  - Create and update Argo CD Applications
  - Enforce consistent application configuration across environments
  - Avoid manual drift in Argo CD UI
- Terraform **does not deploy workloads directly**
  - Argo CD remains the single source of truth for Kubernetes state
- Terraform state is stored in an **encrypted S3 backend** for centralized, version-controlled, and reproducible infrastructure management

### 6. FluxCD (Application Workload Management)
- FluxCD is used to manage actual application workloads, such as the production website and backend services
- Continuously reconciles Helm releases and Kubernetes manifests from Git, ensuring that application deployments, configuration, and scaling behavior always match the declared state
- FluxCD operates at the application layer, while Argo CD is reserved for platform and observability stacks

---

## Kubernetes Deployment
- Applications deployed via Argo CD using:
  - Deployments
  - Services
  - ConfigMaps
  - Ingress
  - Persistent Volumes
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
