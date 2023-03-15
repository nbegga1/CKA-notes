

## Worker node troubleshooting

- Worker node is down
  - Check kubelet service on the specific node: `ssh <node-name>` then `service kubelet status`
  - Check kubelet logs: `journalctl -u kubelet`
  - Change kubelet config: `/var/lib/kubelet/config.yaml` (All config files used for kubelet can be found in `/etc/systemd/system/kubelet.service.d/..`)

## Network troubleshooting

- If CoreDNS pod in `Pending`: check if the network plugin is installed
- If CoreDNS pod is in `CrashLoopBackOff` or `Error` state: If you have nodes that are running **SELinux** with an older version of Docker you might experience a scenario where the coredns pods are not starting. To solve that you can try one of the following options
  - Upgrade to a newer version of Docker
  - Disable SELinux
  - Modify the coredns deployment to set `allowPrivilegeEscalation` to `true`
