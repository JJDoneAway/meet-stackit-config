# Configuration Project for meet stackit 
This repo is used to install all the stuff we need to K8N via ArgoCD

# Stuff to read or to watch
* Install ArgoCD https://argo-cd.readthedocs.io/en/stable/getting_started/#1-install-argo-cd
* ArgoCD quick start https://www.youtube.com/watch?v=MeU5_k9ssrs
* https://artifacthub.io/packages/helm/prometheus-community/kube-prometheus-stack
* https://github.com/prometheus-operator/prometheus-operator/blob/main/Documentation/user-guides/getting-started.md


# Find code repos
* https://github.com/JJDoneAway/meet-stackit
* https://github.com/JJDoneAway/meet-stackit-test

# Setup K8N Cluster
* Create K8N Cluster on https://portal.stackit.cloud
* Download kubeconfig an store it as .kube/config
* test kubectl `kubectl get all`
* install lens: https://k8slens.dev/

# Install ArgoCD
1. `kubectl create namespace argocd`
2. `kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/core-install.yaml`
3. wait until a public ip is asigned to the argocd server `kubectl get -n argocd svc  argocd-server`
4. open UI e.g.: https://193.148.170.178/ (ignor the security warnings as it is just a selfe signed certificate)
5. get password out of the secret `kubectl get secret -n argocd argocd-initial-admin-secret -o jsonpath='{.data.password}' | base64 -d `
6. Login into UI with user admin and password (ignore the % sign at the end of the decoded password)

# Configure CD for meet-stackit
1. Install ArgoCD: `kubectl apply -f argoCD-config/applications/meet-stackit.yaml`
2. Install kube-prometheus stack: `kubectl apply -f argoCD-config/applications/kube-prometheus-stack.yaml`
3. Install prometheus operator extra (there is currently a bug, so we have to do it extra): `kubectl apply -f argoCD-config/applications/prometheus-operator.yaml`
4. Install Ingres: `kubectl apply -f argoCD-config/applications/ingreee-controller-nginx.yaml`
5. Install demo application: `kubectl apply -f argoCD-config/applications/meet-stackit.yaml`
6. Install prometheus monitoring for demo application: `kubectl apply -f argoCD-config/applications/prometheus.yaml`
