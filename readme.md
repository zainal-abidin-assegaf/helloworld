# Hello world

## Getting started

To run this locally:

```
go run helloworld.go
curl http://localhost:8080
```

### Kubernetes dashboard

To get kubernetes dashboard running on Docker:

```
kubectl create -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
kubectl get pod --namespace=kube-system | grep dashboard
kubectl port-forward kubernetes-dashboard-7798c48646–2cdd7 8443:8443 --namespace=kube-system
```

### Build and run Docker image

```
docker build -t helloworld:v1 .
docker login
docker tag helloworld:v1 rogertinsley/hello-world:v1
docker push rogertinsley/hello-world
docker run -p 8080:8080 rogertinsley/hello-world:v1
```


### Deploy to Kubernetes

```
kubectl cluster-info
kubectl run helloworld --image=rogertinsley/hello-world:v1 --port=8080
kubectl get deployments
kubectl get pods
kubectl expose deployment helloworld --type=LoadBalancer
kubectl scale deployment helloworld --replicas=3
kubectl get deployment helloworld
```
