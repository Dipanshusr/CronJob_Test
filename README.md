
controlplane ~ ➜  k get nodes
NAME           STATUS                        ROLES           AGE   VERSION
controlplane   Ready                         control-plane   57m   v1.26.0
node01         NotReady,SchedulingDisabled   <none>          56m   v1.26.0

controlplane ~ ➜  kubectl get nodes -o=json | jq -r '.items[] | select(.status.conditions[] | select(.type=="Ready" and .status=="True")) | .metadata.name'
controlplane

