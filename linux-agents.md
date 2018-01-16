# Instructions to create ACS k8s cluster with linux agents

## login - this step is not needed for Azure Cloud Shell, only needed if you have installed Azure CLI on your dev machine
```sh
az login
```

## List associated subscriptions - this step is not needed for Azure Cloud Shell, only needed if you have installed Azure CLI on your dev machine
```sh
az account list
```

## set account if more than 1 subscription associated with login - this step is not needed for Azure Cloud Shell, only needed if you have installed Azure CLI on your dev machine
```sh
az account set --subscription <subscription id>
# verify correct account is set 
# az account show
```

## Create resource group
```sh
az group create -n acs-workshop-rg -l southeastasia
```

## Create ACS k8s cluster with linux agents
```sh
az acs create -n acs-workshop-linux -g acs-workshop-rg  --orchestrator-type=kubernetes --generate-ssh-keys
```

## If you do not have kubectl installed execute the following command - kubectl is already available with Azure Cloud Shell as a result this step is not needed for Azure Cloud Shell, only needed if you have installed Azure CLI on your dev machine and you do not have kubectl installed
```sh
az acs kubernetes install-cli
```

## Get ACS K8s Credentials for the provisioned cluster
```sh
az acs kubernetes get-credentials -n acs-workshop-linux -g acs-workshop-rg
```

## Follow the instructions mentioned in  [exercise](./k8s-exercise.md)