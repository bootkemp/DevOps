Using the gcloud command line tool, install the Kubernetes command-line tool. kubectl is used to communicate with Kubernetes, which is the cluster orchestration system of GKE clusters:

	gcloud components install kubectl
	
Set project id and Zone:

	gcloud config set project [PROJECT_ID]
	gcloud config set compute/zone us-central1-b
	
	Example: 
	  
	gcloud config set project apps-bc4f3
	gcloud config set compute/zone asia-south1

Run the following command to create a two-node cluster named hello-cluster:

	gcloud container clusters create car-showroom-cluster --num-nodes=2
	
To  check working instances:

	gcloud compute instances list
	
To resize a cluster's node pools, run the following command:

	gcloud container clusters resize [CLUSTER_NAME] --node-pool [POOL_NAME] --num-nodes [NUM_NODES]
    
    example: 
    
    	gcloud container clusters resize car-showroom-cluster --num-nodes 2
    
Run the following command to deploy your application, listening on port 8050:

	kubectl run car-showroom --image=asia.gcr.io/apps-bc4f3/car-showroom --port 8050
	

To see the Pod created by the Deployment, run the following command:

	kubectl get pods
	
	kubectl describe pods
	
	
Expose your application to the Internet and setup load balancer

By default, the containers you run on GKE are not accessible from the Internet, because they do not have external IP addresses. 
You must explicitly expose your application to traffic from the Internet, run the following command:

	
	kubectl expose deployment car-showroom --type=LoadBalancer --port 80 --target-port 8050


The kubectl expose command above creates a Service resource, which provides networking and IP support to your application's Pods. 
GKE creates an external IP and a Load Balancer (subject to billing) for your application.

The --port flag specifies the port number configured on the Load Balancer, and the --target-port 
flag specifies the port number that is used by the Pod created by the kubectl run command from the previous step


If you want to find out the external IP that GKE provisioned for your application, you can inspect the Service 
with the the following command:

	kubectl get service
	

