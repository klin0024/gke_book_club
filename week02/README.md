# Week 02 - docker 基礎2

### 資料管理

```
docker volume create
```

```
docker volume ls
```

```
docker volume inspect
```

```
docker volume rm
```

##### 

如果你使用selinux你可以添加z或Z選項來修改被掛載到容器中的主機文件或目錄的 selinux 標籤
z: 綁定掛載內容在多個容器之間共享
Z: 綁定掛載內容是私有的且未共享的
ro:
rw:

### 網路管理

```
docker network create
```

```
docker network ls
```

```
docker network inspect
```

```
docker network rm
```

```
docker port
```

### 進階管理

```
docker stats
```

```
docker top
```

```
docker system
```
##### Restart policies

Policy	|Result
:---|:---
no	|退出時不要自動重啟容器。這是默認設置
on-failure[:max-retries]	|僅當容器以非零退出狀態退出時才重新啟動。（可選）限制 Docker 守護程序嘗試重新啟動的次數
always	|無論退出狀態如何，始終重新啟動容器。當您指定 always 時，Docker 守護進程將嘗試無限期地重新啟動容器。無論容器的當前狀態如何，容器也將始終在守護程序啟動時啟動。
unless-stopped	|無論退出狀態如何，始終重啟容器，包括守護進程啟動時，除非容器在 Docker 守護進程停止之前進入停止狀態


##### 命名空間

pid 命名空間

net 命名空間

ipc 命名空間

mnt 命名空間

uts 命名空間

user 命名空間

--net=host
--pid=host
--ipc=host
--uts=host
--userns=host

##### Prune

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


```
docker build -t
```