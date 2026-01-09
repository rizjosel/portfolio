# Project Screenshots and Resources

The following screenshots provide visual evidence of the CI/CD platform in action, showcasing real-time pipeline execution, monitoring, and logging from the self-hosted Kubernetes environment.


## Application config repo Structure

```text
.
├── README.md
├── app
│   ├── Chart.yaml
│   ├── templates
│   │   ├── _helpers.tpl
│   │   ├── deployment.yaml
│   │   ├── hpa.yaml
│   │   ├── ingress.yaml
│   │   ├── namespace.yaml
│   │   └── service.yaml
│   └── values.yaml
├── logging
│   ├── elasticsearch
│   │   ├── deployment.yaml
│   │   └── service.yaml
│   ├── filebeat
│   │   ├── configmap.yaml
│   │   ├── daemonset.yaml
│   │   ├── namespace.yaml
│   │   └── rbac.yaml
│   └── kibana
│       ├── deployment.yaml
│       ├── ingress.yaml
│       └── service.yaml
├── monitoring
│   ├── grafana
│   │   ├── configmap.yaml
│   │   ├── deployment.yaml
│   │   ├── ingress.yaml
│   │   ├── namespace.yaml
│   │   └── service.yaml
│   └── prometheus
│       ├── configmap.yaml
│       ├── deployment.yaml
│       ├── ingress.yaml
│       ├── namespace.yaml
│       ├── node_exporter.yaml
│       ├── rbac.yaml
│       └── service.yaml
└── terraform
    └── argo
        ├── main.tf
        ├── modules
        │   ├── main.tf
        │   └── varriables.tf
        ├── providers.tf
        ├── terraform.tfstate
        └── terraform.tfstate.backup
```

## Projects

### Jenkins folder:
![image](images/jenkins-project-folder.png)

### Argo Applications (UI)
![image](images/argo%20application.png)

### Kubernetes pods:
![image](images/clusterpods.png)

### Prometheus
![image](images/prometheus.png)

### Grafana/Dashboards
![image](images/grafana.png)
![image](images/grafana%20dashboard.png)
![image](images/grafanadashboard.png)

### Kibana
![image](images/kibana-elasticsearch%20logs.png)
