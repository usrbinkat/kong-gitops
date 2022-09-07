# Kong ArgoCD GitOps

A repo demonstrating Kong GitOps deployment with ArgoCD.

###### Included:
- Kong Gateway
- Kuma Mesh on Kubernetes
- Kuma Mesh Universal Nodes

###### Dependencies:
- kind
- argocd cli
## Create Kind Cluster

```bash
kind create cluster --config kind/config.yaml
```

## Install ArgoCD

```bash
kubectl create namespace argocd
kubectl --namespace argocd kustomize argocd | kubectl apply -n argocd -f -
```

- get argocd default admin password

```bash
kubectl get secrets -n argocd -oyaml argocd-initial-admin-secret -o jsonpath='{.data.password}' | base64 -d ; echo
```

- Port-forward argocd

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

- Port-forward argocd webui & login to https://localhost:8080
- Credentials `admin:$PASSWORD`

```bash
argocd login localhost:8080
```

## asdf

```bash
```