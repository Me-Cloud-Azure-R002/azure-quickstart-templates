---
title: Kubernetes Architecture
description: ""
date: 2022-07-03T22:14:42.017Z
preview: ""
draft: ""
tags: ""
categories: k8s-architecture
lastmod: 2022-07-12T17:26:56.337Z
---

# AT implementation 

My Implementation of the AKS template is based on the following Azure templates & its parameters
[Reference - azure.microsoft.com](https://azure.microsoft.com/en-us/resources/templates/aks-vmss-systemassigned-identity/)

```bash

az group create --name rg-k8s-cluster-0001 --location centralindia #use this command when you need to create a new resource group for your deployment
az group deployment create --resource-group rg-k8s-cluster-0001 --template-file azuredeploy.json --parameters aksClusterName=k8s-cluster-0001 dnsPrefix=amtyagi

```

## To connect to the solution

The template deployment will output `controlPlaneFQDN` value while will be the Kubernetes API endpoint for the cluster.

### My Output

```
Outputs:
Name                Type                       Value
==================  =========================  ==========
controlPlaneFQDN    String                     #{Your DNS Prefix}#-a38a5fa0.hcp.#{AksResourceLocation}#.azmk8s.io)
My Output            My Output                    amtyagi-f73e5a8a.hcp.centralindia.azmk8s.io
```

## To manage the solution

To get your credentials for your kubectl-cli you can use the Azure CLI command:

```bash
az aks get-credentials --name k8s-cluster-0001 --resource-group rg-k8s-cluster-0001
```
