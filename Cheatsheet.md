# CKA-notes

Get pod info: `kubectl get pod -o wide`

Usage of how to create objects: `kubectl create <object> --help`

Wait for a pod to be in a `Running` state: `kubectl get pods -n <namespace> --watch`

Get documentation of object manifest: `kubectl explain <object>.<for-example-spec>.<for-example-imagePullSecret>`

Edit pod yaml will give error `error: pods "ubuntu-sleeper" is invalid  A copy of your changes has been stored to "/tmp/kubectl-edit-1063288277.yaml"`. Use `kubectl replace --force -f </tmp/...>` to force replace the pod yaml.

Get pod yaml sample: `kubectl run <pod-name> --image=<image-name> --dry-run=client -o yaml`

Execute command in pod: `kubectl exec <pod-name> -- <command>`  (Add `-i -t` to get an interactive terminal)

Switch to other default namespace: `kubectl config set-context --current --namespace=<namespace>`
