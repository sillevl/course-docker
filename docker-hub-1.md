# Docker Hub

Sharing Docker images is made easy by Docker Hub. Anybody can create an account to Docker Hub to distribute images that can be deployed on other systems or by other users. 

For this example, let us use an open source project from github. The TodoMVC using Nodejs, Vue, and Nuxt should be a great example. It is a demo application using JavaScript on the server and client. 

{% embed data="{\"url\":\"https://github.com/nuxt/todomvc\",\"type\":\"link\",\"title\":\"nuxt/todomvc\",\"description\":\"todomvc - Nuxt.js TodoMVC Example\",\"icon\":{\"type\":\"icon\",\"url\":\"https://github.com/fluidicon.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://avatars0.githubusercontent.com/u/23360933?s=400&v=4\",\"width\":400,\"height\":400,\"aspectRatio\":1}}" %}

Lets clone the project so that we have it on our computer. Cloning the git repository can be done with the following command: 

```text
git clone https://github.com/nuxt/todomvc.git
```

This will download the project in a directory called `todomvc`.

By default the project does not provide a Dockerfile. We will need to create one. An example could be:

{% embed data="{\"url\":\"https://gist.github.com/sillevl/09be59e875c706296cbfd01d627bc95e\",\"type\":\"rich\",\"title\":\"Docker file for node project with vue\",\"description\":\"Docker file for node project with vue · GitHub\",\"icon\":{\"type\":\"icon\",\"url\":\"https://gist.github.com/fluidicon.png\",\"aspectRatio\":0},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://avatars3.githubusercontent.com/u/979071?s=400&v=4\",\"width\":400,\"height\":400,\"aspectRatio\":1},\"embed\":{\"type\":\"reader\",\"html\":\"<script type=\\"text/javascript\\" src=\\"https://gist.github.com/09be59e875c706296cbfd01d627bc95e.js\\"></script>\",\"aspectRatio\":0}}" %}

This `Dockerfile `will use an node image to provide the JavaScript runtime on the server. It will also install all dependencies using the npm package manager. Finally it will start the application using the `npm start` command.

Lets build it using the command

```text
docker build -t todomvc .
```

You can test the container using the command

```text
docker run -it -p 80:3000 todomvc
```

When everything works well, you could share the container using Docker Hub. You will need to create an account to be able to push \(upload\) containers and distribute them to other systems or developers.

When you have an account, you can log in to Docker Hub using the command line using the command

```text
docker login
```

Before we can push the container we need to 'tag' it with a name. This can be done using the command

```text
docker tag todomvc YOUR-USER-ID/ todomvc
```

{% hint style="info" %}
Don't forget to replace YOUR-USER-ID with your Docker Hub user id.
{% endhint %}

Now you are ready to push the image to Docker Hub using the command

```text
docker push YOUR-USER-ID/todomvc
```

You can now go to your Docker Hub and see your newly pushed image at [https://hub.docker.com/](https://hub.docker.com/)

The image is now available to anybody and can be run with the command

```text
docker run -it -p 80:3000 YOUR-USER-ID/todomvc
```

You should now be able to visit the webpage at [http://192.168.99.100](http://192.168.99.100)

