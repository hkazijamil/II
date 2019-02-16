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
nano /etc/systemd/system/kubelet.service.d/10-kubeadm.conf
```
and paste this

```
Environment="cgroup-driver=systemd/cgroup-driver=cgroupfs"
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
sudo cp -rf /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
export KUBECONFIG=/etc/kubernetes/admin.conf

kubectl apply -f https://docs.projectcalico.org/v3.3/getting-started/kubernetes/installation/hosted/rbac-kdd.yaml
kubectl apply -f https://docs.projectcalico.org/v3.3/getting-started/kubernetes/installation/hosted/kubernetes-datastore/calico-networking/1.7/calico.yaml

kubectl create -f https://raw.githubusercontent.com/kubernetes/dashboard/master/aio/deploy/recommended/kubernetes-dashboard.yaml

kubectl create serviceaccount dashboard -n default
kubectl create serviceaccount calico-node -n kube-system
kubectl create clusterrolebinding dashboard-admin -n default --clusterrole=cluster-admin --serviceaccount=default:dashboard

kubectl describe services kubernetes-dashboard --namespace=kube-system

kubectl cluster-info

kubectl get svc --namespace kube-system

kubectl -n kube-system edit service kubernetes-dashboard
kubectl -n kube-system get service kubernetes-dashboard

kubectl get pods -o wide --all-namespaces

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
 ```
 systemctl restart systemd-logind.service
 ```


## Convert Deployment yaml
```
# Linux
curl -L https://github.com/kubernetes/kompose/releases/download/v1.16.0/kompose-linux-amd64 -o kompose

# macOS
curl -L https://github.com/kubernetes/kompose/releases/download/v1.16.0/kompose-darwin-amd64 -o kompose

# Windows
curl -L https://github.com/kubernetes/kompose/releases/download/v1.16.0/kompose-windows-amd64.exe -o kompose.exe

chmod +x kompose
sudo mv ./kompose /usr/local/bin/kompose
```

## Auto deploy with kompose

kompose --file <FILE_PATH> --namespace=<PROJECT_NAME_NAMESPACE> up  
kompose --file <FILE_PATH> --namespace=<PROJECT_NAME_NAMESPACE> down
### Create Namespace
```
apiVersion: v1
kind: Namespace
metadata:
  name: <insert-namespace-name-here>
```
```
kubectl create serviceaccount <insert-serviceaccount-name-here> -n <insert-namespace-name-here>
```
```
kubectl get secrets regcred

kubectl get secret regcred --output="jsonpath={.data.\.dockerconfigjson}" | base64 --decode

kubectl patch serviceaccount <insert-serviceaccount-name-here> -n <insert-namespace-name-here> -p '{"imagePullSecrets": [{"name": "regcred"}]}'
```
#### NB: secrect need to be created inside namespace to patch with service accout of namepsace




