---
title: Do not mount the Docker/containerd/CRI-O socket to Pods and Containers
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Docker/Containerd/CRI-O socket is highly privileged, effectively having root access. Any process or application having access to this socket also inherits elevated root privileges, and therefore, increases the risk of exploits.

```yaml sample-pod-docker-socket.yaml
apiVersion: v1
kind: Pod
metadata:
  name: frontend
spec:
  containers:
    name: app
    image: images.my-company.example/app:v4
  volumes:
    name: SampleVolume1
    hostPath:
-    path: /var/run/docker.sock
```
```yaml sample-pod-containerd-socket.yaml
apiVersion: v1
kind: Pod
metadata:
  name: frontend
spec:
  containers:
    name: app
    image: images.my-company.example/app:v4
  volumes:
    name: SampleVolume1
    hostPath:
-    path: /var/run/containerd.sock
```
```yaml sample-pod-crio-socket.yaml
apiVersion: v1
kind: Pod
metadata:
  name: frontend
spec:
  containers:
    name: app
    image: images.my-company.example/app:v4
  volumes:
    name: SampleVolume1
    hostPath:
-    path: /var/run/crio.sock
```

## What is the impact? (Availability Impact)

Exposing Docker/Containerd/CRI-O socket to a container effectively provides unauthorized root access to all processes in that container.

## Affected Components

Pod, Deployment, DaemonSet, StatefulSet, ReplicaSet, ReplicationController, Job and CronJob

## Additional Resources

For more details on container runtime refer to the[ documentation here](https://kubernetes.io/docs/setup/production-environment/container-runtimes/)