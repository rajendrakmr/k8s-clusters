# Installing Argo CD
##### Create a namespace for Argo CD:
```base
    kubectl create namespace argocd
 ```
### Apply the Argo CD manifest:
 ```base
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
### Check services in Argo CD namespace:
 ```base
    kubectl get svc -n argocd
```
### Expose Argo CD server using NodePort:
```base
   kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "NodePort"}}'
```
### Apply the Argo CD manifest:
 ```base
   kubectl port-forward -n argocd service/argocd-server 8443:443 --address=0.0.0.0 &
```


### Install cli:
 ```base
   curl -sSL -o argocd-linux-amd64 https://github.com/argoproj/argo-cd/releases/latest/download/argocd-linux-amd64
    sudo install -m 555 argocd-linux-amd64 /usr/local/bin/argocd
    rm argocd-linux-amd64
```

### Login inside argocd cli:
 ```base
  argocd login localhost:8080 --username admin --password <your-password> --insecure
```
