# Setup

<br>

### Step 1: Setup Istio

Execute in terminal: 

```
kubectl apply -f install/kubernetes/helm/istio/templates/crds.yaml
helm template install/kubernetes/helm/istio --name istio --namespace istio-system > $HOME/istio.yaml
kubectl create namespace istio-system
kubectl apply -f $HOME/istio.yaml

or 

kubectl apply -f install/kubernetes/helm/istio/templates/crds.yaml
kubectl apply -f install/kubernetes/helm/helm-service-account.yaml
helm init --service-account tiller
helm install install/kubernetes/helm/istio --name istio --namespace istio-system

or 

jx create addon istio
```


### Step 2: Setup Istio Injection

Execute in terminal: 

```
kubectl label namespace jx-staging istio-injection=enabled
find manifests/sock-shop-istio -type f -exec istioctl create -f {} \;
```
