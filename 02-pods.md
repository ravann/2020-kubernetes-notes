# KUBERNETES PODS

## Running a POD

```bash
kubectl run nginx-alp --image nginx:alpine
kubectl run nginx --image=nginx --replicas=5
```

## Listing and deleting pods

```bash
kubectl get pods
kubectl delete pod <PODNAME>
```

This deletes the pod, but deployment still exists, so kubernetes will recreate the pod

To ensure the nginx-alp doesnt run, we need to delete the deployment

```bash
kubectl get deployments
kubectl delete deployment nginx-alp
```

## Port Forwarding

```bash
kubectl port-forward deployment/nginx 8080:80
```

## YAML

[NGINX YAML](nginx-pod.yaml)

```bash
kubectl create -f nginx-pod.yaml --dry-run --validate=true
kubectl create -f nginx-pod.yaml
```

OR use apply

Apply will create if pod doesnt exist. It will make changes based on YAML if pod exists.

```bash
kubectl apply -f nginx-pod.yaml --dry-run --validate=true
kubectl apply -f nginx-pod.yaml
```

TO be able to run apply later for pods that are created using "create" command, we should use --save-config

```bash
kubectl delete pod my-nginx
kubectl create -f nginx-pod.yaml --save-config
kubectl apply -f nginx-pod.yaml
```

Get pod info

```bash
kubectl get pod my-nginx -o yaml
```

Describe pods

```bash
kubectl describe pod my-nginx
```

Get into the shell

```bash
kubectl exec my-nginx -it sh
```

## POD Health
