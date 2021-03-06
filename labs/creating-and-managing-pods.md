# Creating and managing virtual machines

`demo.sh` script which you used provisioned Virtlet, started virtual machine with cirros image, started nginx container and exposed it via Service.
Let's check how it all works.

The script will finish and will ssh into a cirros vm. Switch to another console and list the pods:


```bash
kubectl get pod
```

cirros vm and nginx pod are both listed. Now list the services:

```bash
kubectl get svc
```

Now go back to the first console where you are logged in the cirros vm. Check that you have internet access:

```bash
ping 8.8.8.8
ping mirantis.com
```

In cluster network communication also works. Retrieve data from Nginx. Use Nginx service IP:

```bash
curl <nginx_service_ip>
```

Exit VM using ctrl-d command. 

## View Pod details

Use the `kubectl get` and `kubectl describe` commands to view details for the `cirros` VM Pod:

## View the logs of a Pod

Use the `kubectl logs` command to view the logs for the `cirros` VM Pod:

```
kubectl logs cirros-vm
```

## Attach to the VM

Use the `kubectl attach` command to attach to the VM console

```
kubectl attach -it cirros-vm
```

## Create new Ubuntu VM

Now you can create another virtual machine. Let's create Ubuntu VM from Virtlet examples:

```bash
cat virtlet/examples/ubuntu-vm-with-testuser.yaml
kubectl apply -f virtlet/examples/ubuntu-vm-with-testuser.yaml
```

This example also shows how cloud-init script can be used. Here new user: `testuser` is created and also ssh key is injected.
Wait for ubuntu VM:

```bash
kubectl get pod -w
```

Now attach to the VM using testuser/testuser credentials:

```bash
kubectl attach -it ubuntu-vm-with-testuser
```

Check if it also has internet connection.

## Use in Deployment

Because Virtlet VMs are just normal Pods you can create Deployment,DaemonSet or even StatefulSet from Virtual Machines:

```bash
cat examples/deployment-cirros-vm.yaml
kubectl apply -f examples/deployment-cirros-vm.yaml
```

When it's ready you can scale it:

```bash
kubectl scale --replicas=2 deploy/cirros
```

