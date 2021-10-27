# Week 07 - kubrenetes 基礎3

### kubectl

- kubectl 命令行工具用於管理Kubernetes 集群

- 通過kubeconfig 文件來訪問Kubernetes 集群

- 設置kubeconfig 的3種方式:
  - 預設讀取 $HOME/.kube/config
  - 設置KUBECONFIG 環境變量指定kubeconfig 文件位置
  - kubectl 帶```-kubeconfig```參數指定kubeconfig 文件位置

### kubeconfig

##### clusters

- cluster包含 Kubernetes 集群的API Endpoint以及集群的CA憑證

- 也可以設置```insecure-skip-tls-verify: true```忽略Kubernetes API的TLS驗證

```
clusters:
- cluster:
    certificate-authority: path/to/my/cafile
    server: https://horse.org:4443
  name: horse-cluster
- cluster:
    insecure-skip-tls-verify: true
    server: https://pig.org:443
  name: pig-cluster
```

##### users

- user定義對 Kubernetes 集群進行身份驗證的客戶端憑據

- 可用的憑據包含client-certificate， client-key，token，, auth-provider和 username/password

```
users:
- name: blue-user
  user:
    token: blue-token
- name: green-user
  user:
    client-certificate: path/to/my/client/cert
    client-key: path/to/my/client/key
- name: gcp-user
  user:
    auth-provider:
      config:
        cmd-args: config config-helper --format=json
        cmd-path: /usr/lib/google-cloud-sdk/bin/gcloud
        expiry-key: '{.credential.token_expiry}'
        token-key: '{.credential.access_token}'
      name: gcp
```

##### contexts

- context 用於提供的身份驗證信息和命名空間將請求發送到指定的Kubernetes 集群

- context定義了一個命名的cluster, user, namespace元組

```
contexts:
- context:
    cluster: horse-cluster
    namespace: chisel-ns
    user: green-user
  name: federal-context
```

##### current-context

- 加載kubeconfig 配置時,默認使用的集群、用戶、命名空間元組的context

- 可以使用```kubectl config use-context```更改current-context, 切換到不同的Kubernetes 集群