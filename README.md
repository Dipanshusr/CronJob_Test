
controlplane ~ ➜  k get nodes
NAME           STATUS                        ROLES           AGE   VERSION
controlplane   Ready                         control-plane   57m   v1.26.0
node01         NotReady,SchedulingDisabled   <none>          56m   v1.26.0

controlplane ~ ➜  kubectl get nodes -o=json | jq -r '.items[] | select(.status.conditions[] | select(.type=="Ready" and .status=="True")) | .metadata.name'
controlplane


controlplane ~ ➜  kubectl get nodes -o=json | jq '.items | map(select(.status.conditions[] | select(.type == "Ready" and .status == "True"))) | length'
2

controlplane ~ ➜  k get node
NAME           STATUS   ROLES           AGE   VERSION
controlplane   Ready    control-plane   94m   v1.26.0
node01         Ready    <none>          93m   v1.26.0

controlplane ~ ➜  kubectl get nodes --no-headers | wc -l
2
