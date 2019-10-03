## Docker Basics

### docker ps -a

 This commands lists the containers on our system

Here, you can see one entry(hello-world)
```
syamj@test-ubuntu:~$ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                      PORTS               NAMES
4c7d3d414cc8        hello-world         "/hello"            45 minutes ago      Exited (0) 45 minutes ago                       tender_goldberg
syamj@test-ubuntu:~$
```
- CONTAINER ID - A unique ID assigned to a container.
- IMAGE - Name of the image.
- COMMAND - Command run while executing the container.
- CREATED - Create time.
- STATUS - Status of the Container.
- PORTS - If any port is exposed.
- NAMES - Name given to a container.


### docker ps


```
syamj@test-ubuntu:~$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
syamj@test-ubuntu:~$

```
docker ps command will only list the containers which are running currently.

### docker images

This command lists all the images in the system.
In our case, we have only one image - hello-world.
```
syamj@test-ubuntu:~$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
hello-world         latest              fce289e99eb9        9 months ago        1.84kB
syamj@test-ubuntu:~$
```
Even after the container is stopped the image remains in the system. So if we need to run the container again, there is no need to download the image from the central repository.

There are two type of Docker Images.

- OS Images
	It will be an image of an Operating system(eg:- Ubuntu, Centos etc)
- App Images
   This image will contain an application and all it's dependencies(eg:- Jenkins, Nginx)

When we run  docker run hello-world, docker checks if the image is available in the local system. If not, docker will access registry.hub.docker.com  and download the image.

A docker image name has two parts.

- image name
- image tag

Example :-
- centos:6
- httpd:2.2
- ubuntu:16.04
- ubuntu:16.10
- ubuntu:latest


### docker pull <image_name:tag>

Docker pull is used to download a specific image to our local system.
> Note : This command will only download. To run the container , docker run should be used.
```
syamj@test-ubuntu:~$ docker pull  ubuntu:18.10
18.10: Pulling from library/ubuntu
8a532469799e: Pull complete
32f4dcec3531: Pull complete
230f0701585e: Pull complete
e01f70622967: Pull complete
Digest: sha256:7d657275047118bb77b052c4c0ae43e8a289ca2879ebfa78a703c93aa8fd686c
Status: Downloaded newer image for ubuntu:18.10

syamj@test-ubuntu:~$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
ubuntu              18.10               9dc19675e327        2 months ago        67.3MB
hello-world         latest              fce289e99eb9        9 months ago        1.84kB
syamj@test-ubuntu:~$

```

### docker rm <container_id>

docker rm is used to delete an container from the system.
Now I'm going to delete the container hello-world from my system
```
syamj@test-ubuntu:~$ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                         PORTS               NAMES
4c7d3d414cc8        hello-world         "/hello"            About an hour ago   Exited (0) About an hour ago                       tender_goldberg

syamj@test-ubuntu:~$ docker rm 4c7d3d414cc8
4c7d3d414cc8
syamj@test-ubuntu:~$

syamj@test-ubuntu:~$ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
syamj@test-ubuntu:~$

```
Now the container hello-world is not listed when I run the command docker ps -a
