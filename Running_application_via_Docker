## Running real applications via Docker.

Now let's try running an apache webserver as a container.
```
syamj@test-ubuntu:~$ docker run --name webserver  -p 8080:80  -d httpd:2.2
2764ad3324be860a4321b13b3538856c79264ccf027575307601e4305cc8f383
syamj@test-ubuntu:~$ sudo netstat -plantu | grep 80
tcp6       0      0 :::8080                 :::*                    LISTEN      14397/docker-proxy
syamj@test-ubuntu:~$
```
While running the container named webserver we used two attributes 
- -p 8080:80 :- This means the application running in the port 80 of the docker container will automatically be re directed to 8080 of the local machine. So from the outer world if call ip_of_VM:8080 ,we'll be able to access the application hosted in the container.
-  -d :- This will run the container in background, ie, ,the container won't exit till we stop the container.

### docker exec

So now the container is running in the background. Let's check what is running inside the container.

```
syamj@test-ubuntu:~$ docker ps -a
CONTAINER ID        IMAGE               COMMAND              CREATED             STATUS              PORTS                  NAMES
2764ad3324be        httpd:2.2           "httpd-foreground"   19 minutes ago      Up 19 minutes       0.0.0.0:8080->80/tcp   webserver
syamj@test-ubuntu:~$ docker exec -it webserver /bin/bash
root@2764ad3324be:/usr/local/apache2# ps ax
   PID TTY      STAT   TIME COMMAND
     1 ?        Ss     0:00 httpd -DFOREGROUND
     7 ?        S      0:00 httpd -DFOREGROUND
     8 ?        S      0:00 httpd -DFOREGROUND
     9 ?        S      0:00 httpd -DFOREGROUND
    10 ?        S      0:00 httpd -DFOREGROUND
    11 ?        S      0:00 httpd -DFOREGROUND
    12 pts/0    Ss     0:00 /bin/bash
    18 pts/0    R+     0:00 ps ax
root@2764ad3324be:/usr/local/apache2#
```
