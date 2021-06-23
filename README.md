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

## Getting this to work


ray.init(address="auto")
2021-06-21 15:14:02,862	INFO worker.py:726 -- Connecting to existing Ray cluster at address: 172.17.0.10:6379

What does this mean?  What is it doing, it is trying to connect to an existing ray cluster at this address apparently.  Notice it is using the endpoint for my ray cluster and the port for the redis server from the head node.  


Exception ignored in: <function ClientBaseRef.__del__ at 0x7ffb0cbad4c0>
Traceback (most recent call last):
  File "/home/therealchainman/miniconda3/lib/python3.8/site-packages/ray/util/client/common.py", line 83, in __del__
AttributeError: 'NoneType' object has no attribute 'is_connected'

To clarify for anyone who is looking for what is the difference between the 3 on a simpler level. You can expose your service with minimal ClusterIp (within k8s cluster) or larger exposure with NodePort (within cluster external to k8s cluster) or LoadBalancer (external world or whatever you defined in your LB).

ClusterIp exposure < NodePort exposure < LoadBalancer exposure

ClusterIp
Expose service through k8s cluster with ip/name:port
NodePort
Expose service through Internal network VM's also external to k8s ip/name:port
LoadBalancer
Expose service through External world or whatever you defined in your LB.

