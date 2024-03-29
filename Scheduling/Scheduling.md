## Labels and Selectors 

- Get objects based on label: `kubectl get <object>  --selector <key1>=<value1>,<key2>=<value2>`
- ReplicaSet matchlabels must correspond to pod labels defined in the pods spec.

## Taints and Tolarations

- Add taint to node: `kubectl taint node <node-name> <key>=<value>:<NoSchedule/NoExecute/PreferNoSchedule>`
- Add toleration to pod: `kubectl explain pod.spec.tolarations`

## Node Affinity

- Label a node: `kubectl label node <node-name> <key>=<value>`
- Create node affinity on pod spec: ![image](https://user-images.githubusercontent.com/64038272/225858439-3e2aafb0-05f3-4659-993b-4b7d518ad581.png)

## Resource Limits

- Define resource limits for pod: ![image](https://user-images.githubusercontent.com/64038272/226167773-187cbce5-421e-4dec-ad6a-3314b890c3a5.png)
- Define resource requests for pod: ![image](https://user-images.githubusercontent.com/64038272/226167800-34d2eaf0-6717-43fd-bdcf-f720855de638.png)

- If a pod is `OOMKilled` that means that it ran out of memory.

## DaemonSets

- Easy way to create DaemonSet yaml: `kubectl create deployment <ds-name> -n <namespace> --image=<image-name> --dry-run=client -o yaml` **and change** `kind: Deployment` **to** `kind: DaemonSet`

## Static pods

- You can recognize static pods by looking if the nodename is appended to the end of the pod name. Or look at the `ownerReferences` in the pod yaml.
- Path of the directory holding the static pod yaml files: Check the `staticPodPath` section in the kubelet configuration (/var/lib/kubelet/config.yaml). (PS: The location of the kubelet configuration file can also be found by looking at the systemd unit file of the kubelet) 

## Multiple Schedulers

- Let a pod be scheduled by other than the default scheduler: In pod spec add `schedulerName: <non-default-scheduler>`
