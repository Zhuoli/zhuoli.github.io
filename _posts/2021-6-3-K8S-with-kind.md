---
layout: post
title: 'KIND一种新的技术在本地电脑上模拟Kubernetes'
date: 2021-6-3
author: zhuoli
cover: 'http://on2171g4d.bkt.clouddn.com/jekyll-banner.png'
tags: k8s, kubernetes
---

在自己的电脑上运行k8s可以很方便的测试你得k8s yaml文件，之前有minikube单它并不支持multi-node. 最近kind开始流行起来，而且它与WSL (Windows Substem Linux)集成的很好。那么我们就开始用kind吧.

`
Why kind?
kind supports multi-node (including HA) clusters
kind supports building Kubernetes release builds from source
support for make / bash or docker, in addition to pre-published builds
kind supports Linux, macOS and Windows
kind is a CNCF certified conformant Kubernetes installer
`

## 安装kind并创建你的第一个k8s cluster
一个cluster就是多个nodes的集合，就是一个k8s unit。下面示例中，我们创建了一个名叫wslkind的cluster,并把kubeconfig配置文件写入了 $~/.kube/config文件中
```bash
# Check if the KUBECONFIG is not set
echo $KUBECONFIG
# Check if the .kube directory is created > if not, no need to create it
ls $HOME/.kube
# Create the cluster and give it a name (optional)
kind create cluster --name wslkind
# Check if the .kube has been created and populated with files
ls $HOME/.kube
# list clusters that has been created
kind get clusters
# Check how many nodes it created
kubectl get nodes
# Check the services for the whole cluster
kubectl get all --all-namespaces
```


## 安装helm并部署你的第一个k8s service
helm可以帮助你部署k8s service, 参考helm主页: https://helm.sh/docs/intro/quickstart/

1. Create a example service using helm and create namespace if it does not exist
```bash
helm install bitnami/mysql --generate-name --create-namespace --namespace zhuolins
```


Tip:

  Watch the deployment status using the command:` kubectl get pods -w --namespace zhuolins`

Services:
``` bash
  echo Primary: mysql-1622777550.zhuolins.svc.cluster.local:3306
```
Administrator credentials:
```bash
  echo Username: root
  echo Password : $(kubectl get secret --namespace zhuolins mysql-1622777550 -o jsonpath="{.data.mysql-root-password}" | base64 --decode)
```
To connect to your database:

  1. Run a pod that you can use as a client:
```bash
      kubectl run mysql-1622777550-client --rm --tty -i --restart='Never' --image  docker.io/bitnami/mysql:8.0.25-debian-10-r16 --namespace zhuolins --command -- bash
```
  2. To connect to primary service (read/write):
```bash
      mysql -h mysql-1622777550.zhuolins.svc.cluster.local -uroot -p my_database
```
To upgrade this helm chart:

  1. Obtain the password as described on the 'Administrator credentials' section and set the 'root.password' parameter as shown below:
```bash
      ROOT_PASSWORD=$(kubectl get secret --namespace zhuolins mysql-1622777550 -o jsonpath="{.data.mysql-root-password}" | base64 --decode)
      helm upgrade --namespace zhuolins mysql-1622777550 bitnami/mysql --set auth.rootPassword=$ROOT_PASSWORD
```