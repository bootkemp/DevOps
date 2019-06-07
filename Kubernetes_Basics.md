Reference: https://kubernetes.io/docs/tutorials/kubernetes-basics/explore/explore-intro/

Pods 
				
	A pod is a group of one or more Docker containers. 		 	 	 		
			
	Kubernetes orchestrates, schedules, and manages pods. When we refer to an application running inside of Kubernetes, it’s running within a Docker container inside of a pod. A pod is given its own IP address, and all containers within the pod share this IP (which is different from plain Docker, where each container gets an IP address). When volumes are mounted to the pod, they are also shared between the individual Docker containers running in the pod. 

	Note: 	Pods can be destroyed at any point.  

Nodes


	A Pod always runs on a Node. A Node is a worker machine in Kubernetes and may be either a virtual or a physical machine, depending on the cluster. Each Node is managed by the Master. A Node can have multiple pods, and the Kubernetes master automatically handles scheduling the pods across the Nodes in the cluster. The Master's automatic scheduling takes into account the available resources on each Node.

	Every Kubernetes Node runs at least:
	
	Kubelet: a process responsible for communication between the Kubernetes Master and the Node; it manages the Pods and the containers running on a machine.
	
	A container runtime (like Docker, rkt) :  Responsible for pulling the container image from a registry, unpacking the container, and running the application.
	Containers should only be scheduled together in a single Pod if they are tightly coupled and need to share resources such as disk.
	

Labels
					
	Labels are simple key/value pairs that we can assign to pods like release=stable or tier=backend. Pods can have multiple labels that group and categorize in a loosely coupled fashion.

	Labels are used for replication controllers and services. 

		 	 	 		
Replication Controllers
					
	Kubernetes has a concept called ReplicationController that manages the number of replicas for a given set of microservices. For example, let’s say we wanted to manage the number of pods labeled with tier=backend and release=stable. We could create a replication controller with the appropriate label selector and then be able to control the number of those pods in the cluster with the value of replica on our ReplicationController. 
				
Services
					
	It allows us to use a label selector to group our pods and abstract them with a single virtual (cluster) IP that we can then use to discover them and interact with them. 
