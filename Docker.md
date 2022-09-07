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

Each image can be run in different ways, below you can see common examples:

```powershell
Docker run <name of the image>
```
```powershell
docker run --name some-nginx -v /some/content:/usr/share/nginx/html:ro -d nginx
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
