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



## Set up ingress for ray dashboard

