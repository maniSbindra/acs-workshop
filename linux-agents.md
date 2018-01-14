# Instructions to create ACS k8s cluster with linux agents

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
az group create -n acs-workshop-rg -l southeastasia
```

## Create ACS k8s cluster with linux agents
```sh
az acs create -n acs-workshop-linux -g acs-workshop-rg  --orchestrator-type=kubernetes --generate-ssh-keys
```

## Get ACS K8s Credentials
```sh
az acs kubernetes get-credentials -n acs-workshop-linux -g acs-workshop-rg
```