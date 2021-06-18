# Notes


## Setting up the k8s-helm chart

We are using helm 3.6.x version to install ray on minikube k8s node. 

1. Follow the directions and it works well, update relevant parts of the helm charts. 
1. 


How does it create redis?  What is redis?  
Remote Dictionary Server, used in-memory key-value data store (stores in memory not on disk, important distinction)
What makes it different from normal database.


## Testing the Ray client and using the cluster

ValueError: Failed to look up actor with name 'abc'. You are either trying to look up a named actor you didn't create, the named actor died, or the actor hasn't been created because named actor creation is asynchronous.

raise cloudpickle.loads(ticket.error)

I was able to connect to the ray client from inside the cluster, by using a k8s resource called a job. 
But I wasn't able to connect to the ray client externally by port-forward or without port-forward because my k8s cluster
is on my laptop, so I should be able to access the endpoint from the actual internal cluster IP endpoint. 

I don't know why but I can't see a way to connect to this.  
There is this cloudpickle error
difference between ray.client("addres").connect() and ray.connect("address")



I should try an ingress to connect externally 



## Set up ingress for ray dashboard


## Set up ingress for ray client


## What is the Ray client? 

It is in the util library for python.  so I guess it is a separate library, but it allows you to connect to the ray cluster.

pickling protocol that is used for data transfer in between the ray client and the ray 

## Endpoint in k8s services

They are the cluster ip for k8 pods.  So the service shows an endpoint which is the IP for a pod.  

## Creating a Ray Server
How do we do this?  
You can create a ray server

Is this different from ray serve?  What is ray serve?  

## 