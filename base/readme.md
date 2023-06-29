### Kubernetes basics

1. Components: https://kubernetes.io/docs/concepts/overview/components/

```bash
kubectl get node
```

2. Tooling

- kubectl (must have anyway): 
-- Linux: https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/
-- MacOS: https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/
- multipal UI tools (VsCode plugins, Lens etc)

3. Ecosystem

- Monitoring: Prometheus, Victoria etc.
- Logging: Loki, Elastic etc
- Deploy tools: Helm, Kustomize, ArgoCD, Flux etc
- Storage: Rook, Longhorn etc
- Many other things

4. Install options:

- kubeadm
- kubespray, deckhouse etc
- cloud providers

Distributions CNCF: 
https://landscape.cncf.io/card-mode?category=certified-kubernetes-distribution&grouping=category

5. Worfkoads

- Pods: https://kubernetes.io/docs/concepts/workloads/pods/

```bash
kubectl get pod
```
- Workload resources: https://kubernetes.io/docs/concepts/workloads/controllers/

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  namespace: testing
spec:
  selector:
    matchLabels:
      app: nginx
  replicas: 2 # tells deployment to run 2 pods matching the template
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```
* Create namespace `testing`:
```bash
kubectl create ns testing
```
* Deploy nginx
```bash 
kubectl apply -f nginx.yaml
```

* Check deployment:
```bash
kubectl -n testing get deployments
```

* Check pods:
```bash
kubectl -n testing get pod
kubectl -n testing desribe pod {{pod_name}}
```

* Check nginx logs:
```bash
kubectl -n testing logs {{pod_name}} --tail 30
``` 

6. Configuration objects

- configmaps
- secrets

7. Resource managnent: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers

- Requests
- Limits
- Etc

