# Setup Sockshop

<br>

### Step 1: Setup

Execute in terminal: 

```
kubectl create namespace sock-shop

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

istioctl create -f manifests/front-end-gw.yaml
istioctl create -f manifests/front-end-vs.yaml

istioctl create -f manifests/carts-db-dest.yaml
istioctl create -f manifests/carts-dest.yaml
istioctl create -f manifests/catalogue-db-dest.yaml
istioctl create -f manifests/catalogue-dest.yaml
istioctl create -f manifests/orders-db-dest.yaml
istioctl create -f manifests/orders-dest.yaml
istioctl create -f manifests/payment-dest.yaml
istioctl create -f manifests/queue-master-dest.yaml
istioctl create -f manifests/rabbitmq-dest.yaml
istioctl create -f manifests/session-db-dest.yaml
istioctl create -f manifests/shipping-dest.yaml
istioctl create -f manifests/user-db-dest.yaml
istioctl create -f manifests/user-dest.yaml
```
