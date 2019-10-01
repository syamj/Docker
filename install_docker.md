# Install Docker in Ubuntu!
Run the below command to update your repository.
```
sudo apt-get update
```
To install Docker, run the below command.

```
sudo apt-get install docker.io
```

You should see something like this. Press 'Y' to confirm the installation.
```
syamj@test-ubuntu:~ $ sudo apt-get install docker.io
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  bridge-utils cgroupfs-mount containerd pigz runc ubuntu-fan
Suggested packages:
  ifupdown aufs-tools debootstrap docker-doc rinse zfs-fuse | zfsutils
The following NEW packages will be installed:
  bridge-utils cgroupfs-mount containerd docker.io pigz runc ubuntu-fan
0 upgraded, 7 newly installed, 0 to remove and 11 not upgraded.
Need to get 52.2 MB of archives.
After this operation, 257 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Adding group `docker' (GID 115) ...
Done.
Created symlink /etc/systemd/system/sockets.target.wants/docker.socket → /lib/systemd/system/docker.socket.
Processing triggers for systemd (237-3ubuntu10.29) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for ureadahead (0.100.0-21) ...
syamj@test-ubuntu:~$
```
Once completed, let's start docker and make sure it's running.

```
sudo systemctl start docker
sudo systemctl enable docker
sudo systemctl status docker
```
```
syamj@test-ubuntu:~ $ sudo systemctl status docker
● docker.service - Docker Application Container Engine
   Loaded: loaded (/lib/systemd/system/docker.service; disabled; vendor preset: enabled)
   Active: active (running) since Tue 2019-10-01 11:14:47 UTC; 5min ago
     Docs: https://docs.docker.com
```
To check the version of the Docker.
```
docker version
```

And the output should should look like this.
```
syamj@test-ubuntu:~$ docker version
Client:
 Version:           18.09.7
 API version:       1.39
 Go version:        go1.10.1
 Git commit:        2d0083d
 Built:             Fri Aug 16 14:20:06 2019
 OS/Arch:           linux/amd64
 Experimental:      false

Server:
 Engine:
  Version:          18.09.7
  API version:      1.39 (minimum version 1.12)
  Go version:       go1.10.1
  Git commit:       2d0083d
  Built:            Wed Aug 14 19:41:23 2019
  OS/Arch:          linux/amd64
  Experimental:     false

```

Yay! Docker is started and running in our Ubuntu Machine :) 

Now to make sure everything works fine, run the below command.

```
docker run hello-world
```

While running this I got the below permission denied error.

```
syamj@test-ubuntu:~$ docker run hello-world
docker: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post http://%2Fvar%2Frun%2Fdocker.sock/v1.39/containers/create: dial unix /var/run/docker.sock: connect: permission denied.
See 'docker run --help'.
syamj@test-ubuntu:~$

```

Okay! Now to fix this, this is what I did.

- Open /etc/group file
- Add your username(syamj in my case) to the group docker

Now the group docker will look like below

```
syamj@test-ubuntu:~$ sudo grep docker /etc/group
docker:x:115:syamj
syamj@test-ubuntu:~$
```

Great. We'll try the hello-world command again. :)

```
syamj@test-ubuntu:~$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
1b930d010525: Pull complete
Digest: sha256:b8ba256769a0ac28dd126d584e0a2011cd2877f3f76e093a7ae560f2a5301c00
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

```

### YAY!! It worked :)

#### So what does docker run hello-world do?

docker run hello-world does exactly what it sounds like. It runs an image named "hello-world."
Docker looks for this image on our local system. When it can’t find the image, Docker downloads it from Docker Hub for us.
Hello-world displays a message telling us everything’s working. Then it spells out the process for us before recommending some additional steps.
