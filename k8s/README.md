# k8s
Delete all objects under a namespace
```
kubectl delete namespaces [namespace]
```

Delete all objects under all namespaces
```
kubectl delete --all namespaces
```

Get pods for all namespaces
```
kubectl get pods --all-namespaces
kubectl get pods -A
```


# Kind
Show all clusters
```
kind get clusters
```

Delete cluster
```
kind delete cluster --name [cluster]
```


