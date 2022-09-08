# Docker Labs

## Commands

## ps

docker ps command allows us to see the running containers

```powershell
docker ps
```

### Pull

```powershell
Docker Pull <name of the image>
```

### Run

Each image can be run in different ways, and will depend on the task, below you can see common examples:

```powershell
Docker run <name of the image>
```
```powershell
docker run --name some-nginx `
-v /some/content:/usr/share/nginx/html:ro `
-d nginx
```
```powershell
docker run -it ubuntu
```
```powershell
docker run -d ubuntu bash `
-c "shuf -i 1-10000 -n 1 -o /data.txt && tail -f /dev/null"

docker exec bd5d28124f63 cat /data.txt
```

### Docker Stop

```powershell
docker stop <CONTAINER_ID>
i.e docker stop f1b9c871b706
```

### Docker rm

```powershell
docker rm <CONTAINER_ID>
i.e docker rm f1b9c871b706
```

### Create

We can use the below command to create the containers, based on an image

```powershell
docker create <name of the image>
i.e docker create nginx
```

We can create our own container with the docker container create:

```powershell
docker container create --name my-nginx-container nginx
```

Then run the container with the custom name:

```powershell
docker container start my-nginx-container
docker ps
```

### Push

```powershell
docker push
```

## Persistence 

If we need to have persistence we might use the docker volume and its sub-commands:

```powershell
docker volume create todo-db
```

We normally run an application like this:
```
docker run -d -p 80:80 docker/getting-started
```

To attach a volume we can run the command with the -v option, while specifying the already created volume inside the container:

```powershell
docker run -d -p 80:80 `
-v todo-db:/etc/todos docker/getting-started
```

With the create container id, we can check that our container has a volume created in the /etc/todos directory (do not forget to change your container id):

```powershell
docker exec -it `
16dad0d893cb99385dfaf1776c71ccf98c6d1a673a3304321f5023aaa2cbd657 `
ls /etc
```

After this we can write/read in our volume and then in case we destroy or create a new container, we can attach our container and our data will be there to be used

If we need to see the volumes that we have created we can use the below command

```powershell
docker volume ls
```

We can inspect our volume with the below command

```powershell
docker volume inspect todo-db
```

### Control where we store the data with bind mounts

If we need to know where the data is stored, or we need to identify the path where the mounting point is, we can specify this with the below command

```powershell
docker run -d -p 80:80 `
-v "<location where we want to store the data from our computer>" `
todo-db:/etc/todos docker/getting-started
```

Any data will be stored in the specified location and we'll be able to see the data from our computer, not like when we don't bind the mount

## Work with Multiple Containers at the Same Time

How do we have a container that can use another container for any task?. With network

List our networks:

```powershell
docker network ls
```

Bridgem, None and Host are default networks

To remove a network we can execute the below command:

```powershell
docker network rm <name of the network>
```


We can inspect our networks with the below command

```powershell
docker network inspect <container id or name>
```


