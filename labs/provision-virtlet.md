## Virtlet provisioning
#### Using MCP

Follow the latest instructions how to [deploy Kubernetes cluster](https://docs.mirantis.com/mcp/latest/mcp-deployment-guide/deploy-mcp-cluster-using-drivetrain/deploy-k8s.html) and then deploy Virtlet [Deploy Virtlet on MCP](https://docs.mirantis.com/mcp/latest/mcp-deployment-guide/deploy-mcp-cluster-manually/deploy-kubernetes-cluster-manually/enable-virtlet/deploy-virtlet.html)

#### Using kubeadm-dind-cluster integration

For this workshop you will use [kubeadm-dind-cluster](https://github.com/kubernetes-sigs/kubeadm-dind-cluster) cluster.
Download a `demo.sh` script which will deploy Kubernetes and provision Virtlet there.

```bash
wget https://raw.githubusercontent.com/Mirantis/virtlet/v1.2.0/deploy/demo.sh
chmod +x demo.sh
MULTI_CNI=1 ./demo.sh
```

Answer `y` to the script’s questions and wait until the script completes. The script will create a CirrOS VM for you and display its shell prompt.


#### Other deployment options

To see how to provision Virtlet on non MCP clusters see the [deployment docs](https://github.com/Mirantis/virtlet/blob/master/deploy/real-cluster.md)
