# Private Build and Release Agent for Mendix (VM ARM Template)

This ARM template can be used to deploy a Virtual Machine (i.e. Docker host) that will host a VSTS agent container compatible for use with Mendix (i.e. capable of executing the Mendix Docker Build Pack). 

This ARM template can be used in situations where the Microsoft Hosted Linux VSTS agents do not suffice. For example when deploying to Kubernetes clusters which are not reachable from the public internet.
