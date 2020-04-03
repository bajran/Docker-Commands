## !! DOCKER !!

You can install docker on Windows, Mac, Linux

Link for docker installation :- 
> [For Mac User](https://docs.docker.com/docker-for-mac/install/)

> [For Windows User](https://docs.docker.com/docker-for-windows/install/)

Before executing commands, make sure that you have login on Docker Hub.
> [Docker Hub](https://hub.docker.com/)

#### Note : For Windows User
##### **If you have operating system with version -> Windows 10 Pro, then you can directly install docker desktop 
##### **If you don't have Windows 10 Pro, then you must install docker-toolbox to run docker on your machine

#### Commands

``` 
> docker version 
```
> To get the version of docker, which is installed in our system
--------------------------------------------------------
```
> docker pull <container_image>   e.g -> docker pull busybox
```
> It will pull *busybox* image from docker-hub
--------------------------------------------------------
```
> docker run <container_image>   e.g -> docker run busybox
```
> It will check whether it have busybox image in their local image repository, if it does not have this
> the it will go to docker-hub and pull that image to our local image repository and then run that, it 
> happens only once if the image is not their in our local image repository

> You can the different instances of busybox, by providing their version, If you didn't provide any 
> then by default it will take latest version

*for Default latest version, In both cases it will take latest version*
```
> docker run busybox:latest or >docker run busybox
```
*If you need to specify any particular version, **then??** *
```
> docker run busybox:12.0
```
> It will pull the busybox 12.0 version

---------------------------------------------------------
```
> docker ps
```
> To see running the container
----------------------------------------------------------
```
> docker ps --all or docker ps -a
```
> To see all the container
*E.g*
```
> docker ps --all
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                      PORTS               NAMES
efc10b902596        mongo               "docker-entrypoint.s…"   9 minutes ago       Up 9 minutes                27017/tcp           tender_grothendieck
```
----------------------------------------------------------
```
> docker start efc10b902596
```
> Start Container
> If I want to run the mongo container then I need to get the container id, and run the start command

```
> docker stop efc10b902596
```
> Stop Container
> If I want to stop the mongo container then I need to get the container id, and run the stop command

```
> docker rm efc10b902596.
```
> Remove Container
> If I want to completely remove the container , then run the remove command 

```
 > docker ps -all 
```
> To verify whether the image has removed or not, then we need to run above command and check in result whether image has gone or not.
---------------------------------------------------------------

> To check images on our host machine, then run
```
> docker images
```

> It will gives us below result for availabel images on host
```
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
<none>              <none>              e3aec4897168        5 days ago          18.4MB
mongo               latest              bcef5fd2979d        2 weeks ago         386MB
alpine              latest              e7d92cdc71fe        7 weeks ago         5.59MB
busybox             latest              6d5fcfe5ff17        2 months ago        1.22MB
hello-world         latest              fce289e99eb9        14 months ago       1.84kB
```
> And to remove the image, from your host you need to run
```
> docker rmi <REPOSITORY_Name>
```

------------------------------------------------------------------------------

##### Interactive Mode
```
> docker exect -it <container_id>   -> docker exec -it efc10b902596 bash
```
Here *exec* is to execute, *-it* interactive mode. i.e to interact with container image
###### Result -> It will open the container in bash mode for interaction in our case we are interacting with mongo

we get such type of bash prompt
```
root@efc10b902596:/#
```
###### If we enter mongo in that, then will get below result
```
root@efc10b902596:/# mongo
```

#### ----Start O/P----
```
MongoDB shell version v4.2.3
connecting to: mongodb://127.0.0.1:27017/?compressors=disabled&gssapiServiceName=mongodb
Implicit session: session { "id" : UUID("26f27cea-8748-436d-89cb-4de8dae81e2c") }
MongoDB server version: 4.2.3
Server has startup warnings:
2020-03-04T02:31:57.597+0000 I  STORAGE  [initandlisten]
2020-03-04T02:31:57.597+0000 I  STORAGE  [initandlisten] ** WARNING: Using the XFS filesystem is strongly recommended with the WiredTiger storage engine
2020-03-04T02:31:57.597+0000 I  STORAGE  [initandlisten] **          See http://dochub.mongodb.org/core/prodnotes-filesystem
2020-03-04T02:31:59.904+0000 I  CONTROL  [initandlisten]
2020-03-04T02:31:59.904+0000 I  CONTROL  [initandlisten] ** WARNING: Access control is not enabled for the database.
2020-03-04T02:31:59.904+0000 I  CONTROL  [initandlisten] **          Read and write access to data and configuration is unrestricted.
2020-03-04T02:31:59.904+0000 I  CONTROL  [initandlisten]
---
Enable MongoDB's free cloud-based monitoring service, which will then receive and display
metrics about your deployment (disk utilization, CPU, operation statistics, etc).

The monitoring data will be available on a MongoDB website with a unique URL accessible to you
and anyone you share the URL with. MongoDB may use this information to make product
improvements and to suggest MongoDB products and deployment options to you.

To enable free monitoring, run the following command: db.enableFreeMonitoring()
To permanently disable this reminder, run the following command: db.disableFreeMonitoring()
---
```
#### ----End O/P----

###### If we want to check dbs in mongodb then, in bash we need write add show dbs
```
> show dbs
admin   0.000GB
config  0.000GB
local   0.000GB
```

 #### If we want to exit from bash / Interactive mode of container
  ## ***_ctrl + d_*** ##														                         

 
----------------------------------------------------------------------------
 
#### Difference in docker stop and docker kill
```
> docker stop <container_id>
```
> It will execute the ongoing process and then stop the container or we can say that after completion
> of current executing work it can stop the container

```
> docker kill <container_id>
```
> It will kill/stop the container without waiting for completion of ongoing process.

-----------------------------------------------------------------------------

##### Multiple ways to get into container
```
docker exec -it  efc10b902596 bash - 
```
> In this  case we need to start the container first (if it is not yet running) and then need to execute this command to enter in that > > container
```
docker run -it mongo bash  
```
> You don't need to start container here, This command will start your container as well as it will enter in container as well

--------------------------------------------------------------------------------

=== Create Your Own Image === 

> we can going to create mymongo image

> first create folder > mkdir mymongo
> Go to that folder > mymongo -> and then create Dockerfile

> Here understand that how to create container image

> Dockerfile -- It is processed by  --> Docker client --It will give futher to Docker Server and process the commands written in Docker > file --After all the processing image is going to generate--> Custom Image
 
> what to write inside the Dockerfile, hmmmm ??
> so, lets start, prior to that understand first how to write comment in Dockerfile
> using [ # ] symbol you can write the command.
> e.g --> # step 1


> Let's Start with create of Dockerfile
> Dockerfile is composition of:-
> [ INSTRUCTION ] [ ARGUMENT ] 
> Everything on left in dockerfile is instruction which tell docker client what to do
> Everything on right in dockerfile is argument which is instruction for that argument


<!-- Docker File Start -->

# step 1
# First step is used os to interact with hardware, here we are using alpine
# alpine - It is minimal docker image which is based on Alpine Linux 
# It is base image
```
FROM alpine
```

# step 2
# Install a software
# apk - It is like [ apt get ]
# binutils - is nothing but program
# It is like we are going to the alpine environment and adding binutils program
```
RUN apk add binutils
```
<!-- Docker File End -->

Each line in dockerfile contains layer, 

Now create docker image

Go to mymongo folder ```$mymongo >```
do the ls command to check Dockerfile is present or not ```$mymongo > ls```

then run docker build command, and see the result 
```$mymongo > docker build .```
Sending build context to Docker daemon  2.048kB
Step 1/2 : FROM alpine
latest: Pulling from library/alpine
c9b1b535fdd9: Pulling fs layer
c9b1b535fdd9: Verifying Checksum
c9b1b535fdd9: Download complete
c9b1b535fdd9: Pull complete
Digest: sha256:ab00606a42621fb68f2ed6ad3c88be54397f981a7b70a79db3d1172b11c4367d
Status: Downloaded newer image for alpine:latest
 ---> e7d92cdc71fe
Step 2/2 : RUN apk add binutils
 ---> Running in 73907c905946
fetch http://dl-cdn.alpinelinux.org/alpine/v3.11/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.11/community/x86_64/APKINDEX.tar.gz
(1/3) Installing libgcc (9.2.0-r3)
(2/3) Installing libstdc++ (9.2.0-r3)
(3/3) Installing binutils (2.33.1-r0)
Executing busybox-1.31.1-r9.trigger
OK: 17 MiB in 17 packages
Removing intermediate container 73907c905946
 ---> e3aec4897168
Successfully built e3aec4897168
---------------------------------------

If any of layer is failed, then we need to fixed it and it doesn't start with first layer, acutally it 
cache the layer and when we re-run it again, it takes from cache and starts from the failed part again

--------------------------------------------------------------------------
##### Inspect

To get the details of docker container, then run below commands
```
> docker inspect <container_id>
```
--------------------------------------------------------------------------
##### Logs

TO get the logs of container
```
> docker logs <container_id>
```
-------------------------------------------------------------

##### History

TO get the history of docker image
```
> docker history <container-id>
```
e.g
```
> docker history redis                                                                                                  IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
7eed8df88d3b        13 days ago         /bin/sh -c #(nop)  CMD ["redis-server"]         0B
<missing>           13 days ago         /bin/sh -c #(nop)  EXPOSE 6379                  0B
<missing>           13 days ago         /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B
<missing>           13 days ago         /bin/sh -c #(nop) COPY file:df205a0ef6e6df89…   374B
<missing>           13 days ago         /bin/sh -c #(nop) WORKDIR /data                 0B
<missing>           13 days ago         /bin/sh -c #(nop)  VOLUME [/data]               0B
<missing>           13 days ago         /bin/sh -c mkdir /data && chown redis:redis …   0B
<missing>           13 days ago         /bin/sh -c set -eux;   savedAptMark="$(apt-m…   24.6MB
<missing>           13 days ago         /bin/sh -c #(nop)  ENV REDIS_DOWNLOAD_SHA=61…   0B
<missing>           13 days ago         /bin/sh -c #(nop)  ENV REDIS_DOWNLOAD_URL=ht…   0B
<missing>           13 days ago         /bin/sh -c #(nop)  ENV REDIS_VERSION=5.0.7      0B
<missing>           13 days ago         /bin/sh -c set -eux;  savedAptMark="$(apt-ma…   4.04MB
<missing>           13 days ago         /bin/sh -c #(nop)  ENV GOSU_VERSION=1.11        0B
<missing>           13 days ago         /bin/sh -c groupadd -r -g 999 redis && usera…   329kB
<missing>           2 weeks ago         /bin/sh -c #(nop)  CMD ["bash"]                 0B
<missing>           2 weeks ago         /bin/sh -c #(nop) ADD file:e5a364615e0f69616…   69.2MB
```
------------------------------------------------------------------

