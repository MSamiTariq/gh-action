---
title: EndpointSlice v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the `discovery.k8s.io/v1` API version, available since `v1.21`.

All existing persisted objects are accessible via the new API  
Notable changes in `discovery.k8s.io/v1`:

- use per Endpoint nodeName field instead of deprecated topology[`kubernetes.io/hostname`] field
- use per Endpoint zone field instead of deprecated topology[`topology.kubernetes.io/zone`] field
- topology is replaced with the deprecatedTopology field which is not writable in v1

```yaml sample-endpointslice.yaml
- apiVersion: discovery.k8s.io/v1beta1
+ apiVersion: discovery.k8s.io/v1
kind: EndpointSlice
endpoints:
- addresses:
  - "20"
  conditions:
    ready: false
    serving: false
    terminating: false
  deprecatedTopology:
    "28": "29"
  hostname: "21"
  nodeName: "30"
  targetRef:
    apiVersion: "25"
    fieldPath: "27"
    kind: "22"
    name: "24"
    namespace: "23"
    resourceVersion: "26"
    uid: ɑ
  zone: "31"
metadata:
  name: "Test"
ports:
- appProtocol: "34"
  name: "33"
  port: 3000
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `discovery.k8s.io/v1beta1` API version of EndpointSlice will no longer be served in `v1.25`.

## Additional Resources

For more details on the deprecation of EndpointSlice, please refer to the official Kubernetes documentation here:  [K8s-Deprecated-API-Migration-Guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#endpointslice-v125)