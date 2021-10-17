# GitOps
PoC GitOps repository

# Intro
This is my Argo CD demo GitOps repository.

# Installation

1. Provision Kubernetes cluster of your choice. Solution has been tested with minikube and blow configuration:

```bash
minikube start --memory=4096 --cpus=2 --nodes=3 --kubernetes-version=v1.20.10 --driver="virtualbox" --profile="master"
minikube addons enable metrics-server --profile="master"
```

2. Add Argo CD Helm repository to your local Helm configuration. Make sure you use >v3.0 version (tested on v3.7.1).

```bash
helm repo add argo https://argoproj.github.io/argo-helm
```

3. Install Argo CD using values.yaml file provided in following folder:

```bash
kubectl create namespace argocd
helm install argocd -n argocd repos/argo-cd/3.25.1 --values=clusters/master/applications/argo-cd/values.yaml
```




