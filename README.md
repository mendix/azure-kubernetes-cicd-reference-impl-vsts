#  Mendix Azure-VSTS-Kubernetes CI/CD Reference Implementation

The Mendix Azure-VSTS-Kubernetes CI/CD Reference Implementation is a reference implementation for running a cluster of Mendix runtime instances by setting up a managed Kubernetes cluster on Azure. The Kubernetes cluster will use Docker containers built using the [Mendix Docker buildpack](https://github.com/mendix/docker-mendix-buildpack). The build and deployment of containers on the cluster is orchestrated using Microsoft Visual Studio Team Services.

**We also have a Reference Implementation available using Jenkins as CI/CD platform. This implementation is described [here](https://github.com/MXClyde/azure-kubernetes-cicd-reference-impl-jenkins/)**

# Video how-to

Video will follow

# Scope of the Reference Implementation

# Technical Architecture of the Reference Implementation

# Commands used in video how-to

This section lists the commands used during the video how-to for easy copy-pasting:

Become root on the shell
```
sudo -i
```

Check version of the Azure CLI

```
az --version
```
Login to Azure

```
az login
```

Set feature flag to enable AKS preview

```
az provider register -n Microsoft.ContainerService
```

Create a Resource Group

```
az group create --name mx-cicd-ref-impl --location centralus
```

Create AKS Cluster

```
az aks create --resource-group mx-cicd-ref-impl --name mx-cicd-ref-impl-cluster --node-count 1 --generate-ssh-keys
```
