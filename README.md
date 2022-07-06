# Pelorus workshop
// TODO: intro to pelorus 

**.Why Pelorus?**
// TODO: Vision with image: https://pelorus.readthedocs.io/en/latest/Philosophy/

**.Architecture**
// TODO: https://pelorus.readthedocs.io/en/latest/Architecture/

## Prerequisites
* OPC 4.7+
* oc cli
* Helm 3

## Installation

**.Clone Pelorus**

In this example we will clone the Pelorus 1.6.0 version

```zsh
git clone --depth 1 --branch v1.6.0 https://github.com/konveyor/pelorus
cd pelorus
```

**.Create the namespace**

I will use the namespace ```pelorus```. Feel free to use another namespace. 

```zsh
oc create namespace pelorus
```

**.Install the operator with Helm**
```zsh
helm install operators charts/operators --namespace pelorus
```

If we explore the pods, we can see that Pelorus have deployed ```Grafana``` and ```Prometheus``` operators. 

```zsh
❯ oc get pods -n pelorus
NAME                                                   READY   STATUS    RESTARTS   AGE
grafana-operator-controller-manager-85fd5c89bb-qpfgt   2/2     Running   0          8m53s
prometheus-operator-6b495cc576-q54mm                   1/1     Running   0          8m46s
```

**.Install Pelorus**
Once the Operator have been istalled completely, it's time to deploy the Pelorus instance. 

We will use the Pelorus chart:
```zsh
helm install pelorus charts/pelorus --namespace pelorus
```