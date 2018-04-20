Directions to install are here
https://github.com/kubernetes/dashboard#kubernetes-dashboard

For my lab running kubectl proxy was annoying. Basically running helm version of minecraft in my basement so I am going to expose this as a service.

```
$ kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
$ kubectl proxy
http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/
```




Visit https://blog.2vcps.io/k8s for more info
# Create the Service Account

```
kubectl create -f admin-svc-account.yaml
```
# Create the CluserRoleBinding
```
kubectl create -f admin-clusterrolebding.yaml
```
# 

# Get the token to login

```
kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}')
```
# Get the svc nodeport port
```
kubectl get svc -n kube-system
```
# go to the master 
```
https://<master ip>:<svc port>
```
Use the token to login