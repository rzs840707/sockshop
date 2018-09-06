# Setup Sockshop

<br>

### Step 1: Setup

Execute in terminal: 

```
kubectl create namespace sock-shop
kubectl label namespace sock-shop istio-injection=enabled
kubectl create -f manifests/sock-shop
find manifests/sock-shop-istio -type f -exec istioctl create -f {} \;
```

```
kubectl apply -f <(istioctl kube-inject -f manifests/carts.yaml)
kubectl apply -f <(istioctl kube-inject -f manifests/carts-db.yaml)
kubectl apply -f <(istioctl kube-inject -f manifests/catalogue.yaml)
kubectl apply -f <(istioctl kube-inject -f manifests/catalogue-db.yaml)
kubectl apply -f <(istioctl kube-inject -f manifests/front-end.yaml)
kubectl apply -f <(istioctl kube-inject -f manifests/orders-db.yaml)
kubectl apply -f <(istioctl kube-inject -f manifests/orders.yaml)
kubectl apply -f <(istioctl kube-inject -f manifests/payment.yaml)
kubectl apply -f <(istioctl kube-inject -f manifests/queue-master.yaml)
kubectl apply -f <(istioctl kube-inject -f manifests/rabbitmq.yaml)
kubectl apply -f <(istioctl kube-inject -f manifests/session-db.yaml)
kubectl apply -f <(istioctl kube-inject -f manifests/shipping.yaml)kubectl
kubectl apply -f <(istioctl kube-inject -f manifests/user-db.yaml)
kubectl apply -f <(istioctl kube-inject -f manifests/user.yaml)

istioctl apply -f manifests/front-end-gw.yaml
istioctl apply -f manifests/front-end-vs.yaml

istioctl apply -f manifests/carts-db-dest.yaml
istioctl apply -f manifests/carts-dest.yaml
istioctl apply -f manifests/catalogue-db-dest.yaml
istioctl apply -f manifests/catalogue-dest.yaml
istioctl apply -f manifests/orders-db-dest.yaml
istioctl apply -f manifests/orders-dest.yaml
istioctl apply -f manifests/payment-dest.yaml
istioctl apply -f manifests/queue-master-dest.yaml
istioctl apply -f manifests/rabbitmq-dest.yaml
istioctl apply -f manifests/session-db-dest.yaml
istioctl apply -f manifests/shipping-dest.yaml
istioctl apply -f manifests/user-db-dest.yaml
istioctl apply -f manifests/user-dest.yaml
```
