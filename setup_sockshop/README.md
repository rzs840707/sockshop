# Setup Sockshop

<br>

### Step 1: Setup

Execute in terminal: 

```
kubectl label namespace jx-staging istio-injection=enabled
kubectl create -f manifests/sock-shop
find manifests/sock-shop-istio -type f -exec istioctl create -f {} \;
```
