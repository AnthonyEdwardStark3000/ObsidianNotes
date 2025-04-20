#### Docker volumes
![[Pasted image 20250412154834.png]]Used to store the containers in it so that the changes made in the containers will remain, whenever the container is stopped and restarted.

```
run -d --rm -p 8080:80 -v nginx-data:/usr/share/nginx/html --name nginx-test nginx:stable

docker volume list - to check the volumes available or created

docker exec -it nginx-test   

root@dc8e91a17900:/usr/share/nginx/html# echo "Docker this change is permanent" > index.html   

exit
```
#### Creating Docker image for containerization

Docker image can be created using either of these two options
1.  Docker file
2.  .Net SDK

 > Docker image is an blueprint that contains everything needed to run the application .  

#### Docker file : -
 Docker file is an simple text file that contains the configuration for creating a docker image , which creates image via BuildKit when it is build. 
 
  ![[Pasted image 20250412160956.png | 400 | 600]]

```
dotnet publish .\CRUDExample.csproj -o published /p:UseAppHost=false
```
Write a docker file

```
FROM mcr.microsoft.com/dotnet/aspnet:8.0

  

# working directory

WORKDIR /app

  

# what file to be copied

COPY published/ ./

  

# what file to be run from the copied file

ENTRYPOINT ["dotnet","CRUDExample.dll"]
```

#### Building a docker image

```
# docker build -t docker-name location-of-the-docker-file

dotnet build -t crudexample-docker . (or) docker build -t crudexample-docker -f DockerFile .
docker images
docker run --rm -p 8080:8080 crudexample-docker 
```

#### MultiStageBuilds - What if a change occurs in the above done build and want to upload that ? 

.dockerignore

```
**/bin

**/obj

**/Properties

**/DockerFile*

**/dockerignore

**/appsettings.Development.json

**/*.sln
```

DockerFile

```
# Stage 1

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build

WORKDIR /src

COPY . .

RUN dotnet publish "CRUDExample.csproj" -o /published /p:UseAppHost=false

  

# Stage 2

FROM mcr.microsoft.com/dotnet/aspnet:8.0

# working directory

WORKDIR /app

# what file to be copied

# COPY published/ ./

COPY --from=build /published .

  

# what file to be run from the copied file

ENTRYPOINT ["dotnet","CRUDExample.dll"]
```

docker images
docker rmi crudexample-docker

#### Build docker again
docker build -t crudexample-docker -f DockerFile .

