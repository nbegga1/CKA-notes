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

## Certificates API

- Create CertificateSigningRequest
  - Get sample from https://kubernetes.io/docs/reference/access-authn-authz/certificate-signing-requests/ under the heading 'Create CertificateSigningRequest'
  - Use encoded .csr from user `cat <csr-file> | base64 -w 0`


## Kubeconfig

- Default kubeconfig file is located at: `${HOME}/.kube/config`
  - If you want to use a contex that is not not defined in your default kubeconfig file `kubectl config use-context <context> --kubeconfig <path-to-your-kubeconfig>`

## RBAC

- Check authorization modes: `cat /etc/kubernetes/manifests/kube-apiserver.yaml`
- Check user permission: `kubectl auth can -i get-pods -n default --as <user>`
- Create role from scratch `kubectl create role --help`
- Create rolebinding from scratch `kubectl create rolebinding --help`

## Cluster roles

- Create clusterrole from scratch `kubectl create clusterrole --help`
- Create clusterrolebinding from scratch `kubectl create clusterrolebinding --help`
- Get possible api-resources to apply permissions for `kubectl api-resources`

## Service Accounts

- Service accounts can be used in rolebindings to provide permissions.
- Add Service account to pod via deployment in the pod spec: `serviceAccountName: <sa-name>`

## Image security

- Store docker credentials: `kubectl create secret docker-registry <secret-name> --docker-server=<registry-server-name> --docker-username=<username> --docker-password=<password> --docker-email=<email>`
- OR `kubectl create secret docker-registry --help`
- Use secret in deployment under pod spec: `imagePullSecrets: - name: <secret-name>`

## Security contexts

- Find out which user the container runs as: `kubectl exec <container-name> -- whoami`
- Run container as specific user: within pod spec under the container section add `securityContext: > runAsUser: <user-id>`
- Add capabilities to user: within pod spec under the container section add `securityContext: > capabilities: <capability>`

NOTE: Security context can be specified both at the pod level and the container level. Security contexts defined at the container level override any security context defined at the pod level. Also note that capabilities can only be defined at the container level.

## Network policies

- Example of networkpolicy yaml: https://kubernetes.io/docs/concepts/services-networking/network-policies/
- Use multiple `to` or `from` if you want to allow traffic from/to multiple pods or ip's with different port numbers.
```yaml
...
  egress:
    - to:
        ...
    - to:
        ...
```

NOTE: Take note of the subtle difference between 

Allows ingress from a pod with the name `frontend` **AND** that is in the namespace `prod` 
```yaml
...
  ingress:
  - from
    - podSelector
          matchLabels:
            name: frontend
      namespaceSelector:
          matchLabels:
            name: prod
```

Allows ingress from any pod with the name `frontend` **OR** any pod that is in the namespace `prod`

```yaml
...
  ingress:
  - from
    - podSelector
          matchLabels:
            name: frontend
    - namespaceSelector:
           matchLabels:
             name: prod
```
