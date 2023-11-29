---
title: Restrict retryRemoteLocalities from using deprecated xDS v2 API
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade Istio to `v1.11+` to apply the available patch. To upgrade your version of Istio, please follow the steps given in the Official Istio Documentation [here](https://istio.io/latest/docs/setup/upgrade/)

```yaml yaml
'''Example VirtualService'''

apiVersion: networking.istio.io/v1beta1
kind: VirtualService
metadata:
  name: ratings-route
spec:
  hosts:
  - echo.default.svc.cluster.local
  http:
  - route:
    - destination:
        host: echo.default.svc.cluster.local
    retries:
      attempts: 3
      perTryTimeout: 2s
      retryOn: gateway-error,connect-failure,refused-stream
+      retryRemoteLocalities: true
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk Signature.

## What is the impact? (Availability Impact)

Using `retryRemoteLocalities` will invalidate VirtualService configuration, causing Istio to malfunction and stop serving traffic in the cluster.

## Why does this exist? (Root Cause)

In Istio versions `v1.10.2` and below, the `retryRemoteLocalities` in VirtualService uses v2 xDS API which is now deprecated and disabled by default.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using versions of Istio earlier than and including `v1.10.2`

_Affected Images_  
The container image tags for Istio earlier than and including `v1.10.2` are affected.

Avoid using `retryRemoteLocalities` in the VirtualService configuration.

## Additional Resources

Details of the exact github issue can be found [here](https://github.com/istio/istio/issues/33737).