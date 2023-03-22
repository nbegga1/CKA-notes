## OS upgrades

- Drain node of workloads: `kubectl drain <node>`
- Mark node as schedulable: `kubectl uncordon <node>`
- Mark node as unschedulable: `kubectl cordon <node>`
- When you encounter the following error when trying to `kubectl drain <node>` :`rror: unable to drain node "node01" due to error:cannot delete Pods declare no controller`
  - It probabllly means that the pod is not part of a replication controller
  
## Cluster upgrade

- Verify on which system your host is running: `cat /etc/*release*`
- https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/kubeadm-upgrade/
  - Controlplane components should always be upgraded first
  - You must always upgrade **1** major version at a time
  - Make sure to drain a node before upgrading.
  - Make sure to do the kubeadm, kubelet and kubectl upgrades on the workernode itself.
  - ![image](https://user-images.githubusercontent.com/64038272/226656840-1efa8f43-ecb0-48a5-a7bb-2b82bc73c75b.png)

## ETCD

- Take snapshot of the ETCD database: `ETCDCTL_API=3 etcdctl --endpoints=https://127.0.0.1:2379 --cacert=<trusted-ca-file> --cert=<cert-file> --key=<key-file> snapshot save <backup-file-location>`
- Restore etcd: 
  - `ETCDCTL_API=3 etcdctl snapshot restore --data-dir <new-etcd-location> <snapshot-location>`
  - Modify etcd location in etcd manifest file because ETCD is a static pod: `vi /etc/kubernetes/manifest/etcd.yaml`
  - Modify the volume path to `<new-etcd-location>`
- Stacked etcd: etcd is on the same node as the controlplane components
- External etcd: etcd is not on the same node as the controlplane components
