# Kubectl tips

## Enable Bash Completion

```
echo "source <(kubectl completion bash)" >> ~/.bashrc
source ~/.bashrc
```
---

## Get api resources

```
kubectl api-resources
```

--

## Get resources in namespaces 

```
kubectl get pods --all-namespaces

kubectl get pods -n kube-system 

kubectl get deployments -n kube-system 
```

---

## Usage of -o flag 

```
kubectl get pods -o wide 

kubectl get pods POD_NAME_HERE -o yaml 

kubectl get pods POD_NAME_HERE -o json 
```

## Labels and selections 

```
kubectl get pods -n kube-system --show-labels 

kubectl get pods -n kube-system --selector=k8s-app

kubectl get pods -n kube-system --selector=k8s-app=kube-dns

kubectl get pods -n kube-system -L k8s-app

```

## Advanced search using JSONPath

```
kubectl get pods -n kube-system --sort-by='{.metadata.name}'

kubectl get pods -n kube-system --sort-by='{.metadata.creationTimestamp}'

kubectl get pods -n kube-system --sort-by='{.spec.containers[0].name}'

```

--- 
## Create dummy manifest files

```
kubectl create namespace testnamespace --dry-run -o yaml

kubectl create deployment mydeploy --image=nginx --dry-run -o yaml

kubectl run nginx --image=nginx -o yaml --dry-run -o yaml

kubectl run mysql --image=mysql --port=3306 --env="MYSQL_ROOT_PASSWORD=root" --dry-run -o yaml

kubectl run nginx --image=nginx -o yaml --expose --dry-run -o yaml

```

---

## Use explain 

```
kubectl explain pod

kubectl explain pod.apiVersion

kubectl explain pod.spec.containers.image
```

















