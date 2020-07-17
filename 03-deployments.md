# KUBERNETES DEPLOYMENT

## Creating a deployment

```bash
kubectl run nginx-rep --image=nginx --replicas=5
```

Lets get the yaml generated

```bash
kubectl get deployment nginx-rep -o yaml > 03-deployments/nginx-rep.yaml
```

And improve on it. Added:

- ports
- resources
- livenessProbe

Removed lines that are runtime specific OR not clear at this point.

[nginx-rep YAML](03-deployments/nginx-rep.yaml)

# SCALING
