#  Mendix Azure-VSTS-Kubernetes CI/CD Reference Implementation

The Mendix Azure-VSTS-Kubernetes CI/CD Reference Implementation is a reference implementation for running a cluster of Mendix runtime instances by setting up a managed Kubernetes cluster on Azure. The Kubernetes cluster will use Docker containers built using the [Mendix Docker buildpack](https://github.com/mendix/docker-mendix-buildpack). The build and deployment of containers on the cluster is orchestrated using Microsoft Visual Studio Team Services.

**We also have a Reference Implementation available using Jenkins as CI/CD platform. This implementation is described [here](https://github.com/MXClyde/azure-kubernetes-cicd-reference-impl-jenkins/)**
