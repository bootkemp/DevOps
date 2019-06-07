Below are some dockerfile commands you must know:

Reference: https://docs.docker.com/engine/reference/builder/

FROM

	The base image for building a new image. This command must be on top of the dockerfile.


MAINTAINER

	Optional, it contains the name of the maintainer of the image.

RUN

	Used to execute a command during the build process of the docker image.

ADD

	Copy a file from the host machine to the new docker image. There is an option to use an URL for the file, docker will then download that file to the destination directory.

ENV

	Define an environment variable.

CMD

	Used for executing commands when we build a new container from the docker image.


ENTRYPOINT

	Define the default command that will be executed when the container is running.


WORKDIR

	This is directive for CMD command to be executed.

USER

	Set the user or UID for the container created with the image.

VOLUME

	Enable access/linked directory between the container and the host machine.


Example:


	FROM python:3.7-alpine 	--> Build an image starting with the Python 3.7 image.
	WORKDIR /code		--> Set the working directory to /code.
	ENV FLASK_APP app.py	--> Set environment variables used by the flask command.
	ENV FLASK_RUN_HOST 0.0.0.0	--> Set environment variables used by the flask command.
	RUN apk add --no-cache gcc musl-dev linux-headers	--> Install gcc so Python packages such as MarkupSafe and SQLAlchemy can compile speedups.
	COPY requirements.txt requirements.txt	--> Copy requirements.txt and install the Python dependencies.
	RUN pip install -r requirements.txt  
	COPY . . --> Copy the current directory . in the project to the workdir . in the image.
	CMD ["flask", "run"] --> Set the default command for the container to flask run.
	This tells Docker to:

