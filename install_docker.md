# Install Docker in Ubuntu!
Run the below command to update your repository.
```
sudo apt-get update
```
To install Docker, run the below command.

```
sudo apt-get install docker.io
```

> syamj@test-ubuntu:~ $ sudo apt-get install docker.io
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
sudo systemctl start docker
sudo systemctl status docker
```
>syamj@test-ubuntu:~ $ sudo systemctl status docker
● docker.service - Docker Application Container Engine
   Loaded: loaded (/lib/systemd/system/docker.service; disabled; vendor preset: enabled)
   Active: active (running) since Tue 2019-10-01 11:14:47 UTC; 5min ago
     Docs: https://docs.docker.com

To check the version of the Docker.
```
docker --version
```
>syamj@test-ubuntu:~ $ docker --version
Docker version 18.09.7, build 2d0083d
syamj@test-ubuntu:~$


Yay! Docker is started and running in our Ubuntu Machine :) 
