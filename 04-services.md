# SERVICES

## TYPES OF SERVICES

- ClusterIP: Exposes the Service on a cluster-internal IP. Choosing this value makes the Service only reachable from within the cluster. This is the default ServiceType.
- NodePort: Exposes the Service on each Node's IP at a static port (the NodePort). A ClusterIP Service, to which the NodePort Service routes, is automatically created. You'll be able to contact the NodePort Service, from outside the cluster, by requesting <NodeIP>:<NodePort>.
- LoadBalancer: Exposes the Service externally using a cloud provider's load balancer. NodePort and ClusterIP Services, to which the external load balancer routes, are automatically created.
- ExternalName: Maps the Service to the contents of the externalName field (e.g. foo.bar.example.com), by returning a CNAME record

### ClusterIP

Refer to the below sample nginx-serv deployment and service files.

[nginx-serv-d YAML](04-services/nginx-serv-d.yaml)

[nginx-serv-s YAML](04-services/nginx-serv-s.yaml)

The below service file is used to create network for nginx-rep file that was worked in deployments section.

[nginx-rep-s YAML](04-services/nginx-rep-s.yaml)

Notice, the selector is a run label as the label defined in the deployment is run.

### Testing ClusterIP

Before we start to test, lets look at things running on my kubernetes cluster.

![kubectl get all](04-services/cip_k_get_all.png)

Now connect to a random pod running on the same namespace ( not sure at this point if namespace makes a difference)

![test service is working](04-services/cip_test_service.png)

Both the service name and IP Address are recognized by the node!!!
