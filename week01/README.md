# Week 01 - docker 基礎1


### 基本概念

Docker 包括三個基本概念
- 映像檔（Image）
- 容器（Container）
- 倉庫（Repository）

### 安裝

##### 手動安裝

- Install Docker 19.03+:
```
sudo dnf install -y yum-utils
sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
sudo dnf install -y docker-ce docker-ce-cli containerd.io
sudo systemctl start docker
```

- Verify you are now running version 19.03+:
```
sudo docker version
```

- Compare your output with the following example to ensure the Client and Server versions are 19.03+ :
```
Client: Docker Engine - Community
  Version:          19.03.13
  ...
Server: Docker Engine - Community
  Engine:
  Version:          19.03.13
```

##### 從 Marketplace 部署



### 映像檔

```
docker pull 
```

```
docker images
```

```
docker inspect
```

```
docker rmi
```

```
docker rmi $(docker images -q)
```

```
docker save -o 
```

```
docker load -i
```

### 容器


```
docker run
```

```
docker run -d
```

```
docker run -d -p 80:80
```

```
docker run -d -v /some/content:/usr/share/nginx/html
```

```
docker run -d -e NGINX_PORT=80
```

```
docker ps
```

```
docker ps -a
```

```
docker inspect
```

```
docker exec -it
```

```
docker stop
```

```
docker start
```

```
docker restart
```

```
docker rm
```

```
docker rmi $(docker ps -q)
```

### 倉庫

##### 公有倉庫

- Docker Hub: https://hub.docker.com/
- Quay: https://quay.io/
- GCR: https://cloud.google.com/container-registry

##### 私有倉庫

- Docker Registry: https://docs.docker.com/registry/
- Harbor: https://goharbor.io/docs/2.3.0/
- Artifact Registry: https://cloud.google.com/artifact-registry/docs/quickstarts

```
docker login
```

```
docker tag
```

```
docker push
```

```
gcloud auth configure-docker
```