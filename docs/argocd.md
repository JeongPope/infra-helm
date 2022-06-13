# ArgoCD
### Helm Chart
```bash
$ helm repo add argo https://argoproj.github.io/argo-helm
$ helm fetch argo/argo-cd
```

### Install
```bash
$ helm upgrade -i argocd -f argocd.yaml ./argo-cd -n argocd
```

### ArgoCD CLI
```bash
$ curl -sSL -o ~/bin/argocd https://github.com/argoproj/argo-cd/releases/latest/download/argocd-linux-amd64
$ chmod +x ~/bin/argocd
```

### Credential : admin
```bash
# Get initial password
$ kubectl -n argocd get secret argocd-initial-admin-secret \
    -o jsonpath="{.data.password}" | base64 -d; echo

# Login
$ argocd login {{ server }} --grpc-web

# Update Password
$ argocd account update-password --grpc-web
```