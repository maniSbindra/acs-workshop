# Exercise to go through some basic k8s resources, commands and concepts

## Use the following container images depending on whether you are using linux or windows agents
* For K8s cluster with **linux agents** use {container-image} = tutum/hello-world. (In the following steps of this exercise **replace {container-image} with tutum/hello-world** )
* For K8s cluster with **windows agents** use {container-image} = maninderjit/asp.net:0.2. (In the following steps of this exercise **replace {container-image} with maninderjit/asp.net:0.2**)

## Get basic information about the kubernetes cluster, and information about the nodes
```sh
# Get cluster information
kubectl cluster-info

# Check status of different kubernetes components
kubectl get componentstatuses

# Get Details of Nodes in the cluster
kubectl get nodes
```

## Create deployment and Pods for web application, remember to replace {container-image} with the actual image as shown above
```sh
# Create deployment and pods
kubectl run webapp --image={container-image} --port=80

# view the deployment
kubectl get deployments

# view the pod/s.
kubectl get pods
# pod name will be of the form webapp-XXXXXXX-XX

# view the nodes on which the pods are scheduled
kubectl get pods -o wide
# before moving to the next step wait for the pods state to change to running. This will take longer for the windows container as the image size is large, which causes the initial image pull to take longer
```

## Expose the Deployment so using service of type Loadbalancer. Once public IP is available for the service, access it using the browser. You should see a website which displays the hostname/machine name for the web container.
```sh
# expose deployment as service
kubectl expose deployment webapp --port=80 --type=LoadBalancer

# Get Details of Service
kubectl get services

# watch service till we get a public ip. After status changes from pending and you a public ip for the service, hit that public ip from the browser. You can terminate the watch on this command using ctrl + c
kubectl get services -w
```


## Scale the deployment to 3 pods. Doing refresh (ctrl + F5) of the browser after this should show you 3 different machine names
```sh
## scale the deployment
kubectl scale --replicas=3 deployment/webapp

## have a look at the deployment
kubectl get deployment webapp

## view the pods and which nodes they are scheduled to
kubectl get pods -o wide -w

## Refresh browser (ctrl + f5)
```

