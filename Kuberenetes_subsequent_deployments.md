Deploy a new version of your app

You can create an image for the next version of your application by building the image and tagging it as v2 

	
	docker tag bootkemp/car-showroom asia.gcr.io/apps-bc4f3/car-showroom:v2
	

Then push the image to the Google Container Registry:

	
	docker push asia.gcr.io/apps-bc4f3/car-showroom:v2


Now, apply a rolling update to the existing deployment with an image update:

	
	kubectl set image deployment/car-showroom car-showroom=asia.gcr.io/apps-bc4f3/car-showroom:v2
	
	
To check updated image:

	kubectl describe pods


It will print like following:

	Name:               car-showroom-756b994fb-6pzbq
	Namespace:          default
	Priority:           0
	PriorityClassName:  <none>

	Controlled By:      ReplicaSet/car-showroom-756b994fb
	Containers:
	  car-showroom:
	    Container ID:
	    Image:          asia.gcr.io/apps-bc4f3/car-showroom:v2
	    Image ID:
	    Port:           8050/TCP
	    Host Port:      0/TCP
	    State:          Waiting
	      Reason:       ImagePullBackOff
	    Ready:          False

