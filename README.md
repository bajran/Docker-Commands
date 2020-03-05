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

##### Commands

``` 
> docker version 
To get the version of docker, which is installed in our system
```
--------------------------------------------------------
```
> docker pull busybox
It will pull *busybox* image from docker-hub
```
--------------------------------------------------------
```
> docker run busybox
It will check whether it have busybox image in their local image repository, if it does not have this
the it will go to docker-hub and pull that image to our local image repository and then run that, it 
happens only once if the image is not their in our local image repository
```
---------------------------------------------------------
```
> docker ps
To see running the container
```
----------------------------------------------------------
```
> docker ps --all or docker ps -a
To see all the container
```
----------------------------------------------------------
```
> docker ps --all
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                      PORTS               NAMES
efc10b902596        mongo               "docker-entrypoint.s…"   9 minutes ago       Up 9 minutes                27017/tcp           tender_grothendieck
```
----------------------------------------------------------

##### Start Contianer
If I want to run the mongo container then I need to get the container id, and run the start command which 
is shown below
```
> docker start efc10b902596
```
##### Stop Container
If I want to stop the mongo container then I need to get the container id, and run the stop command which 
is shown below
```
> docker stop efc10b902596
```
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
It will execute the ongoing process and then stop the container or we can say that after completion
of current executing work it can stop the container

```
> docker kill <container_id>
```
It will kill/stop the container without waiting for completion of ongoing process.

-----------------------------------------------------------------------------
