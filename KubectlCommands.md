# TheK8sBook hands-on

This guide is based on the book of *Nigel Poulton - The Kubernets book*. It includes commands to manage  K8s clusters.

# kubectl commands

To list all K8s nodes

`kubectl get nodes`

To view the K8s config file 

`kubectl config view`

To show the current context

`kubectl config current-context`

Switch to another context

`kubectl config use-context docker-desktop` 

where docker-desktop is a valid context defined in kubeconfig

To list all possible Pod's attributes

`kubectl explain pods --recursive`

Drill into specific attributes. The following command drills into the restart policy attribute of a Pod object.

`kubectl explain pod.spec.restartPolicy`

Create Pod from a manifest file

`kubectl apply -f ./pod.yml`

To delete the resources created by the YAML manifest file

`kubectl delete -f ./pod.yml`

To get the running Pods or Services

`kubectl get pods`

`kubectl get svc`

To get more detailed information about the Pod you can use one of the following commands

`kubectl get pods -o wide`

`kuebctl get pods -o yaml`

If you want to better introspect the pod use the describe command

`kubectl describe pods hello-pod`

To enter in the container and open a shell

`kubectl exec -it hello-pod -- sh`

To delete a all pods and respective services

`kubectl delete pods`

`kubectl delete svc`

List all namespaces

`kubectl get ns`

Set the default namespace against which to execute the commands and not providing it in the parameters every time

`kubectl config set-context --current --namespace shield`

Get information about the deployed ingress

`kubectl get ing`

Get a list of all available Kubernetes resources

`kubectl api-resources`

List all available storage classes provided by your cloud operator (in case Kubernetes was hosted in a cloud)

`kubectl get sc`

# ConfigMaps

Get all config maps

`kubectl get cm`

Create a ConfigMap from file

`kubectl create cm testmap2 --from-file cmfile.txt`

Get the ConfigMap as YAML file

`kubectl get cm testmap2 -o yaml`



# Deployments

Inspecting deployment

`kubectl get deploy hello-deploy`

`kubectl describe deploy hello-deploy`

Inspect the replica set

`kubectl get rs`

Then use the returned replica set to describe it

`kubectl describe rs hello-deploy-bb4cf4dd4`

To monitor the upgrading progress

`kubectl rollout status deployment hello-deploy`

To see the history of specific deployment upgrades

`kubectl rollout history deployment hello-deploy`

To delete a deployment

`kubectl delete -f ./deploy.yaml`

# Services

# High availability

Check the HPA profile

`kubectl get hpa`


# Endpoints

Get available endpoints

`kubectl get endpoints`




# K3D create cluster 

`$ k3d cluster create tkb \
--servers 1 \
--agents 3 \
--image rancher/k3s:latest`

The --servers 1 flag creates a single control plane node, the --agents 3 flag creates 3
worker nodes, and the --image rancher/k3s:latest creates the cluster based on the
most recent Kubernetes image available.

# KinD create cluster

This will create a K8s cluster by passing a YML configuration file to the API server simulating a closer real world scenario 

1. Navigate to the downloaded repository Thek8sBook
2. CD to installation
3. Run the command

`kind create cluster --config=kind.yml`






