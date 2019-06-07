1. Using the gcloud command line tool, install the Kubernetes command-line tool. kubectl is used to communicate with Kubernetes, which is the cluster orchestration system of GKE clusters:

	gcloud components install kubectl
	
2. Set project id and Zone:

	gcloud config set project [PROJECT_ID]
	gcloud config set compute/zone us-central1-b
	
	Example: 
	  
	  gcloud config set project apps-bc4f3
	  gcloud config set compute/zone asia-south1

2. Run the following command to create a two-node cluster named hello-cluster:

	gcloud container clusters create hello-cluster --num-nodes=2
	
3. To  check working instances:

	gcloud compute instances list
	
4. To resize a cluster's node pools, run the following command:

	gcloud container clusters resize [CLUSTER_NAME] --node-pool [POOL_NAME] \
    --num-nodes [NUM_NODES]
    
    example: 
    
    gcloud container clusters resize hello-cluster --num-nodes 2
    
5. Run the following command to deploy your application, listening on port 8080:

	kubectl run car-showroom --image=asia.gcr.io/apps-bc4f3/car-showroom --port 8000