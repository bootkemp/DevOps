Common Docker Commands that will be used in workhop:

Commands for creating Docker:

	docker build -t bootkemp/car-showroom .

or
	mvn install dockerfile:build -Dmaven.test.skip=true -- > Causing issues with Spotify Plug-in
	
Now You can now see the list of all the docker images on your system using the following command -

	$ docker image ls
	
To Start Docker:

	docker run -p 8080:8080 -t bootkemp/car-showroom
	
To Check Docker Processes:

	docker ps
	
To stop docker:

	docker stop <Container ID (available from 'docker ps')>
	
To execute command on Docker Instance:

	docker exec -it <Names (available from 'docker ps')> ls
