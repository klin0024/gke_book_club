# Week 02 - docker 基礎2

### 資料管理

- Create a volume

```
docker volume create
```

- List volumes

```
docker volume ls
```

- Display detailed information on one or more volumes

```
docker volume inspect
```

- Remove one or more volumes

```
docker volume rm
```

##### 掛載標記

z: 綁定掛載內容在多個容器之間共享
Z: 綁定掛載內容是私有的且未共享的
ro: 掛載內容唯讀
rw: 掛載內容可讀寫

- example

### 網路管理

- Create a network

```
docker network create
```

- List networks

```
docker network ls
```

- Display detailed information on one or more networks

```
docker network inspect
```

- Remove one or more networks

```
docker network rm
```

- List port mappings or a specific mapping for the container

```
docker port
```

### 進階管理

- Display a live stream of container(s) resource usage statistics

```
docker stats
```

- Display the running processes of a container

```
docker top
```

- Show docker disk usage

```
docker system df
```

- Get real time events from the server

```
docker system events
```

- Display system-wide information

```
docker system info
```

##### 重啟策略

Policy	|Result
:---|:---
no	|退出時不要自動重啟容器。這是默認設置
on-failure[:max-retries]	|僅當容器以非零退出狀態退出時才重新啟動。（可選）限制 Docker 守護程序嘗試重新啟動的次數
always	|無論退出狀態如何，始終重新啟動容器。當您指定 always 時，Docker 守護進程將嘗試無限期地重新啟動容器。無論容器的當前狀態如何，容器也將始終在守護程序啟動時啟動。
unless-stopped	|無論退出狀態如何，始終重啟容器，包括守護進程啟動時，除非容器在 Docker 守護進程停止之前進入停止狀態

- example


##### 命名空間

- pid 命名空間

- net 命名空間

- ipc 命名空間

- mnt 命名空間

- uts 命名空間

- user 命名空間

--net=host
--pid=host
--ipc=host
--uts=host
--userns=host

##### 刪除未使用的物件

```
docker image prune
```

```
docker container prune
```

```
docker volume prune
```

```
docker network prune
```

```
docker system prune
```

### Dockerfile

FROM: 使用的基礎鏡像

MAINTAINER: 維護者訊息

ENV: 環境變數

RUN: 鏡像檔基底上執行指定命令

複製本地端的檔案到容器中
ADD: 可以是一個 URL；還可以是一個 tar 檔案（其複製後會自動解壓縮）
COPY: 複製一個目錄或一個檔案


EXPOSE: 容器對外的Port
VOLUME: 從本地端或其他容器掛載的掛載點
USER: 運行容器時的使用者名稱或 UID，後續的 RUN 也會使用指定使用者
WORKDIR: 後續的 RUN、CMD、ENTRYPOINT 指令指定工作目錄

CMD:  指定啟動容器時執行的命令
ENTRYPOINT: 指定容器啟動後執行的命令，並且不會被 docker run 提供的參數覆蓋

[Example](Dockerfile)


- Build an image from a Dockerfile

```
docker build -t
```