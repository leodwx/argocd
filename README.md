# ARGO CD

## pre-step
switch to docker desktop before installing Arcgo-CD
> kubectl config use-context docker-desktop

## install
source: https://argo-cd.readthedocs.io/en/stable/getting_started/
demo: https://www.youtube.com/watch?v=MeU5_k9ssrs

STEP 1: install with UI 
> kubectl create namespace argocd
> kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

## get admin password 
> kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

### run the app
kubectl port-forward svc/argocd-server -n argocd 9000:443

login using: 
> user: admin
> pass: EL-qLD-Na0bjWNam


## deploy the applications
application.yaml in the cluster for argo cd to start watching the java/springbot app get deployed
> kubectl apply -f application.yaml

accessing the demo java app:
http://localhost:31001/driver/321321
http://localhost:31001/driver/123456

see the env variables: open in Firefox for pretty-printed json
http://localhost:31001/application-status

deploy application-python.yaml to start watching the python app
> kubectl apply -f application-python.yaml



## Install ArgoCD CLI
need brew in Ubuntu: https://www.how2shout.com/linux/how-to-install-brew-ubuntu-20-04-lts-linux/#:~:text=1%20Open%20a%20command%20terminal.%20%202%20Install,the%20brew%20uninstallation%20script%2C%20also%20available...%20More%20

### Service Type Load Balancer
Change the argocd-server service type to LoadBalancer:
> kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'

### Login to CLI
> argocd login 127.0.0.1
use same cred from the UI console

Show the java demo-app deployment:
> argocd app get demo-argo-application