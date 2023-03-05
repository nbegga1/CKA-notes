# CKA-notes

Usage of how to create objects: `kubectl create <object> --help`

Get documentation of object manifest: `kubectl explain <object>.<for-example-spec>.<for-example-imagePullSecret>`

Edit pod yaml will give error `error: pods "ubuntu-sleeper" is invalid  A copy of your changes has been stored to "/tmp/kubectl-edit-1063288277.yaml"`. Use `kubectl replace --force -f </tmp/...>` to force replace the pod yaml.

Get pod yaml sample: `kubectl run <pod-name> --image=<image-name> --dry-run=client -o yaml`
