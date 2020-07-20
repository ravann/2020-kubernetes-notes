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

## SCALING

```bash
kubectl scale -f nginx-rep.yaml --replicas=3
```

Will change the replicas to 3 from 5. We can also scale by mentioning resource name as below:

```bash
kubectl scale --replicas=4 deployment/nginx-rep
```

## DEPLOYMENT STRATEGIES

https://azure.microsoft.com/en-us/overview/kubernetes-deployment-strategy/

### DEPLOYMENT REVISIONS & ROLLBACK

```bash
kubectl rollout history deployment/nginx-rep
```

OR

```bash
kubectl rollout history deployment.v1.apps/nginx-rep
```

To rollback to a specific revision

```bash
kubectl rollout undo deployment.v1.apps/nginx-rep --to-revision=2
```

To rollback to previous revision, we can also use:

```bash
kubectl rollout undo deployment.v1.apps/nginx-rep
```
