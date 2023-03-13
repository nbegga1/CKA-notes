

## Worker node

- Worker node is down
  - Check kubelet service on the specific node: `ssh <node-name>` then `service kubelet status`
  - Check kubelet logs: `journalctl -u kubelet`
  - Change kubelet config: `/var/lib/kubelet/config.yaml` 
