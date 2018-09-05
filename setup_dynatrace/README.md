# Setup Dynatrace

<br>

### Step 1: Set environment variables

Execute in terminal:

```
export API_URL=https://oft62130.sprint.dynatracelabs.com/api
export API_TOKEN=qjY6KIasQ8uDh6UKM0Hwk
export PLATFORM_AS_A_SERVICE_TOKEN=dudXKTTxScSTQpukjIq-9
export HOST_GROUP=istio
```

<br>

### Step 2: Install Dynatrace One-Agent Operator

Execute in terminal:

```
kubectl create -f https://raw.githubusercontent.com/Dynatrace/dynatrace-oneagent-operator/master/deploy/kubernetes.yaml
```

```
kubectl -n dynatrace create secret generic oneagent --from-literal="apiToken=${API_TOKEN}" --from-literal="paasToken=${PLATFORM_AS_A_SERVICE_TOKEN}"
```

Execute in terminal:

```
cat <<EOF | kubectl create -f -
apiVersion: dynatrace.com/v1alpha1
kind: OneAgent
metadata:
  name: oneagent
  namespace: dynatrace
spec:
  apiUrl: ${API_URL}
  skipCertCheck: false
  tokens: ""
  nodeSelector: {}
  tolerations: []
  image: ""
  args:
  - APP_LOG_CONTENT_ACCESS=1
  - HOST_GROUP=${HOST_GROUP}
  env:
    - name: ONEAGENT_ENABLE_VOLUME_STORAGE
      value: "true"
EOF
```
