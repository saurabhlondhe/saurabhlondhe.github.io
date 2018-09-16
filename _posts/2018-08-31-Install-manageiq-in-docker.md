---
layout: post
title:  "ManageIQ Installation in Docker"
date:   2018-08-31
desc: "ManageIQ image pull in Docker and using ManageIQ instance"
keywords: "manageiq,hybridcloud,gh-pages,website,blog,docker"
categories: [Project,Open_Source,Linux]
tags: [manageiq,docker,open source]
icon: icon-docker
---

Docker image for ManageIQ is available. It can be run in Docker container. There are also other options like [Public cloud](http://manageiq.org/docs/get-started/cloud) or [Vagrant](http://manageiq.org/docs/get-started/vagrant) to get started with ManageIQ. It can run everywhere Docker is available.

First thing, you have to install Docker in your system. Follow instructions in [Docker docs](https://store.docker.com/search?type=edition&offering=community) to install Docker.

Start Docker service using

    sudo service docker start 

or do 

    systemctl start docker 

---
### Step 1: Pull Docker image of ManageIQ

    sudo docker pull manageiq/manageiq 

or

    sudo docker pull manageiq/manageiq:gaprindashvili-4 

It will download ManageIQ image from Docker registry. To see image list, run this

    sudo docker images ls 

---
### Stpe 2: Run Docker container

    sudo docker run --privileged -d -p 8443:443 manageiq/manageiq 

or

    sudo docker run --privileged -d -p 8443:443 manageiq/manageiq:gaprindashvili-4 


It will run container in detached mode. ``` -p 8443:443``` will forward your base machine's _8443_ port requests to docker container's _443_ port. To see a list of running containers, execute


    sudo docker ps 


Now ManageIQ container is up and running at IP address [https://127.0.0.1:8443](https://127.0.0.1:8443)

It has username as *admin* and the password is *smartvm*. Get the login and explore the world of ManageIQ.

---
### Step 3: To commit the changes Commit the container

It can be useful to commit a container’s file changes or settings into a new image. This allows you to debug a container by running an interactive shell, or to export a working dataset to another server. 

    docker commit "container_id" manageiq
    
this saves all changes and data, next time run the ``` manageiq``` container.

Reference: http://manageiq.org/docs/get-started/docker