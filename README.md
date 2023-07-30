# install-k8s
install-k8s


# 1) Set hostname on Each Node
    root@master:~/.aws# hostnamectl set-hostname "k8smaster.jy6.shop"
    root@master:~/.aws# hostnamectl
     Static hostname: k8smaster.jy6.shop
           Icon name: computer
          Machine ID: f13d61e1b9eb4977bb8fdadeacdd00a9
             Boot ID: cb109f273d7a461db8e10cad64eeb73c
    Operating System: Ubuntu 22.10
              Kernel: Linux 5.19.0-46-generic
        Architecture: x86-64
     Hardware Vendor: Hewlett-Packard
      Hardware Model: HP EliteBook 840 G2
    Firmware Version: M71 Ver. 01.31
    root@master:~/.aws# exec bash
    root@k8smaster:~/.aws# 
  
    
    
    
    root@worker2:~# sudo hostnamectl set-hostname "k8sworker1.example.net"
    root@worker2:~# hostnamectl
     Static hostname: k8sworker1.example.net
           Icon name: computer
          Machine ID: d58313246ca34fc6bdb115c74932ad50
             Boot ID: 792b794fe7a44d9ca203f2555384ea7c
    Operating System: Ubuntu 22.10
              Kernel: Linux 5.19.0-45-generic
        Architecture: x86-64
     Hardware Vendor: Hewlett-Packard
      Hardware Model: HP EliteBook 8470p
    Firmware Version: 68ICF Ver. F.74
    root@worker2:~# exec bash
    root@k8sworker1:~#
    
  
    
    sangbinlee9@worker4:~$ sudo hostnamectl set-hostname "k8sworker2.example.net"
    [sudo] password for sangbinlee9:
    sangbinlee9@worker4:~$ exec bash
    sangbinlee9@k8sworker2:~$
    root@k8sworker2:/home/sangbinlee9# hostnamectl
     Static hostname: k8sworker2.example.net
           Icon name: computer
          Machine ID: d4d1aba42a2c412292cf1eea1e10fdc4
             Boot ID: d2c72ad6d529455e9f5ab304de0d2463
    Operating System: Ubuntu 22.10
              Kernel: Linux 5.19.0-42-generic
        Architecture: x86-64
     Hardware Vendor: Dell Inc.
      Hardware Model: Inspiron N7010
    Firmware Version: A11
    root@k8sworker2:/home/sangbinlee9#
    
    
    
  
  

# in master node,     sudo kubeadm init --control-plane-endpoint=k8smaster.jy6.shop
    
    
    root@k8smaster:~# sudo kubeadm init --control-plane-endpoint=k8smaster.jy6.shop
    [init] Using Kubernetes version: v1.27.4
    [preflight] Running pre-flight checks
    [preflight] Pulling images required for setting up a Kubernetes cluster
    [preflight] This might take a minute or two, depending on the speed of your internet connection
    [preflight] You can also perform this action in beforehand using 'kubeadm config images pull'
    W0730 11:14:10.512991   53528 images.go:80] could not find officially supported version of etcd for Kubernetes v1.27.4, falling back to the nearest etcd version (3.5.7-0)
    W0730 11:14:50.092063   53528 checks.go:835] detected that the sandbox image "registry.k8s.io/pause:3.8" of the container runtime is inconsistent with that used by kubeadm. It is recommended that using "registry.k8s.io/pause:3.9" assandbox image.
    [certs] Using certificateDir folder "/etc/kubernetes/pki"
    [certs] Generating "ca" certificate and key
    [certs] Generating "apiserver" certificate and key
    [certs] apiserver serving cert is signed for DNS names [k8smaster.jy6.shop kubernetes kubernetes.default kubernetes.default.svc kubernetes.default.svc.cluster.local] and IPs [10.96.0.1 192.168.0.8]
    [certs] Generating "apiserver-kubelet-client" certificate and key
    [certs] Generating "front-proxy-ca" certificate and key
    [certs] Generating "front-proxy-client" certificate and key
    [certs] Generating "etcd/ca" certificate and key
    [certs] Generating "etcd/server" certificate and key
    [certs] etcd/server serving cert is signed for DNS names [k8smaster.jy6.shop localhost] and IPs [192.168.0.8 127.0.0.1 ::1]
    [certs] Generating "etcd/peer" certificate and key
    [certs] etcd/peer serving cert is signed for DNS names [k8smaster.jy6.shop localhost] and IPs [192.168.0.8 127.0.0.1 ::1]
    [certs] Generating "etcd/healthcheck-client" certificate and key
    [certs] Generating "apiserver-etcd-client" certificate and key
    [certs] Generating "sa" key and public key
    [kubeconfig] Using kubeconfig folder "/etc/kubernetes"
    [kubeconfig] Writing "admin.conf" kubeconfig file
    [kubeconfig] Writing "kubelet.conf" kubeconfig file
    [kubeconfig] Writing "controller-manager.conf" kubeconfig file
    [kubeconfig] Writing "scheduler.conf" kubeconfig file
    [kubelet-start] Writing kubelet environment file with flags to file "/var/lib/kubelet/kubeadm-flags.env"
    [kubelet-start] Writing kubelet configuration to file "/var/lib/kubelet/config.yaml"
    [kubelet-start] Starting the kubelet
    [control-plane] Using manifest folder "/etc/kubernetes/manifests"
    [control-plane] Creating static Pod manifest for "kube-apiserver"
    [control-plane] Creating static Pod manifest for "kube-controller-manager"
    [control-plane] Creating static Pod manifest for "kube-scheduler"
    [etcd] Creating static Pod manifest for local etcd in "/etc/kubernetes/manifests"
    W0730 11:14:52.627467   53528 images.go:80] could not find officially supported version of etcd for Kubernetes v1.27.4, falling back to the nearest etcd version (3.5.7-0)
    [wait-control-plane] Waiting for the kubelet to boot up the control plane as static Pods from directory "/etc/kubernetes/manifests". This can take up to 4m0s
    [apiclient] All control plane components are healthy after 5.505122 seconds
    [upload-config] Storing the configuration used in ConfigMap "kubeadm-config" in the "kube-system" Namespace
    [kubelet] Creating a ConfigMap "kubelet-config" in namespace kube-system with the configuration for the kubelets in the cluster
    [upload-certs] Skipping phase. Please see --upload-certs
    [mark-control-plane] Marking the node k8smaster.jy6.shop as control-plane by adding the labels: [node-role.kubernetes.io/control-plane node.kubernetes.io/exclude-from-external-load-balancers]
    [mark-control-plane] Marking the node k8smaster.jy6.shop as control-plane by adding the taints [node-role.kubernetes.io/control-plane:NoSchedule]
    [bootstrap-token] Using token: ea952l.2u4c96zu93moau7f
    [bootstrap-token] Configuring bootstrap tokens, cluster-info ConfigMap, RBAC Roles
    [bootstrap-token] Configured RBAC rules to allow Node Bootstrap tokens to get nodes
    [bootstrap-token] Configured RBAC rules to allow Node Bootstrap tokens to post CSRs in order for nodes to get long term certificate credentials
    [bootstrap-token] Configured RBAC rules to allow the csrapprover controller automatically approve CSRs from a Node Bootstrap Token
    [bootstrap-token] Configured RBAC rules to allow certificate rotation for all node client certificates in the cluster
    [bootstrap-token] Creating the "cluster-info" ConfigMap in the "kube-public" namespace
    [kubelet-finalize] Updating "/etc/kubernetes/kubelet.conf" to point to a rotatable kubelet client certificate and key
    [addons] Applied essential addon: CoreDNS
    [addons] Applied essential addon: kube-proxy
    
    Your Kubernetes control-plane has initialized successfully!
    
    To start using your cluster, you need to run the following as a regular user:
    
      mkdir -p $HOME/.kube
      sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
      sudo chown $(id -u):$(id -g) $HOME/.kube/config
    
    Alternatively, if you are the root user, you can run:
    
      export KUBECONFIG=/etc/kubernetes/admin.conf
    
    You should now deploy a pod network to the cluster.
    Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
      https://kubernetes.io/docs/concepts/cluster-administration/addons/
    
    You can now join any number of control-plane nodes by copying certificate authorities
    and service account keys on each node and then running the following as root:
    
      kubeadm join k8smaster.jy6.shop:6443 --token ea952l.2u4c96zu93moau7f \
            --discovery-token-ca-cert-hash sha256:69e0262fe7a6b7f82a1dd62b547d9942ec2bd21a064b46e5b9397595cd9cb06a \
            --control-plane
    
    Then you can join any number of worker nodes by running the following on each as root:
    
    kubeadm join k8smaster.jy6.shop:6443 --token ea952l.2u4c96zu93moau7f \
            --discovery-token-ca-cert-hash sha256:69e0262fe7a6b7f82a1dd62b547d9942ec2bd21a064b46e5b9397595cd9cb06a
    root@k8smaster:~# exit




  
#

    
    
    root@k8smaster:~# kubectl cluster-info
    Kubernetes control plane is running at https://k8smaster.jy6.shop:6443
    CoreDNS is running at https://k8smaster.jy6.shop:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
    
    To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
    root@k8smaster:~# kubectl get nodes
    NAME                 STATUS   ROLES           AGE    VERSION
    k8smaster.jy6.shop   Ready    control-plane   135m   v1.27.1
    root@k8smaster:~#
    





#
    sudo netstat -tupln | grep 10250
    sudo kill -9 <PID>


# reset k8s


    
    
    kubeadm reset
    sudo apt-get purge kubeadm kubectl kubelet kubernetes-cni kube*   
    sudo apt-get autoremove  
    sudo rm -rf ~/.kube
    
    








#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
