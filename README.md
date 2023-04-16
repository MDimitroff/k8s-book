# TheK8sBook hands-on

This guide is based on the book of Nigel Poulton - The Kubernets book. It includes commands to manage  K8s clusters.

## kubectl commands
---

To list all K8s nodes

`kubectl get nodes`

To view the K8s config file 

`kubectl config view`

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






