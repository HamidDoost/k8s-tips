## K8S - Architecture components and commands

### Installing components

- Manual ( Download installer, extract it, and run it as a service)

- Kubeadm (does not install Kubeadm)


### ETCD

- Manual setup

```bash
wget -q --https-only \ "https://github.com/coreos/etcd/releases/download/v3.3.9/etcd-v3.3.9-linux-amd64.tar.gz"`
```
- Setup - Kubeadm

`kubectl get pods -n kube-system`

- Explore ETCD

`kubectl exec <etcd-master> –n kube-system etcdctl get / --prefix –keys-only`

### kube-api server

- Installing kube-api server

`wget https://storage.googleapis.com/kubernetes-release/release/v1.13.0/bin/linux/amd64/kube-apiserver`

- View api-server - kubeadm

`kubectl get pods -n kube-system`

- View api-server options - kubeadm

`cat /etc/kubernetes/manifests/kube-apiserver.yaml`

- View api-server options

`cat /etc/systemd/system/kube-apiserver.service`

`ps -aux | grep kube-apiserver`

### Kube-Schduler

- Installing Kube-Scheduler

`wget https://storage.googleapis.com/kubernetes-release/release/v1.13.0/bin/linux/amd64/kube-scheduler`

- View kube-scheduler options - kubeadm

`cat /etc/kubernetes/manifests/kube-scheduler.yaml`

- View kube-scheduler options

`ps -aux | grep kube-scheduler`

### Kubelet

- Installing Kubelet (always manual)

`wget https://storage.googleapis.com/kubernetes-release/release/v1.13.0/bin/linux/amd64/kubelet`

- View kubelet options

`ps -aux | grep kubelet`

### Kube-Proxy

- Installing kube-proxy

`wget https://storage.googleapis.com/kubernetes-release/release/v1.13.0/bin/linux/amd64/kube-proxy`

- View kube-proxy - kubeadm

`kubectl get pods -n kube-system`


