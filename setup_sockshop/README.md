# Setup Sockshop

<br>

### Step 1: Setup

Execute in terminal: 

```
kubectl create namespace sock-shop

kubectl apply -f manifests/front-end-gw.yaml
kubectl apply -f manifests/front-end-vs.yaml

kubectl apply -f manifests/carts-db-dest.yaml
kubectl apply -f manifests/carts-dest.yaml
kubectl apply -f manifests/catalogue-db-dest.yaml
kubectl apply -f manifests/catalogue-dest.yaml
kubectl apply -f manifests/orders-db-dest.yaml
kubectl apply -f manifests/orders-dest.yaml
kubectl apply -f manifests/payment-dest.yaml
kubectl apply -f manifests/queue-master-dest.yaml
kubectl apply -f manifests/rabbitmq-dest.yaml
kubectl apply -f manifests/session-db-dest.yaml
kubectl apply -f manifests/shipping-dest.yaml
kubectl apply -f manifests/user-db-dest.yaml
kubectl apply -f manifests/user-dest.yaml

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
kubectl apply -f <(istioctl kube-inject -f manifests/shipping.yaml)
kubectl apply -f <(istioctl kube-inject -f manifests/user-db.yaml)
kubectl apply -f <(istioctl kube-inject -f manifests/user.yaml)
```



kubectl create -f manifests-policy/
