# Instructions to create ACS k8s cluster with windows agents

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


<!-- ## Create Service Principal and get clientid and clientsecret
```sh
``` -->

## Create resource group
```sh
az group create -n acs-workshop-win-rg -l southeastasia
```

## Register required providers with subscription
```sh
az provider show -n Microsoft.Network -o table
# if Microsoft.Network not registered then register it
az provider register -n Microsoft.Network

az provider show -n Microsoft.Compute -o table
# if Microsoft.Compute not registered then register it 
az provider register -n Microsoft.Compute
```

## Create ACS k8s cluster with windows agents. Please do change the windows agent machine password (--admin-password value).
```sh
az acs create -n acs-workshop-windows -g acs-workshop-win-rg  --orchestrator-type=kubernetes --generate-ssh-keys --windows --admin-username azureuser --admin-password myDiffiCultp@ssword
```

## If you do not have kubectl installed execute the following command - kubectl is already available with Azure Cloud Shell as a result this step is not needed for Azure Cloud Shell, only needed if you have installed Azure CLI on your dev machine and you do not have kubectl installed
```sh
az acs kubernetes install-cli
```

## Get ACS K8s Credentials for the provisioned cluster
```sh
az acs kubernetes get-credentials -n acs-workshop-windows -g acs-workshop-win-rg
```

## Follow the instructions mentioned in  [exercise](./k8s-exercise.md)