# KUBERNETES SETUP

Use docker desktop, enable kubernetes

# KUBERNETES BASIC COMMANDS

```bash
kubectl version
kubectl cluster-info
kubectl get all
kubectl get pods
kubectl get deployments
```

# KUBERNETES WEB UI DEVELOPMENT

- Install Web UI Development
- - Search for "kubernetes web ui dashboard"
- - Site: https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/

kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0/aio/deploy/recommended.yaml
kubectl describe secret -n kube-system
kubectl proxy

[URL to Open in browser](http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#/overview?namespace=_all)
