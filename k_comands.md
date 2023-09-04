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

  **Pods:**
  - `kubectl get pods`: List all pods in the current namespace.
  - `kubectl describe pod <pod-name>`: Show detailed information about a specific pod.
  - `kubectl logs <pod-name>`: View logs of a specific pod.
  - `kubectl exec -it <pod-name> -- <command>`: Execute a command in a running pod.

**Services:**
  - `kubectl get services`: List all services in the current namespace.
  - `kubectl expose deployment <deployment-name> --port=<port> --target-port=<target-port> --type=<service-type>`: Create a service for a deployment.

**Deployments:**
  - `kubectl get deployments`: List all deployments in the current namespace.
  - `kubectl rollout status deployment <deployment-name>`: Check the status of a deployment.
  - `kubectl rollout history deployment <deployment-name>`: View the rollout history of a deployment.
  - `kubectl rollout undo deployment <deployment-name>`: Rollback a deployment to a previous revision.

**ConfigMaps and Secrets:**
  - `kubectl create configmap <configmap-name> --from-file=<file-path>`: Create a ConfigMap from a file.
  - `kubectl create secret generic <secret-name> --from-literal=<key>=<value>`: Create a secret.

**Scaling:**
  - `kubectl scale deployment <deployment-name> --replicas=<desired-replicas>`: Scale a deployment up or down.

**Namespace:**
  - `kubectl get namespaces`: List all namespaces.
  - `kubectl create namespace <namespace-name>`: Create a new namespace.
  - `kubectl config set-context --current --namespace=<namespace-name>`: Change the default namespace.

What does the READY column in the output of the kubectl get pods command indicate?

`Running Containers in POD/Total Containers in POD`

Delete `webapp` pod with force and immidiate termination

`k delete po --force --grace-period=0 webapp`

`kubectl delete pod <pod-name> --force --grace-period=0`

Delete all pods forcefull

`kubectl delete pods --all --force --grace-period=0`