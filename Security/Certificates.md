## View Certificate details

- Identify certificate files used
  - `cat /etc/kubernetes/manifests/<server-name>`

Note: ETCD has its own CA file.

- View certificate file
  - `openssl x509 -in <cert-file> -text -noout`

- What to do if you can not use the `kubectl` command anymore?
  - `kubectl` command sends request to the `kube-apiserver` so start looking in the `kube-apiserver` pod.
  - `docker ps -a | grep kube-apiserver`
  - `docker logs <container-id>`
  - Look at what is going wrong
    - Possible issue: connection with pod on port `2379` is failing. This indicates an issue with the `etcd` pod. Check logs of `etcd` container to troubleshoot...
