# Inspecting containers

### Logs



{% embed data="{\"url\":\"https://docs.docker.com/engine/reference/commandline/logs/\",\"type\":\"link\",\"title\":\"docker logs\",\"description\":\"Description Fetch the logs of a container Usage docker logs \[OPTIONS\] CONTAINER Options Name, shorthand Default Description --details Show extra details provided to logs --follow , -f Follow log output...\",\"icon\":{\"type\":\"icon\",\"url\":\"https://docs.docker.com/favicons/docs@2x.ico\",\"width\":129,\"height\":128,\"aspectRatio\":0.9922480620155039},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://docs.docker.com/images/docs@2x.png\",\"width\":950,\"height\":500,\"aspectRatio\":0.5263157894736842}}" %}





### Docker exec

When a container is running in the background. It is possible to execute commands inside that container. A popular command is `bash`. This enables to view what is going on inside the container. You could compare this with an SSH session into the Container.

```text
docker exec -it <containerIdOrName> bash
```

{% embed data="{\"url\":\"https://docs.docker.com/engine/reference/commandline/exec/\",\"type\":\"link\",\"title\":\"docker exec\",\"description\":\"Description Run a command in a running container Usage docker exec \[OPTIONS\] CONTAINER COMMAND \[ARG...\] Options Name, shorthand Default Description --detach , -d Detached mode: run command in the background...\",\"icon\":{\"type\":\"icon\",\"url\":\"https://docs.docker.com/favicons/docs@2x.ico\",\"width\":129,\"height\":128,\"aspectRatio\":0.9922480620155039},\"thumbnail\":{\"type\":\"thumbnail\",\"url\":\"https://docs.docker.com/images/docs@2x.png\",\"width\":950,\"height\":500,\"aspectRatio\":0.5263157894736842}}" %}





