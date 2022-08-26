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
<br/>
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

6) `kubectl run <pod_name> --image=<image_name> --port=<port_value>`

Creates pod and starts it pulling the image and then starting a container

7) `kubectl delete pods <pod_name>`

Deletes specified pod by name

8) `kubectl get pods -o wide`

Shows detailed info about all pods

9) `kubectl describe pods <pod_name>`

Show full info about specified pod

10) `kubectl exec -it <pod_name> <command>`

Executes command in a specified pod, flag '-it' is optional

11) `kubectl logs <pod_name>`
Shows all logs of the specified pod

12) `kubectl port-forward <pod_name> <host-port>:<cluster-port>`

Mapps cluster port to host port so we can access our app in the specified pod
Example: `kubectl port-forward hello-pod 8000:3000` - now we can access localhost:8000 and this will point to pod's 3000 port

## Creating pods from manifest yaml file
Yaml example: 
```
apiVersion: v1
kind: Pod
metadata:
  name: hello-pod
spec:
  containers:
    - name: container-express
      image: lumineks/kuber:latest
      ports:
        - containerPort: 3000
```
### Command to create pod from file - `kubectl apply -f <path_to_file>`

### Command to delete created pod from file - `kubectl delete -f <path_to_file>`

#### We can change 'image' of the pod without redeployment!