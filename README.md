# Configuration Project for meet stackit 
This repo is used to install all the stuff we need to K8N via ArgoCD

# Stuff to read or to watch
* Install ArgoCD https://argo-cd.readthedocs.io/en/stable/getting_started/#1-install-argo-cd
* ArgoCD quick start https://www.youtube.com/watch?v=MeU5_k9ssrs


# Find code repos
* https://github.com/JJDoneAway/meet-stackit
* https://github.com/JJDoneAway/meet-stackit-test

# Install ArgoCD
`kubectl create namespace argocd`
`kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/core-install.yaml`
wait until a public ip is asigned to the argocd server `kubectl get -n argocd svc  argocd-server`
