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

- Check wich **ip range** the networking solution will be allocating: `kubectl logs -n kube-system <networking-solution-pod>` see `ipalloc-range:...`

## Service networking

- Services are created by the `kube-proxy` and are clusterwide virtual objects
- Check **IP range** of services: `ps aux | grep kube-api-server` see `range=...`
- **This range should not overlap with CNI range!**
- Check iptables of a service: `iptables -L -t nat | grep <service-name>`
- Entries created by kube-proxy and what **proxier** it uses: `cat /var/log/kube-proxy.log`

## DNS

- Get IP of coredns service: kubectl get <dns-service> -n kube-system` or look in the `kubelet` configmap.
- Configuration file for configuring CoreDNS: `/etc/coredns/Corefile` inside CoreDNS pod. This is from configmap that is mounted in pod as a volume.
- Services can be resolved in the following ways:
  - `<service-name>` (if service 'is' in the same namespace)
  - `<service-name>.<namespace>`
  - `<service-name>.<namespace>.svc`
  - `<service-name>.<namespace>.svc.cluster.local`
- Ip of a service can be found by `kubectl describe svc -n <namespace> <service-name>` -> `IP: ...`
- Ip that a service is redirecting to can be found by `kubectl describe svc -n <namespace> <service-name>` -> `Endpoints: ...`

## Ingress

- rewrite-target option allows to change rewrite the input path so that `http://<ingress-service-input>:<ingress-port-input>/watch` becomes `http://<watch-service>:<port>/` instead of `http://<watch-service>:<port>/watch`
