# Minikube

## To start minikube with virtual-box virtuliazation tool use: `minikube start --no-vtx-check`

## management commands:

1) `minikube ssh`
Enter virtual machine/cluster
username: docker
password: tcuser

2) `minikube start/stop/delete`
Starts, stops or deletes VM with k8s cluster

3) `minikube start --cpus=4 --memory=8gb --disk-size=5gb`
Starts VM with k8s cluster using configured pc resources

4) `minikube start -p MYSUPERCLUSTER`
Starts VM with k8s cluster with our name

## Kubectl

## Management commands: 
1) `kubectl version`

2) `kubectl version --client`

3) `kubectl get componentstatuses`
Shows state of K8s cluster

4) `kubectl cluster-info`
Shows info about K8s cluster

5) `kubectl get nodes`
Shows all servers of K8s cluster