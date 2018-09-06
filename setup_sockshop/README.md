# Setup Sockshop

<br>

### Step 1: Setup

Execute in terminal: 

```
kubectl create -f manifests-policy/
kubectl create -f manifests/
```







# Front-end

## Step 1: Create Deployment and Service:

```
kubectl apply -f <(istioctl kube-inject -f manifests/front-end.yaml)
```

## Step 2: Create Destination Rule

```
cat <<EOF | istioctl create -f -
apiVersion: config.istio.io/v1alpha3
kind: DestinationRule
metadata:
  name: sock-shop-default-v1
  namespace: sock-shop
spec:
  host: front-end
  subsets:
  - name: v1
    labels:
      version: v1
EOF
```

## Step 3: 

```
cat <<EOF | kubectl apply -f -
apiVersion: networking.istio.io/v1alpha3
kind: Gateway
metadata:
  name: sock-shop-gateway
  namespace: sock-shop
spec:
  selector:
    istio: ingressgateway # use Istio default gateway implementation
  servers:
  - port:
      number: 80
      name: http
      protocol: HTTP
    hosts:
    - "*"
EOF
```

## Step 4:

```
cat <<EOF | kubectl apply -f -
apiVersion: networking.istio.io/v1alpha3
kind: VirtualService
metadata:
  name: sock-shop
  namespace: sock-shop
spec:
  hosts:
  - "*"
  gateways:
  - sock-shop-gateway
  http:
  - match:
    - uri:
        prefix: /
    route:
    - destination:
        port:
          number: 8079
        host: front-end
EOF
```
