Ways to install k8s
Kubeadm
Minikube
Kops
K8s in gcp


Step1:
On Master & worker node
sudo su
apt-get update  
apt-get install docker.io -y
service docker restart  
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -  
echo "deb http://apt.kubernetes.io/ kubernetes-xenial main" >/etc/apt/sources.list.d/kubernetes.list
apt-get update
apt install kubeadm=1.20.0-00 kubectl=1.20.0-00 kubelet=1.20.0-00 -y  

Step2:
On Master:
   kubeadm init --pod-network-cidr=192.168.0.0/16
   >Copy the token and paste it into the worker node.
Step3:
On Master: 
  exit
    mkdir -p $HOME/.kube
    sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
    sudo chown $(id -u):$(id -g) $HOME/.kube/config


   
step4:
On Master:
kubectl apply -f https://docs.projectcalico.org/manifests/calico.yaml
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.49.0/deploy/static/provider/baremetal/deploy.yaml





Our Kubernetes installation and configuration are complete
