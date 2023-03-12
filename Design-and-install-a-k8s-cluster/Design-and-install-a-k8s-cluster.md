## Install "Kubernetes the kubeadm way"

- (Prerequisites) Forwarding IPv4 and letting iptables see bridged traffic: https://kubernetes.io/docs/setup/production-environment/container-runtimes/
- Verify which distribution you are using: `cat /etc/*-release`
- Install kubeadm and kubelet packages with a specific version: https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/
  - Install specific version: `sudo apt-get install -y kubelet=<version> kubeadm=<version> kubectl=<version>`
- Get kubelet version: `kubelet --version`  
- Initialize controlplane (master) node: `kubeadm init --apiserver-advertise-address=<interface-ip> --apiserver-cert-extra-sans=controlplane --pod-network-cidr=<cidr-range>` (`cidr-range` should be the same as range configured in the CNI plugin) (`interface-ip` is the ip of eth interface of the node: `ip addr`)
- From the output of `kubeadm init` you get the commands to setup kubeconfig, the token to join other nodes to the cluster and you get the link to add a network plugin.
- Download file to modify and apply: `curl -fsSLo <local-dir>/<filename> <url-of-file>` then `kubectl apply -f <local-dir>/<filename>`

