# cni-k8s
DEMO DEMO DEMO

1) Clone repository

git clone https://github.com/cni-september/cni-k8s.git

cd cni-k8s

1)Install kubectl

cat <<EOF > /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=0
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF
yum install -y kubectl


2)Install minikube
Minikube is a tool that makes it easy to run Kubernetes locally. Minikube runs a single-node Kubernetes cluster inside a VM on your laptop for users looking to try out Kubernetes or develop with it day-to-day.


curl -Lo minikube https://storage.googleapis.com/minikube/releases/v0.28.2/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/


3)Start minikube locally 

minikube start --vm-driver=none


kubectl apply -f client-pod.yaml

kubectl apply -f client-node-port.yaml

kubectl get pods

kubectl get services

minikube ip

curl -w '\n' localhost:31515
-> hellow world should appear


4)Test kubernetes functionality:

docker container ls | grep september  -> get container id
docker container kill 'container_id'

kubectl get pods -> you should see the status and how the container restarts automatically
