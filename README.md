# 👋 Hi, I’m Riz

I’m a DevOps enthusiast with hands-on experience in CI/CD pipelines, GitOps workflows with Argo CD and FluxCD, and Kubernetes deployments. My portfolio demonstrates practical expertise in building and managing on-prem infrastructure, automating deployments, and implementing observability and monitoring solutions.

This platform runs on a self-hosted Kubernetes cluster provisioned across multiple Ubuntu VMs on VirtualBox using a Bridged Adapter. It emphasizes end-to-end DevOps skills, from infrastructure provisioning to application delivery.

## Key Projects & Skills

- **CI/CD & Automation:** Built pipelines with Jenkins, triggered via GitHub Webhooks, and securely exposed with Ngrok.
- **GitOps & Application Delivery:** Deployed and managed applications using Argo CD and FluxCD, leveraging Terraform modules for reusable Argo CD Application resources with encrypted S3 backend state.
- **Kubernetes Infrastructure:** Provisioned clusters using kubeadm on Ubuntu VMs, configured Calico CNI for networking, and MetalLB for LoadBalancer services.
- **Containerization & Orchestration:** Containerized applications using Docker and deployed them via Helm charts and Kubernetes manifests.
- **Observability & Monitoring:** Implemented Prometheus, Grafana, and the ELK Stack (Elasticsearch, Logstash/Filebeat, Kibana) for logging and metrics.
- **Quality & Compliance:** Integrated SonarQube for continuous code quality analysis and automated feedback.


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

## Architecture Summary

- **CI/CD Pipeline:** GitHub → Jenkins → SonarQube → Argo CD → Kubernetes
- **Infrastructure:** 4 Ubuntu VMs on VirtualBox (Windows Host)
- **Infrastructure as Code:** Terraform (Argo CD Application Management)
- **Container Orchestration:** Kubernetes
- **GitOps:** 
  - **Argo CD:** Monitors observability and monitoring applications (Prometheus, Grafana, ELK Stack)
  - **Flux CD:** Monitors application deployments
- **Logging:** Filebeat → Elasticsearch → Kibana
- **Monitoring:** Prometheus → Grafana
- **Code Quality & Compliance:** SonarQube for static code analysis and automated feedback

![image](images/architecture3.png)

---

## Project Documentation

- **CI/CD Platform Overview** → [cicd_platform.md](cicd_platform.md)  
- **CI/CD & Git Flow Details** → [cicd_gitflow.md](cicd_gitflow.md)  
- **Platform Screenshots** → [project_screenshots.md](project_screenshots.md)


## Other Projects
- eks - https://github.com/rizjosel/cicd-platform-aws 
- cdk - https://github.com/rizjosel/cdk-python
