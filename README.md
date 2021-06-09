# ArgoCD Installation
1. `vagrant up`
2. `vagrant ssh`
3. `curl -sfL https://get.k3s.io | sh`
4. `sudo su -`
5. `kubectl create namespace argocd`
6. `kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml`
7. `kubectl get svc -n argocd argocd-server -o yaml > argocd-nodeport.yaml`
8. `kubectl apply -f argocd-nodeport.yaml -n argocd`
9. `kubectl get svc -n argocd`
10. `kubectl port-forward svc/argocd-server-nodeport -n argocd 8080:443`
10. `https://vagrantip:nodeport`
11. `kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d`
12. `argocd login localhost:8080`
13. `argocd account update-password`

# Deployment
1. `create namespace.yaml`
2. `create configmap.yaml`
3. `create deployment.yaml`
4. `create service.yaml`
5. `kubectl apply -f argocd-nginx.yaml`
6. `kubectl get application -n argocd`
7. `go to argocd in browser and sync`
8. `kubectl get ns`
9. `kubectl get deploy -n demo`
10. `kubectl get svc -n demo`
