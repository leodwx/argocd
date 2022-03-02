# ARGO CD

## install
source: https://argo-cd.readthedocs.io/en/stable/getting_started/
demo: https://www.youtube.com/watch?v=MeU5_k9ssrs

## get admin password 
$ kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo


## deploy the applciations

application.yaml in the cluster for argo cd to start watching the java app
$ kubectl apply -f application.yaml


deploy papplication-python.yaml to start watching the python app
$ kubectl apply -f application-python.yaml

