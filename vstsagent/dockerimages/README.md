# Dockerfile for Mendix-compatile VSTS agent

This Dockerfile was used to create a VSTS agent with support for Docker-in-Docker and Subversion.
It is dervied from the vsts-agent Docker images provided by Microsoft (microsoft/vsts-agent).
The resulting image is available on Docker Hub (mxclyde/vstsagent) and used in the ARM template for the VSTS build agent in the
Mendix CI/CD Reference Implementation (VSTS Flavour)
