# 1 Kubeadm : Tool to create / initialize cluster

  # 1. Disable the swap memmory
  > sudo swapoff -a
  > sudo sed -i '/ swap / s/^/#/' /etc/fstab

  # 2. Add Kubernetes cgroup 
  >  sudo vim  /etc/docker/daemon.json
   {
       "exec-opts": ["native.cgroupdriver=systemd"]
   }
    > sudo systemctl daemon-reload
    > sudo systemctl restart docker
    > sudo systemctl restart kubelet
    > sudo docker info |grep -i cgroup

  # 3. Assign Unique Hostname
   > sudo hostnamectl set-hostname master-node

# start kubernetes cluster  -> start kubernetes master 
> sudo kubeadm init --pod-network-cidr=10.244.0.0/16
    # output : Your Kubernetes control-plane has initialized successfully!

# To start using your cluster, you need to run the following as a regular user:

  > mkdir -p $HOME/.kube
  > sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  > sudo chown $(id -u):$(id -g) $HOME/.kube/config

# Alternatively, if you are the root user, you can run:

  > export KUBECONFIG=/etc/kubernetes/admin.conf

# You should now deploy a pod network to the cluster.
 > sudo export kubever=$(kubectl version | base64 | tr -d '\n')
 > sudo kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$kubever"


