# Week 01 - container 進階

### docker

- Docker 採用了 C/S 架構，包括客戶端和服務端。 Docker daemon 作為服務端接受來自客戶的請求，並處理這些請求（建立、執行、分發容器）。 客戶端和服務端既可以執行在一個機器上，也可透過 socket 或者 RESTful API 來進行通信。
- Docker daemon 一般在宿主主機後臺執行，等待接收來自客戶端的消息。 Docker 客戶端則為使用者提供一系列可執行命令，使用者用這些命令實作跟 Docker daemon 互動。

![docker](images/01.png)

### podman

- Podman 是一個開源的容器運行時項目，可在大多數 Linux 平台上使用。 Podman 提供與 Docker 非常相似的功能。正如前面提到的那樣，它不需要在你的系統上運行任何守護進程，並且它也可以在沒有 root 權限的情況下運行。
- Podman 可以管理和運行任何符合 OCI（Open Container Initiative）規範的容器和容器鏡像。 Podman 提供了一個與 Docker 兼容的命令行前端來管理 Docker 鏡像。


 |Docker |Podman
:---|:---|:---
架構 |Client/Server |Fork/Exec
運行程序 |root 運行 |root/非root 運行
OCI |符合 OCI 標準 |符合 OCI 標準

### skopeo

- Skopeo 是一個鏡像管理工具，允許我們通過 Push、Pull和復製鏡像來處理 Docker 和符合 OCI 規範的鏡像。

### buildah

- 雖然 Podman 也可以支持用戶構建 Docker 鏡像，但是構建速度比較慢。並且默認情況下使用 VFS 存儲驅動程序會消耗大量磁盤空間。
- Buildah 是一個專注於構建 OCI 容器鏡像的工具，Buildah 構建速度非常快並使用覆蓋存儲驅動程序，可以節約大量的空間。
- Buildah 基於 fork-exec 模型，不以守護進程運行。 Buildah 支持 Dockerfile 中的所有命令。你可以直接使用 Dockerfiles 來構建鏡像，並且不需要任何 root 權限。 Buildah 也支持用自己的語法文件構建鏡像，可以允許將其他腳本語言集成到構建過程中。

![Docker vs Podman](images/02.png)

### docker-compose



### podman-docker

https://jimmysong.io/kubernetes-handbook/