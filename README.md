# Configuration Project for meet stackit 
This repo is used to install all the stuff we need to K8N via ArgoCD

# Stuff to read or to watch
* Install ArgoCD https://argo-cd.readthedocs.io/en/stable/getting_started/#1-install-argo-cd
* ArgoCD quick start https://www.youtube.com/watch?v=MeU5_k9ssrs


# Find code repos
* https://github.com/JJDoneAway/meet-stackit
* https://github.com/JJDoneAway/meet-stackit-test

# Install ArgoCD
1. `kubectl create namespace argocd`
2. `kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/core-install.yaml`
3. wait until a public ip is asigned to the argocd server `kubectl get -n argocd svc  argocd-server`
4. open UI e.g.: https://193.148.170.178/ (ignor the security warnings as it is just a selfe signed certificate)
5. get password out of the secret `kubectl get secret -n argocd argocd-initial-admin-secret -o jsonpath='{.data.password}' | base64 -d `
6. Login into UI with user admin and password (ignore the % sign at the end of the decoded password)

# Configure CD for meet-stackit
* `kubectl apply -f argoCD-config/meet-stackit.yaml`



