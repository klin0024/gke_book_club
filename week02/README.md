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

[example](volume_metadata.json)

- Remove one or more volumes

```
docker volume rm
```

- example

```
docker run -d -v volume:/usr/share/nginx/html
```

##### 掛載標記

標記 | 說明
:---|:---
z| 貼上SELinux標籤,綁定掛載內容在多個容器之間共享
Z| 貼上SELinux標籤,綁定掛載內容是私有的且未共享的
ro| 掛載內容唯讀
rw| 掛載內容可讀寫

- example

```
docker run -d -v /some/content:/usr/share/nginx/html:ro
```

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

[example](network_metadata.json)

- Remove one or more networks

```
docker network rm
```

- example

```
docker run -d -net=net
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

[example](docker_info.txt)

##### 重啟策略

Policy	|Result
:---|:---
no	|退出時不要自動重啟容器。這是默認設置
on-failure[:max-retries]	|僅當容器以非零退出狀態退出時才重新啟動。（可選）限制 Docker 守護程序嘗試重新啟動的次數
always	|無論退出狀態如何，始終重新啟動容器。當您指定 always 時，Docker 守護進程將嘗試無限期地重新啟動容器。無論容器的當前狀態如何，容器也將始終在守護程序啟動時啟動。
unless-stopped	|無論退出狀態如何，始終重啟容器，包括守護進程啟動時，除非容器在 Docker 守護進程停止之前進入停止狀態

- example

```
docker run --restart always
```

##### 命名空間

- pid 命名空間

不同使用者的程式就是透過 pid 命名空間隔離開的，且不同命名空間中可以有相同 pid。所有的 LXC 程式在 Docker 中的父程式為 Docker 程式，每個 LXC 程式具有不同的命名空間。同時由於允許巢狀結構，因此可以很方便的實作巢狀結構的 Docker 容器。

使用宿主主機pid 命名空間

```
docker run --pid=host
```

- net 命名空間

網路隔離是透過 net 命名空間實作的， 每個 net 命名空間有獨立的網路設備, IP 位址, 路由表, /proc/net 目錄。這樣每個容器的網路就能隔離開來。Docker 預設採用 veth 的方式，將容器中的虛擬網卡同 host 上的一個 Docker 橋接器 docker0 連接在一起。

使用宿主主機net 命名空間

```
docker run --net=host
```

- ipc 命名空間

容器中程式互動還是採用了 Linux 常見的程式間互動方法 (interprocess communication - IPC), 包括信號量、消息隊列和共享記憶體等。然而同 VM 不同的是，容器的程式間互動實際上還是 host 上具有相同 pid 命名空間中的程式間互動，因此需要在 IPC 資源申請時加入命名空間訊息，每個 IPC 資源有一個唯一的 32 位 id

使用宿主主機ipc 命名空間

```
docker run --ipc=host
```

- mnt 命名空間

mnt 命名空間允許不同命名空間的程式看到的檔案結構不同，這樣每個命名空間 中的程式所看到的檔案目錄就被隔離開了。每個命名空間中的容器在 /proc/mounts 的訊息只包含所在命名空間的 mount point。

- uts 命名空間

UTS("UNIX Time-sharing System") 命名空間允許每個容器擁有獨立的 hostname 和 domain name, 使其在網路上可以被視作一個獨立的節點而非主機上的一個程式。

使用宿主主機uts 命名空間

```
docker run --uts=host
```

- user 命名空間

每個容器可以有不同的使用者和組 id, 也就是說可以在容器內用容器內部的使用者執行程式而非主機上的使用者。

使用宿主主機user 命名空間

```
docker run --userns=host
```

```
docker run --privileged
```

##### 刪除未使用的物件

- Remove unused images

```
docker image prune
```

- Remove all stopped containers

```
docker container prune
```

- Remove all unused local volumes

```
docker volume prune
```

- Remove all unused networks

```
docker network prune
```

- Remove unused data

```
docker system prune
```

### Dockerfile

指令 |說明
:---|:---
FROM| 使用的基礎鏡像
MAINTAINER| 維護者訊息
ENV| 環境變數
RUN| 鏡像檔基底上執行指定命令
ADD| 可以是一個 URL；還可以是一個 tar 檔案（其複製後會自動解壓縮）
COPY| 複製一個目錄或一個檔案
EXPOSE| 容器對外的Port
VOLUME| 從本地端或其他容器掛載的掛載點
USER| 運行容器時的使用者名稱或 UID，後續的 RUN 也會使用指定使用者
WORKDIR| 後續的 RUN、CMD、ENTRYPOINT 指令指定工作目錄
CMD|  指定啟動容器時執行的命令
ENTRYPOINT| 指定容器啟動後執行的命令，並且不會被 docker run 提供的參數覆蓋

[example](Dockerfile)


- Build an image from a Dockerfile

```
docker build -t
```

### Base Image

##### Google

Google-provided: https://cloud.google.com/artifact-management/docs/managed-base-images#google-provided_base_images

cloud-build-samples: https://github.com/GoogleCloudPlatform/cloud-build-samples

##### RedHat

Universal: https://www.redhat.com/en/blog/introducing-red-hat-universal-base-image

Explore: https://catalog.redhat.com/software/containers/explore

##### Open Source

python: https://github.com/docker-library/python

golang: https://github.com/docker-library/golang

terraform: https://github.com/hashicorp/terraform/

ansible: https://github.com/ansible/ansible-docker-base