## Labels and Selectors 

- Get objects based on label: `kubectl get <object>  --selector <key1>=<value1>,<key2>=<value2>`
- ReplicaSet matchlabels must correspond to pod labels defined in the pods spec.

## Taints and Tolarations

- Add taint to node: `kubectl taint node <node-name> <key>=<value>:<NoSchedule/NoExecute/PreferNoSchedule>`
- Add toleration to pod: `kubectl explain pod.spec.tolarations`

## Node Affinity

- Label a node: `kubectl label node <node-name> <key>=<value>`
- Create node affinity on pod spec: ![image](https://user-images.githubusercontent.com/64038272/225858439-3e2aafb0-05f3-4659-993b-4b7d518ad581.png)

