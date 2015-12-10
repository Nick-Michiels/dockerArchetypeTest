#Basic Example Java Docker Project

This java docker project prints the java version of the java:8 docker container

We use the docker-maven-plugin from spotify which can be used to create a Docker image with artifacts built from your Maven project.

You can package and build an image with the default configuration by running this command. Building will automatically trigger when packaging.

	mvn clean package 

To deploy and push the image:

	mvn clean deploy

On Windows, by default, the plugin will try to connect to docker on ```localhost:2375```. Set the DOCKER_HOST environment variable to connect elsewhere.

	DOCKER_HOST=tcp://<host>:2375

On Unix this would be ```unix:///var/run/docker.sock```

To remove the image named foobar run the following command:

	mvn docker:removeImage -DimageName=foobar

Commits to the master branch will trigger the continuous integration agent to build the jar and release by uploading to Sonatype. If you are a project maintainer with the necessary credentials, you can also build and release locally by running the below.

	mvn release:clean
	mvn release:prepare
	mvn release:perform

For more information about this plugin, please visit its [GitHub repository](https://github.com/spotify/docker-maven-plugin).

If you'd like to manually run the image:

	docker run -it --rm --name my-running-app my-java-app

Located in ```src/main/docker```, there is a Dockerfile. In the Dockerfile, there are a number of useful example commands.