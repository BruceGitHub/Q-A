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

# Probe
During this entire process, **readiness** and **liveness** probes will still be probed, but their failure will **not cause the killing of the container**, as it is already being killed.

# Hook and delivery guarantees (PostStart | PreStop)
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

# Distribuiting times

|------------ terminationGracePeriodSeconds |------------ |

|--- PreStop ---- |

So `terminationGracePeriodSeconds` includes `PresStop` time.

- https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#hook-handler-execution


# Step 
```
- You use the kubectl tool to manually delete a specific Pod, with the default grace period (30 seconds).

- The Pod in the API server is updated with the time beyond which the Pod is considered "dead" along with the grace period. If you use kubectl describe to check on the Pod you're deleting, that Pod shows up as **Terminating**. 

- On the node where the Pod is running: as soon as the kubelet sees that a Pod has been marked as **terminating** (a graceful shutdown duration has been set), 

- The kubelet begins the local Pod shutdown process.
  - if one of the Pod's containers has defined a **preStop** hook, the kubelet runs that hook inside of the container. 
    - If the **preSto**p hook is still running after the grace period expires, the kubelet requests a small, one-off grace period extension of 2 seconds.

  - The kubelet triggers the container runtime to send a TERM signal to process 1 inside each container.
    - If the order of shutdowns matters, consider using a preStop hook to synchronize.

- At the same time as the kubelet is starting graceful shutdown, the control plane removes that shutting-down Pod from EndpointSlice (and Endpoints) objects where these represent a 
  Service with a configured selector. 
  - ReplicaSets and other workload resources no longer treat the shutting-down Pod as a valid, in-service replica. 
  - Pods that shut down slowly cannot continue to serve traffic as load balancers (like the service proxy) remove the Pod from the list of endpoints **as soon as the termination grace period begins.** 

  - When the grace period expires, the kubelet triggers forcible shutdown. The container runtime sends SIGKILL to any processes still running in any container in the Pod. The kubelet also cleans up a hidden pause container if that container runtime uses one.

  - The kubelet triggers forcible removal of Pod object from the API server, by setting grace period to 0 (immediate deletion).

  - The API server deletes the Pod's API object, which is then no longer visible from any client.
```

# Flow 
![](https://miro.medium.com/max/640/0*f5uyna4QDLDP8-cm)

# Reference
- https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/#pod-termination
- 2022 - https://livebook.manning.com/concept/kubernetes/terminationgraceperiodsecond
- 2020 - https://carlosbecker.com/posts/k8s-pod-shutdown-lifecycle/
- 2018 - https://cloud.google.com/blog/products/containers-kubernetes/kubernetes-best-practices-terminating-with-grace
- 2016 - https://pracucci.com/graceful-shutdown-of-kubernetes-pods.html