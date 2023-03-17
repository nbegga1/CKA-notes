## Labels and Selectors 

- Get objects based on label: `kubectl get <object>  --selector <key1>=<value1>,<key2>=<value2>`
- ReplicaSet matchlabels must correspond to pod labels defined in the pods spec.

## Taints and Tolarations

- Add taint to node: `kubectl taint node <node-name> <key>=<value>:<NoSchedule/NoExecute/PreferNoSchedule>`
- Add toleration to pod: `kubectl explain pod.spec.tolarations`

## Node Affinity

- 
