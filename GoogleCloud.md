1. Make sure that Container Registry is enabled. Billing is required.

2. Configured Docker to use gcloud as a credential helper, or are using another authentication method. To use gcloud as the credential helper, run the command:

	gcloud auth configure-docker
	
3. Tag the local image with the registry name by using the command:

	docker tag [SOURCE_IMAGE] [HOSTNAME]/[PROJECT-ID]/[IMAGE]
	
	
	docker tag bootkemp/car-showroom asia.gcr.io/apps-bc4f3/car-showroom
	
4. Verify Tagging:


	docker image ls

REPOSITORY                           TAG                 IMAGE ID            CREATED             SIZE
bootkemp/car-showroom                latest              9a831050ba04        14 hours ago        127MB
asia.gcr.io/apps-bc4f3/car-showroom   latest              9a831050ba04        14 hours ago        127MB

5. Push the tagged image to Container Registry

	docker push asia.gcr.io/apps-bc4f3/car-showroom
	
6. Now go to the "Storage" in the GCP Console.


7. Click the artifacts.[PROJECT-ID].appspot.com or [REGION].artifacts.[PROJECT-ID].appspot.com bucket's link.

8. Select the Permissions tab.

9. Click Add members. provide your gmail id.

10. From the Select a role drop-down menu's Storage category, select Storage Object Viewer. Click Add.

    Using gsutil:
    
    
    gsutil iam ch [TYPE]:[EMAIL-ADDRESS]:objectViewer gs://[BUCKET_NAME]
    
    link: https://cloud.google.com/container-registry/docs/access-control
    
11. Run gcloud container images list-tags to view the image's tag(s) and automatically-generated digest:

	gcloud container images list-tags [HOSTNAME]/[PROJECT-ID]/[IMAGE]


	Example: gcloud container images list-tags asia.gcr.io/apps-bc4f3/car-showroom


    The output will be like following:
    
	C:\spring-server-car-showroom>gcloud container images list-tags asia.gcr.io/apps-bc4f3/car-showroom
	DIGEST        TAGS    TIMESTAMP
	34f194bb85ea  latest  2019-06-06T20:34:45


12. To pull from Container Registry, use the command:

	docker pull [HOSTNAME]/[PROJECT-ID]/[IMAGE]:[TAG]
	
13. To run the docker container 

	To test your container image using your local Docker engine, run the following command:

	docker run --rm -p 8000:8050 asia.gcr.io/apps-bc4f3/car-showroom

13. Clean up

	To avoid incurring charges to your GCP account for the resources used in this quickstart:

	Run the following command to delete the Docker image from Container Registry.

	gcloud container images delete asia.gcr.io/apps-bc4f3/car-showroom --force-delete-tags

	

