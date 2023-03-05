## Volumes

- Mounting different types of volumes on pods: https://kubernetes.io/docs/concepts/storage/volumes/
- Creating PVs and PVCs: https://kubernetes.io/docs/concepts/storage/persistent-volumes/
- Possible PV reclaim policy values:
     - `"Delete"` means the volume will be deleted from Kubernetes on release
     from its claim. The volume plugin must support Deletion.
     - `"Recycle"` means the volume will be recycled back into the pool of
     unbound persistent volumes on release from its claim. The volume plugin
     must support Recycling.
     - `"Retain"` means the volume will be left in its current phase (Released)
     for manual reclamation by the administrator. The default policy is Retain.

NOTE: Access modes of PVC and PV must match!