## k8s总体架构图
![k8s图1](https://raw.githubusercontent.com/yanming-zhang/Study-Notes/master/resources/k8s-1.png)

![k8s图2](https://raw.githubusercontent.com/yanming-zhang/Study-Notes/master/resources/k8s-2.png)

## 当使用kubectl或调用kube-apiserver提供的api创建pod和service时，工作流程如下：
* kube-apiserver，把相关的pod和service配置存储到etcd中。
* kube-scheduler，从kube-apiserver获取到相关pod的配置，根据集群中的资源和条件限制把pod调度到相应的node节点上。
* kube-controller-manager，从kube-apiserver获取到相关pod和service的配置，定期检查pod的状态，保证有用户配置的足够数量的pod副本在运行，生成service到pod的规则关系。
* kubelet，从kube-apiserver获取分配到本节点的相关pod配置，在本地启动容器并定期检查返回容器状态。
* kube-proxy，从kube-apiserver获取service到pod的规则，在本节点维护iptable或者ipvs相关路由规则。
