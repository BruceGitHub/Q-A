---
layout: post
title: "Shutdown step during rolling updates"
date: 2032-01-03
tags:
 - [k8s]
 - [kubernetes]
 - [rolling update]
 - [shutdown]
 - [delay shutdown]
 - [graceful shutdown]
 - [terminationGracePeriodSeconds]
 - [preStop]
 - [The Container Runtime Interface (CRI)]
 - [The Container Network Interface (CNI)]
 - [The Container Storage Interface (CSI)]
 - [at least once hook send]
published: true
---

# Hook delivery guarantees (PostStart | PreStop)
Hook delivery is intended to be `at least once`, which means that a hook may be called multiple times for any given event, such as for PostStart or PreStop. 
It is up to the hook implementation to handle this correctly.
... For instance, if a kubelet restarts in the middle of sending a hook, the hook might be resent after the kubelet comes back up.

- https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#hook-delivery-guarantees

# PreStop

This hook is called immediately before a container is terminate (this extends the period that allow to kublet to removes `IP` from EndPoints table).
Because during the shutdown some step are excuted in parallel 

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: test-pod
spec:
  containers:
    - name: nginx
      image: nginx
      ports:
        - name: nginx
          containerPort: 80
      lifecycle:
        preStop:
          exec:
            command: ["sleep", "10"]
```


# Distribuiting times

|------------ terminationGracePeriodSeconds |------------ |
|--- PreStop ---- |

So 'terminationGracePeriodSeconds` includes `PresStop` time.

- https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#hook-handler-execution


# terminationGracePeriodSeconds
Time to wait before k8s kills the process default is 30s.The timer starts when the pre-stop hook is called or when the TERM signal is sent if no hook is defined. If the process is still running after the termination grace period has expired, it’s terminated by force via the KILL signal. This terminates the container.


```yaml
Listing 6.20 Setting a lower terminationGracePeriodSeconds for faster pod shutdown
apiVersion: v1
kind: Pod
metadata:
  name: kubia-ssl-shortgraceperiod
spec:
  terminationGracePeriodSeconds: 5
  containers:
  ...
```
- [flow](https://miro.medium.com/max/640/0*f5uyna4QDLDP8-cm)
- https://livebook.manning.com/concept/kubernetes/terminationgraceperiodsecond
- https://cloud.google.com/blog/products/containers-kubernetes/kubernetes-best-practices-terminating-with-grace