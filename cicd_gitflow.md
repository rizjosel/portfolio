this is outdated
# CI/CD & GitOps Flow

## Code Flow
```
Developer → GitHub Pull Request → Jenkins CI → Merge PR - > Build Docker Image → Push to Docker Hub
```

User submits a PR
![image](images/sample-pr.png)

Trigger a Jenkins job(PR checks) via ngrok tunnel<br>
succesful webhook:
![image](images/gh-jenkins-webhook.png)

Triggered Jenkins job:
![image](images/pr-ci-checks.png)

Build Docker after merge:
![image](images/docker-build.png)

Uploaded image tag:
![image](images/docker-tag.png)


## Deployment Flow
```
GitOps Repository → Argo CD → Kubernetes Cluster → Application Exposure
```
Update image tag in application config repo:
![image](images/update_image_tag.png)

Argo CD sync:
![image](images/argocd-sync.png)

Kubernetes deployement:
![image](images/kubernetes-changed-tag.png)