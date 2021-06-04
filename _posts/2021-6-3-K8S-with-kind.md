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