# jenkins-with-docker

Adds docker client to jenkins/jenkins:lts to allow it to build docker containers. Need to share /var/run/docker.sock from the host.

My host is running Ubuntu, so that seemed to create the docker group as 117 but debian seemed to create it as 999, so I have to change the group id to match the host as well as add the jenkins user to the group

So you need to run it with something like this

    docker run \
       -d \
       --restart=unless-stopped \
       -p 8080:8080 \
       -p 50000:50000 \
       -v /var/run/docker.sock:/var/run/docker.sock \
       martinjohn/jenkins-with-docker
