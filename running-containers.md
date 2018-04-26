# Running containers

Running images with Docker can be done using the `Docker run` command. The command can take many attributes that give more information on how to run the container. 

To run the hello-world image that we created earlier, we can use the following command.

```bash
docker run -it -p 80:80 hello-world
```

The command tells to run the hello-world image and create a container. Next we need to tell that we also want the internal port 80 to be available on port 80 on the host machine, this can be done by using the `-p` flag. All traffic to port 80 of the Docker host will be forwarded to port 80 in the container. 

The `-it` flag will make sure the output of the Container is forwarded to our terminal. Terminating the terminal output will also result in terminating the container.

Other flags are documented in the Docker documentation:

{% embed data="{\"url\":\"https://docs.docker.com/engine/reference/run/\",\"type\":\"link\",\"title\":\" \| Docker Documentation\",\"description\":\"Configure containers at runtime\",\"icon\":{\"type\":\"icon\",\"url\":\"https://docs.docker.com/favicons/docs@2x.ico\",\"width\":129,\"height\":128,\"aspectRatio\":0.9922480620155039},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://docs.docker.com/images/docs@2x.png\",\"width\":950,\"height\":500,\"aspectRatio\":0.5263157894736842}}" %}

Lets execute the command and check if everything is running.

The terminal will output the output of the container when running this command. It should look somethig

```text
$ docker run -p 80:80 hello-world
AH00558: apache2: Could not reliably determine the server's fully qualified 
domain name, using 172.17.0.3. Set the 'ServerName' directive globally to 
suppress this message
AH00558: apache2: Could not reliably determine the server's fully qualified 
domain name, using 172.17.0.3. Set the 'ServerName' directive globally to 
suppress this message
[Thu Apr 26 19:00:38.670160 2018] [mpm_prefork:notice] [pid 1] AH00163: 
Apache/2.4.25 (Debian) PHP/7.2.4 configured -- resuming normal operations
[Thu Apr 26 19:00:38.670527 2018] [core:notice] [pid 1] AH00094: Command 
line: 'apache2 -D FOREGROUND'
```

This is the normal output of the Apache application.

Lets start up a browser and surf to [http://192.168.99.100](http://192.168.99.100) If all goes well, we should be able to see the webpage. 

![PHP page hosted from within a Docker container](.gitbook/assets/docker-hello-world-browser.png)

In the terminal we should also see the loggin informatin of Apache detecting our HTTP request and showing some information about that request:

```text
192.168.99.1 - - [26/Apr/2018:19:06:10 +0000] "GET / HTTP/1.1" 200 241 "-" 
  "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko)
   Chrome/66.0.3359.117 Safari/537.36"
192.168.99.1 - - [26/Apr/2018:19:06:10 +0000] "GET /favicon.ico HTTP/1.1" 
   404 505 "http://192.168.99.100/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) 
   AppleWebKit/537.36 (KHTML, like Gecko) Chrome/66.0.3359.117 Safari/537.36"
```

To end the Docker container, press `CTRL+C`. The container will then stop. The Apache server will stop, and it won't be possible to access the webpage again. 

The `docker run` command that we used allows only a single container to run. This might be good to test something quickly, but on a production environment, many containers will be running.

### Running in the background

Docker makes it possible to run containers in the background. This can easily  be done by adding the `-d` flag on the `docker run` command. The `-d` flag will deamonize the container. This means that the container will be running in the background.

```text
 docker run -d -p 80:80 hello-world
```

When running this command, the terminal will return a random string that represents the newly created container. This output could be used to automate other tasks. 

```text
$  docker run -d -p 80:80 hello-world
9881cc50821035579c788372eb453c400ed5649c75a175d52627f27fd7bedab8
```

It is now possible to execute other commands in the terminal. The container will keep running until it is stopped manually.

Test this by surfing to the webpage again and see if you get the Hello World message back.

### Listing all running containers

To see which containers are running, you can use the following command:

```text
docker ps
```

This will show something like this:

```text
$ docker ps
CONTAINER ID   IMAGE         COMMAND                  CREATED         STATUS          PORTS                NAMES
9881cc508210   hello-world   "docker-php-entryp..."   2 minutes ago   Up 2 minutes    0.0.0.0:80->80/tcp   cocky_mcclintock
```

### Stopping containers

Stopping containers can be done with the following command:

```text
docker stop <container_id/name>
```

To stop the container that we created earlier, we can run the following command using its `CONTAINER_ID`:

```text
docker stop 9881cc508210
```

It is also possible to stop the container using its NAME. In this case the command should look like this:

```text
docker stop cocky_mclintock
```

Note that docker will give all its containers a random name. It is possible to assign a custom name to a container by providing the` --name` flag with the `docker run` command.

