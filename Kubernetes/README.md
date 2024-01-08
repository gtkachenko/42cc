### Pre-requisites
- Access to internet;
- Access to the k8s cluster;
- Installed `kubectl`;- Have specific namespace;
- Setup correct k8s context.


## Deploy k8s manifest
1. Created k8s deployment:
```shell
kubectl apply -f deployment.yaml
```
2. Create pod distribution budget:
```shell
kubectl apply -f pdb.yaml
```
3. Create horizontal pod autoscaler
```shell
kubectl apply -f hpa.yaml
```