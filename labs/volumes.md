# Volumes

[Volumes Documentation](https://github.com/Mirantis/virtlet/blob/master/docs/volumes.md)

Virtlet only partially supports Kubernetes Volumes. It’s possible to use Virtlet’s flexvolume driver to specify mounting of local block devices, “ephemeral volumes” with their lifetime bound to the one of the pod, and Ceph volumes that are specified as block devices.

ConfigMap and Secret mounts are supported, which are actually copied into the VMs using the Cloud-Init mechanism(more about it in the next chapter).


See how to use flexvolume with VM Pod:

```bash
cat virtlet/examples/ubuntu-vm-with-volume.yaml
kubectl create -f virtlet/examples/ubuntu-vm-with-volume.yaml
```

There is ongoing work to support more options:

* [Persistent Block Volumes](https://github.com/Mirantis/virtlet/pull/751)
* [Directory volume with 9pfs](https://github.com/Mirantis/virtlet/pull/739) it means support for emptyDir, hostPath...

There are also plans to work on [CSI](https://kubernetes.io/blog/2018/01/introducing-container-storage-interface/)
