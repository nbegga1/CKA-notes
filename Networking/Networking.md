## Explore environment

- See what physical interface is used: `cat /etc/network/interface` or `ifconfig -a` or `ip link`
- See on what ports services/pods are listening: `netstat -natulp | grep <service> | grep LISTEN`

## CNI

- Identify the network plugin configured for k8s: `ps aux | grep kubelet`
- Path configured with all binaries of CNI supported plugins: `/opt/cni/bin`
- CNI plugin configured to be used: `/etc/cni/net.d/` (check in the file within this directory too see which binary file will be executed)

## Deploy network solution

- Deploy network solution as pod: `kubectl apply -f <manifest-file>`

## Networking weave

- Check wich ip range the networking solution will be allocating: `kubectl logs -n kube-system <networking-solution-pod>` (ipalloc-range:.....)
