# Week 01 - container 進階

### podman

- Podman 是一個開源的容器運行時項目，可在大多數 Linux 平台上使用。 Podman 提供與 Docker 非常相似的功能。正如前面提到的那樣，它不需要在你的系統上運行任何守護進程，並且它也可以在沒有 root 權限的情況下運行。
- Podman 可以管理和運行任何符合 OCI（Open Container Initiative）規範的容器和容器鏡像。 Podman 提供了一個與 Docker 兼容的命令行前端來管理 Docker 鏡像。


### skopeo

- Skopeo 是一個鏡像管理工具，允許我們通過 Push、Pull和復製鏡像來處理 Docker 和符合 OCI 規範的鏡像。

### buildah

- 雖然 Podman 也可以支持用戶構建 Docker 鏡像，但是構建速度比較慢。並且默認情況下使用 VFS 存儲驅動程序會消耗大量磁盤空間。
- Buildah 是一個專注於構建 OCI 容器鏡像的工具，Buildah 構建速度非常快並使用覆蓋存儲驅動程序，可以節約大量的空間。
- Buildah 基於 fork-exec 模型，不以守護進程運行。 Buildah 支持 Dockerfile 中的所有命令。你可以直接使用 Dockerfiles 來構建鏡像，並且不需要任何 root 權限。 Buildah 也支持用自己的語法文件構建鏡像，可以允許將其他腳本語言集成到構建過程中。

### docker-compose



### podman-docker

https://jimmysong.io/kubernetes-handbook/