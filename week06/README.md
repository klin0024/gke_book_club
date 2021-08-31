# Week 06 - kubrenetes 基礎2


### Service

- 定義了邏輯上的一群 Pod 以及如何存取他們的規則

- Kubernetes為Pod提供自己的IP地址和一組Pod的單個DNS名稱，但是Pod的IP和DNS名稱並不固定，所以需要Service在它們之間進行負載平衡，Service會提供固定的IP和DNS名稱

##### ClusterIP

##### NodePort

##### LoadBalancer

##### Headless

比較 |ClusterIP |NodePort |LoadBalancer |Headless
:---|:---|:---|:---|:---
對外 |N |Y |Y |N


###### 測驗

![exam01](Service/exam01.JPG)

[Answer](Service/exam01-answer.yml)

---

![exam02](Service/exam02.JPG)

[Answer](Service/exam02-answer.yml)

---

![exam03](Service/exam03.JPG)

[Answer](Service/exam03-answer.yml)

---

![exam04](Service/exam04.JPG)

[Answer](Service/exam04-answer.yml)

---

![exam05](Service/exam05.JPG)

[Answer](Service/exam05-answer.yml)

---

![exam06](Service/exam06.JPG)

[Answer](Service/exam06-answer.yml)

---

![exam07](Service/exam07.JPG)

[Answer](Service/exam07-answer.yml)


---

![exam08](Service/exam08.JPG)

[Answer](Service/exam08-answer.yml)


### Ingress

- Ingress公開了從群集外部到群集內服務的HTTP和HTTPS反向代理服務

- 流量路由由Ingress資源上定義的規則控制，可以定義多個路由規則

- 可以將Ingress配置為提供服務外部可訪問的URL，作為負載平衡的入口，並將SSL綁定在Ingress的入口上

### ServiceAccount

### RBAC

##### role

##### ClusterRole

##### RoleBinding

##### ClusterRoleBinding


### PersistentVolumeClaim

### PersistentVolume

### StorageClass

### Secret

### ConfigMap

### NetworkPolicy

### ResourceQuota

### LimitRange
