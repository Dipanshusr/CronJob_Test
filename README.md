controlplane ~ ➜  kubectl get nodes -o=json | jq -r '.items[] | select(.status.conditions[] | select(.type=="Ready" and .status=="True")) | .metadata.name'
controlplane
