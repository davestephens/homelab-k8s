# Homelab k8s

## Create admin user

Per instructions at https://github.com/kubernetes/dashboard/wiki/Creating-sample-user

```
kubectl apply -f admin-user.yml
```

```
kubectl apply -f admin-role.yml
```

Get token:
```
kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}')

```

## Ingress
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/mandatory.yaml
kubectl apply -f ingress-nginx/service-loadbalancer.yaml
```

## MetalLB
```
kubectl apply -f https://raw.githubusercontent.com/google/metallb/v0.7.3/manifests/metallb.yaml
kubectl apply -f metallb/config.yml
```