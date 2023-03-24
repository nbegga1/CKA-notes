# CKA-notes

- Verify what a user has permissions to do: `kubectl auth can-i <action> <resource> --namespace=<namespace> --as <user>`

- Get pod info: `kubectl get pod -o wide`

- Usage of how to create objects: `kubectl create <object> --help`

- Wait for a pod to be in a `Running` state: `kubectl get pods -n <namespace> --watch`

- Get documentation of object manifest: `kubectl explain <object>.<for-example-spec>.<for-example-imagePullSecret>`

- Edit pod yaml will give error `error: pods "ubuntu-sleeper" is invalid  A copy of your changes has been stored to "/tmp/kubectl-edit-1063288277.yaml"`. Use `kubectl replace --force -f </tmp/...>` to force replace the pod yaml.

- Get pod yaml sample: `kubectl run <pod-name> --image=<image-name> --dry-run=client -o yaml`

- Execute command in pod: `kubectl exec <pod-name> -- <command>`  (Add `-i -t` to get an interactive terminal)

- Switch to other default namespace: `kubectl config set-context --current --namespace=<namespace>`

- Controlplane components are static pods, for which the manifest is usually on the node filesystem: `/etc/kubernetes/manifests`

- Expose pod,rs or deployment: `kubectl expose <object> ...`

Troubleshooting

Cheatsheet: https://kubernetes.io/docs/reference/kubectl/cheatsheet/

![image](https://user-images.githubusercontent.com/64038272/226975611-8bee0560-5b7b-4f0c-9252-6081fa035444.png)

![image](https://user-images.githubusercontent.com/64038272/226975681-742b1ccd-b638-46d2-b3f7-6af9493511c6.png)
