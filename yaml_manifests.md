## Create Kubernetes YAML manifests by dry run

**Pod**

```bash
kubectl run <pod-name> --image=nginx:latest \
    --labels type=web \
    --dry-run=client -o yaml > mypod.yaml
```
**Pod Service**

```bash
kubectl expose pod <pod-name> \
    --port=80 \
    --name <mypod-service> \
    --type=NodePort \
    --dry-run=client -o yaml > mypod-service.yaml
```


**NodePort Service**

```bash
kubectl create service nodeport mypod \
    --tcp=80:80 \
    --node-port=30001 \
    --dry-run=client -o yaml > mypod-service.yaml
```

**Deployment**

```bash
kubectl create deployment <deployment-name> \
    --image=nginx:latest \
    --dry-run=client -o yaml > mydeployment.yaml
```

**Deployment Service**

Create a NodePort service YAML for deployment mydeployment with service port 8080

```bash
kubectl expose deployment mydeployment \
    --type=NodePort \
    --port=8080 \
    --name=mydeployment-service \
    --dry-run=client -o yaml > mydeployment-service.yaml
```

**Job**

Crate job named myjob with nginx image.

```bash
kubectl create job myjob \
    --image=nginx:latest \
    --dry-run=client -o yaml
```

**Cronjob**

Create a cronjob named mycronjob with nginx image and a corn schedule.

```bash
kubectl create cj mycronjob \
    --image=nginx:latest \
    --schedule="* * * * *" \
    --dry-run=client -o yaml
```
