# ARGO CD

## install
source: https://argo-cd.readthedocs.io/en/stable/getting_started/
demo: https://www.youtube.com/watch?v=MeU5_k9ssrs



## apply the application.yaml in the cluster for argo cd to start watching the repo

$ kubectl apply -f application.yaml

## get admin password 
$ kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

user: admin
pass: UyClhWZXMs7QXgwy