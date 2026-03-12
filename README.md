# k8s-practice

A hands-on Kubernetes project I built while learning the core concepts — deployments, services, and inter-pod communication on a local Minikube cluster.

## What's inside

**`k8s-web-hello`** — a simple Node.js app that responds with "Hello World". Deployed and exposed via a LoadBalancer service.

**`k8s-web-to-nginx`** — a Node.js app that talks to an nginx pod running in the same cluster and returns its response. Shows how services communicate internally using Kubernetes DNS.

**`manifests/`** — all the Kubernetes YAML (deployments + services for both apps and nginx).

## Run it yourself

```bash
# Start the cluster
minikube start

# Point Docker to Minikube's daemon
eval $(minikube docker-env)

# Build the images
docker build -t k8s-web-hello ./k8s-web-hello
docker build -t k8s-web-to-nginx ./k8s-web-to-nginx

# Apply manifests
kubectl apply -f manifests/

# Open the apps
minikube service k8s-web-hello
minikube service k8s-web-to-nginx
```

## Stack

Node.js · Docker · Kubernetes · Minikube · nginx
