### Kubernetes basics

1. Components: https://kubernetes.io/docs/concepts/overview/components/

```bash
kubectl get node
```

2. Tooling

- kubectl (must have anyway): https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/
- multipal UI tools (VsCode plugins, Lens etc)

3. Install options:

- kubeadm
- kubespray, deckhouse etc
- cloud providers

Distributions CNCF: 
https://landscape.cncf.io/card-mode?category=certified-kubernetes-distribution&grouping=category

4. Worfkoads

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
```bash
kubectl apply -f nginx.yaml
```

5. 