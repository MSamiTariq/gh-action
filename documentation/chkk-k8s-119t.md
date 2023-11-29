---
title: Istio Delegate VirtualService should specify a valid namespace
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Specify a valid namespace in `spec.http.[].delegate.namespace`

```yaml
---
apiVersion: networking.istio.io/v1alpha3
kind: VirtualService
metadata:
  name: bookinfo
spec:
  hosts:
  - "bookinfo.com"
  gateways:
  - mygateway
  http:
  - match:
    - uri:
        prefix: "/productpage"
    delegate:
       name: productpage
+       namespace: nsA
---
apiVersion: networking.istio.io/v1alpha3
kind: VirtualService
metadata:
  name: productpage
  namespace: nsA
spec:
  http:
  - match:
     - uri:
        prefix: "/productpage/v1/"
    route:
    - destination:
        host: productpage-v1.nsA.svc.cluster.local
  - route:
    - destination:
        host: productpage.nsA.svc.cluster.local
```
```yaml Terraform
# coming soon
```
```yaml Pulumi
# coming soon
```

For more details on setting up a Delegate Virtual Service, please refer to the official Istio documentation here:  
[Istio-Delegate-VirtualService](https://istio.io/latest/docs/reference/config/networking/virtual-service/#Delegate)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk Signature.

## What is the impact? (Availability Impact)

An invalid Istio Delegate configuration will cause Istio to malfunction and stop serving traffic in the cluster.

## Why does this exist? (Root Cause)

Omitting the namespace for Delegate invalidates the VirtualService resulting in no rules being pushed to Envoy.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using any version of Istio.

_Affected Images_  
All container image tags for Istio are affected.

## Additional Resources

The GitHub issue can be found [here](https://github.com/istio/istio/issues/33251)