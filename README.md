# Certs Magic - Services and Ingress
CNCF Certs Magic Show - cloudnative.tv 

- cloudnative.tv [Dynatrace.md](Dynatrace.md)

- Services [Dynatrace.md](Dynatrace.md)
- Ingress [Dynatrace.md](Dynatrace.md)

• Understand host networking configuration on the cluster nodes
• Understand connectivity between Pods
• Understand ClusterIP, NodePort, LoadBalancer service types and endpoints
• Know how to use Ingress controllers and Ingress resources

# kubectl
kubectl api-resources
kubectl get services


# Nginx Install
Docker Desktop -  kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.48.1/deploy/static/provider/cloud/deploy.yaml


# Docker
docker build . -t certs-magic
docker tag certs-magic bradmccoydev/certs-magic:latest
docker push bradmccoydev/certs-magic:latest

Demo app

# Tips
ctrl r reverse search
kubectl run -h
kubectl run test bradmccoydev/test:latest — dry-run=client — o yaml > 2.yaml
kubectl create namespace certs-magic

kubectl run 
kubectl create certsmagic clusterip my-cs --tcp=5678:8080

# Pod
kubectl run certs-magic --image=bradmccoydev/certs-magic:latest --labels="app=certsmagic,env=prod"  -n certs-magic -—dry-run=client -o yaml 

# Deployment
kubectl create deployment certs-magic --image=bradmccoydev/certs-magic:latest --replicas=3 -n certs-magic --dry-run=client -o yaml 

kubectl expose deployment certs-magic --port=80 --target-port=80 --name=certs-magic -n certs-magic --dry-run=client -o yaml

## Services
# ClusterIP.
Exposes a service which is only accessible from within the cluster.

# NodePort.
Exposes a service via a static port on each node's IP.

# LoadBalancer.
Exposes the service via the cloud provider's load balancer.