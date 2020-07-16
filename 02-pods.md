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

3 ways to check health

1. Run a command in pod
2. Connect to a socket and check if it goes though
3. Run a HTTP request and check its a OK response

3 types of checks

1. **Startup probe** - if defined waits for this probe to succeed before other probes are kicked off. This ensures other probes doesnt interfere with the container startup process
2. **Readiness probe** - checks if the container is ready to accept connections. A pod is considered ready when all its containers are ready. If the readiness probe fails, the endpoints controller will remove the IP address from all services.
3. **Livenes probe** - checks if container is healthy else will restart it

[Link to liveness Docs](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/)

[EXEC liveness - YAML](exec-liveness.yaml)

[HTTP liveness - YAML](nginx-pod-liveness.yaml)

[TCP liveness and readiness - YAML](tcp-liveness-readiness.yaml)
