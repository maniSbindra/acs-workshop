# This repository has instructions to create ACS Kubernetes (K8s) Cluster, and understand basic kubernetes resources and commands

## Azure Command Line Interface (Azure CLI) is required for the rest of this exercise. Azure Cloud shell already has Azure CLI configured. You can access Azure cloud shell through the azure portal (portal.azure.com). The [article](https://docs.microsoft.com/en-us/azure/cloud-shell/overview) shows how to initiate the Azure cloudshell (with screenshots). Alternately you can install Azure CLI on your local machine from [Install Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)

## Install kubectl by following instructions at [install kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

## Create K8s cluster
* To create K8s cluster with Linux Agents follow instructions in [Linux Agents](./linux-agents.md)

* To create K8s cluster with Windows Agents follow instructions in [Windows Agents](./win-agents.md)

## Once required cluster is created complete the [exercise](./k8s-exercise.md) which will take you through the most common k8s resources and commands