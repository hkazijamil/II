## Install Kubernetes

```
apt-get update && apt-get install -y apt-transport-https curl
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
cat <<EOF >/etc/apt/sources.list.d/kubernetes.list
deb https://apt.kubernetes.io/ kubernetes-xenial main
EOF
apt-get update
apt-get install -y kubelet kubeadm kubectl
apt-mark hold kubelet kubeadm kubectl

```
```
systemctl daemon-reload
systemctl restart kubelet
```

```
 
```
```
kubeadm reset

kubeadm init --pod-network-cidr=192.168.0.0/16 --apiserver-advertise-address=178.128.52.148
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
export KUBECONFIG=/etc/kubernetes/admin.conf

kubectl apply -f https://docs.projectcalico.org/v3.3/getting-started/kubernetes/installation/hosted/rbac-kdd.yaml
kubectl apply -f https://docs.projectcalico.org/v3.3/getting-started/kubernetes/installation/hosted/kubernetes-datastore/calico-networking/1.7/calico.yaml

kubectl create -f https://raw.githubusercontent.com/kubernetes/dashboard/master/aio/deploy/recommended/kubernetes-dashboard.yaml

kubectl create clusterrolebinding dashboard-admin -n default --clusterrole=cluster-admin --serviceaccount=default:dashboard
kubectl create serviceaccount dashboard -n default
kubectl describe services kubernetes-dashboard --namespace=kube-system

kubectl cluster-info

kubectl get svc --namespace kube-system

kubectl -n kube-system edit service kubernetes-dashboard
kubectl -n kube-system get service kubernetes-dashboard

kubectl get secret $(kubectl get serviceaccount dashboard -o jsonpath="{.secrets[0].name}") -o jsonpath="{.data.token}" | base64 --decode
```
### For gitlab
```
apiVersion: v1
kind: ServiceAccount
metadata:
  name: gitlab
  namespace: default
```

```
kind: ClusterRoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: gitlab-cluster-admin
subjects:
- kind: ServiceAccount
  name: gitlab
  namespace: default
roleRef:
  kind: ClusterRole
  name: cluster-admin
  apiGroup: rbac.authorization.k8s.io

kubeadm token create
```
 
 ## JOIN cluster
```
 kubeadm token create --print-join-command
```
 
  Install kubernetes and join master as slave
 
 kubeadm join (add) --node-name=<HOST_NAME>
 
 systemctl restart systemd-logind.service
