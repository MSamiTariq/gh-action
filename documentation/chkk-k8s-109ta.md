---
title: Empty regex should not be allowed for Istio VirtualService
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Regex value should not be empty.

```yaml
apiVersion: networking.istio.io/v1alpha3
kind: VirtualService
metadata:
  name: ratings-route
spec:
  hosts:
  - s1.default.svc.cluster.local
  http:
  - match:
    - method:
+        regex: "test"
      name: 80_default
    route:
    - destination:
        host: s1.default.svc.cluster.local
```
```yaml Terraform
# coming soon
```
```yaml Pulumi
# coming soon
```

For more details on configuring EnvoyFilter with Istio, please refer to the official Istio documentation here:  
[Istio-Release-Notes](https://istio.io/latest/news/releases/1.9.x/announcing-1.9/upgrade-notes/#envoyfilter-xds-v2-removal)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk Signature.

## What is the impact? (Availability Impact)

An empty regex will invalidate the VirtualService configuration causing Istio to malfunction and stop serving traffic in the cluster.

## Why does this exist? (Root Cause)

An empty regex will invalidate the Istio VirtualService configuration and may bring down the overall cluster.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using any version of Istio.

_Affected Images_  
All container image tags for Istio are affected.

## Additional Resources

For more details look for [virtual service documentation](https://istio.io/latest/docs/reference/config/networking/virtual-service/)