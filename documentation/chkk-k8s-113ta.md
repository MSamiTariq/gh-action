---
title: Restrict sum of endpoint loadbalancing weights to not exceed uint32 max value
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Update endpoint weights to ensure that the sum of all endpoint weights is less than the unint32 max value (4294967295).

```yaml
apiVersion: networking.istio.io/v1beta1
kind: ServiceEntry
metadata:
  name: se-w-total-ep-wights-over-uint32-max 
spec:
  endpoints:
  - address: 10.0.0.1
    locality: us-west-2
    ports:
      http: 15443
+    weight: 1
  - address: 10.0.0.2
    locality: us-east-2
    ports:
      http: 15443
+    weight: 1
  - address: 10.0.0.3 
    locality: us-east-2
    ports:
      http: 15443
+    weight: 1
  exportTo:
  - '*'
  hosts:
  - www.bookinfo.com 
  location: MESH_INTERNAL
  ports:
  - name: http
    number: 80
    protocol: HTTP
  resolution: DNS
```
```yaml
# coming soon
```
```yaml
# coming soon
```

For more details on configuring a WorkloadEntry, please refer to the official Istio documentation here:  
[Istio-Networking-WorkloadEntry](https://istio.io/latest/docs/reference/config/networking/workload-entry/#WorkloadEntry)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk Signature.

## What is the impact? (Availability Impact)

An invalid ServiceEntry configuration will cause Istio to malfunction and stop serving traffic in the cluster.

## Why does this exist? (Root Cause)

Istio config generation may fail when the sum of endpoint loadbalancing weights exceeds the unint32 max value (4294967295).

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using any version of Istio.

_Affected Images_  
All container image tags for Istio are affected.

## Additional Resources

The GitHub issue can be found [here](https://github.com/istio/istio/issues/33536)