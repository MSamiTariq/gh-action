---
title: Linkerd versions less than v2.12.4 may route traffic to incorrect Pod IPs due to a mismatch between the Kubernetes EndpointSlice and LinkerD Routes
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Linkerd to `v2.12.4` or greater.  
There are four components that need to be upgraded:

- The CLI
- The control plane
- The control plane extensions
- The data plane

It is important that the following steps be performed in sequence:

1. **Upgrade CLI**

```shell
curl --proto '=https' --tlsv1.2 -sSfL https://run.linkerd.io/install | sh
```

2. **Upgrade the Control Plane**

```shell
linkerd upgrade | kubectl apply --prune -l linkerd.io/control-plane-ns=linkerd -f -
```

```shell
linkerd upgrade | kubectl apply --prune -l linkerd.io/control-plane-ns=linkerd \
  --prune-whitelist=rbac.authorization.k8s.io/v1/clusterrole \
  --prune-whitelist=rbac.authorization.k8s.io/v1/clusterrolebinding \
  --prune-whitelist=apiregistration.k8s.io/v1/apiservice -f -
```

3. **Upgrade Extensions**

```shell
linkerd viz install | kubectl apply -f - 
linkerd multicluster install | kubectl apply -f - 
linkerd jaeger install | kubectl apply -f -
```

4. **Upgrade Data Plane**

```shell
kubectl -n <namespace> rollout restart deploy
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Inadequate synchronization between Kubernetes EndpointSlice and Linkerd Routes in Linkerd versions prior to `v2.12.4` may cause traffic to be routed to incorrect Pod IPs. This can result in increased latency and error rates.

## Why does this exist? (Root Cause)

This defect is caused by a race condition between the Kubernetes API and the Linkerd watcher. Although Kubernetes removes the Pod and it no longer exists in the Endpoint Slice, it remains in the Linkerd route table, resulting in an error message due to Linkerd responding to events on the outdated Endpoint Slice before fetching information about the removed Pod.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using Linkerd versions `< stable-2.12.4` contain this Latent Availability Risk.

## Additional Resources

For more information see:

- [GitHub issue](https://github.com/linkerd/linkerd2/issues/10003)
- [GitHub PR](https://github.com/linkerd/linkerd2/pull/10013)
- [Linkerd Upgrade Guide](https://linkerd.io/2.12/tasks/upgrade/)