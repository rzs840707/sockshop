# Setup Sockshop

<br>

### Step 1: Setup

Execute in terminal: 

```
kubectl create namespace sock-shop
kubectl label namespace sock-shop istio-injection=enabled
kubectl create -f manifests/
```



kubectl create -f manifests-policy/
