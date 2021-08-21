# Week 05 - kubrenetes 基礎1


### Kubernetes Architecture



### Kubernetes Component

![K8S](images/k8s.png)

##### Master Node ( Control Plane)

- kube-apiserver

Kubernetes API服務器，Kubernetes 所有組件都是與Kubernetes API溝通，包括客戶端工具

- kube-scheduler

根據資源需求和政策，選擇並分配Pod所要運行的節點

- kube-controller-manager

負責管理並運行 Kubernetes 的控制組件，負責監視叢集程序狀態

- etcd

一致性和高可用性的鍵值資料庫，用於儲存Kubernetes的數據


##### Worker Node

- kubelet

節點的管理員，負責管理該節點上的所有 Pods 的狀態並負責與 Kubernetes API溝通

- kube-proxy

節點的網路代理，允許從群集內部或外部的網路會話與Pod進行網路通信

- Container Runtime

負責運行容器的程式，Kubernetes 支持多種容器運行環境，包含 Docker、 containerd、CRI-O 以及任何實現 Kubernetes CRI的程式


### Kubernetes Resource

分類 |資源
:---|:---
Workload |Pod, HorizontalPodAutoscaler
Controller |ReplicaSet, ReplicationController, Deployment, StatefulSet, DaemonSet, Job, CronJob
Service Discovery |Service, Ingress
Authentication & Authorization |ServiceAccount, RBAC(Role, ClusterRole, RoleBinding, ClusterRoleBinding)
Storage |PersistentVolumeClaim, PersistentVolume, StorageClass, Secret, ConfigMap
Policy |NetworkPolicy, SecurityContext, ResourceQuota, LimitRange
Extension |CustomResourceDefinitions

### YAML

###### 測驗

![exam01](YAML/exam01.JPG)

[Answer](YAML/exam01-answer.yml)

---

![exam02](YAML/exam02.JPG)

[Answer](YAML/exam02-answer.yml)

---

![exam03](YAML/exam03.JPG)

[Answer](YAML/exam03-answer.yml)

---

![exam04](YAML/exam04.JPG)

[Answer](YAML/exam04-answer.yml)

---

![exam05](YAML/exam05.JPG)

[Answer](YAML/exam05-answer.yml)

---

![exam06](YAML/exam06.JPG)

[Answer](YAML/exam06-answer.yml)


### POD

###### 測驗

![exam01](POD/exam01.JPG)

[Answer](POD/exam01-answer.yml)

---

![exam02](POD/exam02.JPG)

[Answer](POD/exam02-answer.yml)

---

![exam03](POD/exam03.JPG)

[Answer](POD/exam03-answer.yml)

---

![exam04](POD/exam04.JPG)

[Answer](POD/exam04-answer.yml)

---

![exam05](POD/exam05.JPG)

[Answer](POD/exam05-answer.yml)

---

![exam06](POD/exam06.JPG)

[Answer](POD/exam06-answer.yml)

---

![exam07](POD/exam07.JPG)

[Answer](POD/exam07-answer.yml)

---

![exam08](POD/exam08.JPG)

[Answer](POD/exam08-answer.yml)

---

![exam09](POD/exam09.JPG)

[Answer](POD/exam09-answer.yml)


### ReplicaSet

###### 測驗

![exam01](ReplicaSet/exam01.JPG)

[Answer](ReplicaSet/exam01-answer.yml)

---

![exam02](ReplicaSet/exam02.JPG)

[Answer](ReplicaSet/exam02-answer.yml)

---

![exam03](ReplicaSet/exam03.JPG)

[Answer](ReplicaSet/exam03-answer.yml)

---

![exam04](ReplicaSet/exam04.JPG)

[Answer](ReplicaSet/exam04-answer.yml)

---

![exam05](ReplicaSet/exam05.JPG)

[Answer](ReplicaSet/exam05-answer.yml)

---

![exam06](ReplicaSet/exam06.JPG)

[Answer](ReplicaSet/exam06-answer.yml)

---

![exam07](ReplicaSet/exam07.JPG)

[Answer](ReplicaSet/exam07-answer.yml)


### Deployment

###### 測驗

![exam01](Deployment/exam01.JPG)

[Answer](Deployment/exam01-answer.yml)

---

![exam02](Deployment/exam02.JPG)

[Answer](Deployment/exam02-answer.yml)

---

![exam03](Deployment/exam03.JPG)

[Answer](Deployment/exam03-answer.yml)

---

![exam04](Deployment/exam04.JPG)

[Answer](Deployment/exam04-answer.yml)

---

![exam05](Deployment/exam05.JPG)

[Answer](Deployment/exam05-answer.yml)

---

![exam06](Deployment/exam06.JPG)

[Answer](Deployment/exam06-answer.yml)

---

![exam07](Deployment/exam07.JPG)

[Answer](Deployment/exam07-answer.yml)

