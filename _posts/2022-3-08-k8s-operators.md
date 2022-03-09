---
layout: post
title: Kubernetes Operators (in progress)
---

One of the greatest features that Kubernetes provides us is the posibility to extend its functionality according our needs, this is done by using Custom Resource Definitios and Operators, in this post we are going to take a look about these concepts, and of course we are going to build our little operator using the operador-sdk framework.


## 1. Why do we need Operators?

The idea to build operators is to facilitate and simplify some repetitive tasks at the time we are managing Kubernetes clusters, and thus, we can focus in doing more 'thinkable' activities.

Another use for building Kubernetes Operators is to abstract the complexity when we want to install and manage the lifecycle of some external components (e.g. Istio, Redis, Vault) , that's why many open-source projects built their own operators to facilitate administrators to install.

### 1.1. What is an Kuberentes Operator?

A Kubernetes Operator is nothing but a component which is constantly watching the desired state of a CRD object and trying to apply that desired state in your Kubernetes cluster (e.g. install some deploy, scale down or up the replicas, etc.), this process is called 'Reconciliation'. A good example of an operator could be the Istio Operator. Before, the way we install Istio was via istioctl, helm or kubectl, although using those 3 tools to install Istio is not complicated, there is somme complexity at the time we want tu upgrade the Istio's version and so on, that's where Istio's operator comes in action, to facilitate our our user expirience with that tool and not worrying about the aforementionated complex and repetitive activities. 

If you were thinking the how we can express our custom desired state for a operator this IstioOperator manifest could be a good example

```yml
apiVersion: install.istio.io/v1alpha1
kind: IstioOperator
metadata:
  namespace: istio-system
  name: example-istiocontrolplane
spec:
  profile: demo  
```

## 2. Let's build our first operator 




