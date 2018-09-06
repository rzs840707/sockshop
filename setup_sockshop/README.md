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


## Step 2: 
