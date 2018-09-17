# Setup

<br>

### Step 1: Setup Istio

Execute in terminal: 

```
kubectl apply -f install/kubernetes/helm/istio/templates/crds.yaml
helm template install/kubernetes/helm/istio --name istio --namespace istio-system > $HOME/istio.yaml
kubectl create namespace istio-system
kubectl apply -f $HOME/istio.yaml
```


### Step 2: Setup Sockshop

Execute in terminal: 

```
kubectl label namespace jx-staging istio-injection=enabled
kubectl create -f manifests/sock-shop
find manifests/sock-shop-istio -type f -exec istioctl create -f {} \;
```
