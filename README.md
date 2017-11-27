#  Mendix Azure-VSTS-Kubernetes CI/CD Reference Implementation

The Mendix Azure-VSTS-Kubernetes CI/CD Reference Implementation is a reference implementation for running a cluster of Mendix runtime instances by setting up a managed Kubernetes cluster on Azure. The Kubernetes cluster will use Docker containers built using the [Mendix Docker buildpack](https://github.com/mendix/docker-mendix-buildpack). The build and deployment of containers on the cluster is orchestrated using Microsoft Visual Studio Team Services.

**We also have a Reference Implementation available using Jenkins as CI/CD platform. This implementation is described [here](https://github.com/MXClyde/azure-kubernetes-cicd-reference-impl-jenkins/)**

# Video tutorial

[![Deploy your own Kubernetes-based Mendix cluster on Microsoft Azure](http://img.youtube.com/vi/uDaMPPy9Wa/0.jpg)](http://www.youtube.com/watch?v=uDaMPPy9Wa "Deploy your own Kubernetes-based Mendix cluster on Microsoft Azure")

# Scope of the Reference Implementation

![Scope of the Reference Implementation](/images/scope_r.png)

# Technical Architecture of the Reference Implementation

![Technical Architecture of the Reference Implementation](/images/arch_r.png)

# Commands used in video how-to

This section lists the commands used during the video how-to for easy copy-pasting:

Check version of the Azure CLI:

```
az --version
```
Login to Azure:

```
az login
```

Set feature flag to enable AKS preview:

```
az provider register -n Microsoft.ContainerService
```

Create a Resource Group:

```
az group create --name mx-cicd-ref-impl --location centralus
```

Create AKS Cluster:

```
az aks create --resource-group mx-cicd-ref-impl --name mx-cicd-ref-impl-cluster --node-count 1 --generate-ssh-keys
```
Install local Kubernetes Command-Line client:
```
az aks install-cli
```
Retrieve cluster credentials:
```
az aks get-credentials --resource-group mx-cicd-ref-impl --name mx-cicd-ref-impl-cluster
```

Create tunnel to access Kubernetes Dashobard:
```
az aks browse --resource-group mx-cicd-ref-impl --name mx-cicd-ref-impl-cluster
```

Create namespace mendixapps:

```
kubectl create namespace mendixapps
```
Shell Script to download Mendix Docker Build Pack (part of build pipeline)

```
wget https://github.com/mendix/docker-mendix-buildpack/archive/master.zip
unzip master.zip
mv  docker-mendix-buildpack-master/* .
rm -R  docker-mendix-buildpack-master
```

Build Arguments (during Build Docker Image step of Build Pipeline
```
BUILD_PATH=trunk
```

Additional Image Tags (during Build Docker Image and Push Docker Image steps of Build Pipeline
```
$(Build.BuildNumber)
```

Artifact name during Publish Build Artifacts (build pipeline)
```
Kubernetes_Config_$(Build.SourceBranch)_$(Build.SourceVersion)_$(Build.BuildNumber)
```

Change context of kubectl to namespace mendixapps:

```
kubectl config set-context $(kubectl config current-context) --namespace=mendixapps
```

Location of Kubernetes manifest for kubectl apply command argument (substitute last part of path with):

```
Kubernetes_Config_$(Build.SourceBranch)_$(Build.SourceVersion)_$(Build.BuildNumber)/kubernetes.yaml
```

# Questions / Feedback / Suggestions / Contributions

Please open an issue or submit a pull request against this repository to provide your input.
