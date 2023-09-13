To get shorthand names `k api-resources`

**Cluster Information:**
  - `kubectl cluster-info`: Displays information about the Kubernetes cluster.

**Cluster Configuration:**
  - `kubectl config view`: View your current Kubernetes configuration.
  - `kubectl config use-context <context-name>`: Switch between different Kubernetes clusters or contexts.
  - `kubectl config set-context <context-name> --cluster=<cluster-name> --user=<user-name> --namespace=<namespace>`: Create or modify a context.

**Managing Resources:**
  - `kubectl create -f <yaml-file>`: Create a resource from a YAML file.
  - `kubectl apply -f <yaml-file>`: Create or update a resource from a YAML file.
  - `kubectl get <resource-type>`: List resources of a particular type.
  - `kubectl describe <resource-type> <resource-name>`: Show detailed information about a specific resource.
  - `kubectl delete <resource-type> <resource-name>`: Delete a resource.

---
### Kubernetes Resources
---
**Pods:** (`po`)
  - `kubectl get pods`: List all pods in the current namespace.
  - `k get po -o wide` : List all pods with node and ip address
  - `kubectl describe pod <pod-name>`: Show detailed information about a specific pod.
  - `kubectl get pod <pod-name> -o yaml > my-new-pod.yaml` : extract the pod definition for a running pod in YAML format to a file
  - `kubectl logs <pod-name>`: View logs of a specific pod.
  - `kubectl exec -it <pod-name> -- <command>`: Execute a command in a running pod.
  - `kubectl run <pod-name> --image=<image-name>` : Create a pod imperatively
  - `kubectl create -f <pod-definition.yaml>`: Create a pod declarativly.

**Replicasets:** (`rs`)
  - `kubectl create -f <replicaset-definiton.yaml>`: Create a replicaset from manifest.
  - `kubectl replace -f <replicaset-definition.yml>`: Update number of replicas in replicaset
  - `kubectl scale –replicas=5 -f <replicaset-definition.yml>`: Update number of replicas in replicaset
  - `kubectl delete replicaset <myapp-replicaset>`: Deletes replicaset and also all underlying pods
  `kubectl edit replicaset <replicaset-name>`: Edit replicaset

**Deployments:** (`deploy`)
  - `kubectl create deployment --image=nginx nginx` : Create a deployment
  - `kubectl create deployment --image=nginx nginx --dry-run=client -o yaml` : Generate Deployment YAML file (-o yaml)
  - `kubectl create deployment --image=nginx nginx --replicas=4 --dry-run=client -o yaml > nginx-deployment.yaml` : Generate a deployment yaml file with replicas
  - `kubectl get deployments`: List all deployments in the current namespace.
  - `kubectl rollout status deployment <deployment-name>`: Check the status of a deployment.
  - `kubectl rollout history deployment <deployment-name>`: View the rollout history of a deployment.
  - `kubectl rollout undo deployment <deployment-name>`: Rollback a deployment to a previous revision.

**Services:** (`svc`)
  - `kubectl get services`: List all services in the current namespace.
  - `kubectl expose deployment <deployment-name> --port=<port> --target-port=<target-port> --type=<service-type>`: Create a service for a deployment.
  - `kubectl expose pod <pod-name> --port=6379 --name <service-name> --dry-run=client -o yaml` : This will automatically use the pod's labels as selectors




**ConfigMaps and Secrets:**
  - `kubectl create configmap <configmap-name> --from-file=<file-path>`: Create a ConfigMap from a file.
  - `kubectl create secret generic <secret-name> --from-literal=<key>=<value>`: Create a secret.

**Scaling:**
  - `kubectl scale deployment <deployment-name> --replicas=<desired-replicas>`: Scale a deployment up or down.

**Namespace:**
  - `kubectl get namespaces`: List all namespaces.
  - `kubectl create namespace <namespace-name>`: Create a new namespace.
  - `kubectl config set-context --current --namespace=<namespace-name>`: Change the default namespace.


**Labels and Selectors**

- `k get po --selector env=dev` : Get pods with env lable equal to dev
- `k get all --selector env=prod`: Get all k resources including po, rs, svc, .. in prod env
- `kubectl get all --selector env=prod,bu=finance,tier=frontend`: get all objects common in all specified lables
- `kubectl get nodes --show-labels`: list the nodes and labels
- `kubectl label nodes <your-node-name> <key>=<value>` : label a node

**Taints and Tolerations**

- `k taint no <node-name> key=<value>:<taint-effect>`: taint a node. taint-effect can be `NoSchedule` or `PreferNoSchedule` or `NoExecute`

- `kubectl taint nodes controlplane node-role.kubernetes.io/control-plane:NoSchedule-` : untaint controlplane node, just add a dash at the end
-`kubectl describe node controlplane | grep -i taints` : list tainst on controlplane node


What does the READY column in the output of the kubectl get pods command indicate?

`Running Containers in POD/Total Containers in POD`

Delete `webapp` pod with force and immidiate termination

`k delete po --force --grace-period=0 webapp`

`kubectl delete pod <pod-name> --force --grace-period=0`

Delete all pods forcefull

`kubectl delete pods --all --force --grace-period=0`