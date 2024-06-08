# All of the supported plugins used be on directory /opt/cni/bin/

ls /opt/cni/bin/

# This is the directory in control plane to check what CNI plugin is used on the cluster

ls /etc/cni/net.d/

# For weave plugins we can check the IP range for pods looking the logs in the weave pod.

k logs -n kube-system weave-net-957ql | grep ipalloc

# To view services IP ranges 

cat /etc/kubernetes/manifests/kube-apiserver.yaml   | grep cluster-ip-range

# To view what proxy kube-proxy is using

k logs -n kube-system kube-proxy-bvk9x