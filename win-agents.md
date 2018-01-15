# Instructions to create ACS k8s cluster with windows agents

## login
```sh
az login
```

## List associated subscriptions
```sh
az account list
```

## set account if more than 1 subscription associated with login 
```sh
az account set --subscription <subscription id>
# verify correct account is set 
# az account show
```

## Create resource group
```sh
az group create -n acs-workshop-win-rg -l southeastasia
```

## Create ACS k8s cluster with windows agents
```sh
az acs create -n acs-workshop-windows -g acs-workshop-win-rg  --orchestrator-type=kubernetes --generate-ssh-keys
```

## If you do not have kubectl installed execute the following command
```sh
az acs kubernetes install-cli
```

## Get ACS K8s Credentials for the provisioned cluster
```sh
az acs kubernetes get-credentials -n acs-workshop-windows -g acs-workshop-win-rg
```

## Follow the instructions mentioned in  [exercise](./k8s-exercise.md)