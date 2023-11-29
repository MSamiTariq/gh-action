---
title: IstioOperator should allow updating items using overlays
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Specify a list format in the overlay path for IstioOperator.

```yaml
apiVersion: install.istio.io/v1alpha1
kind: IstioOperator
metadata:
  name: istiod
  namespace: istio-system
spec:
  components:
    pilot:
      enabled: true
      k8s:
        overlays:
        - kind: Deployment
          name: istiod
          patches:
+          - path: spec.template.spec.containers.[name:discovery].args.[100]
            value: --grpcAddr=:15020
+          - path: spec.template.spec.containers.[name:discovery].ports.[containerPort:15010]
            value:
              containerPort: 15020
              protocol: TCP
        - kind: Service
          name: istiod
          patches:
          - path: spec.ports.[port:15010]
            value:
              port: 15020
              name: grpc-xds
              protocol: TCP
```
```yaml Terraform
# coming soon
```
```yaml Pulumi
# coming soon
```

For more details on customizing Istio installation, please refer to the official Istio documentation here:  
[Istio-Custom-Installation](https://istio.io/latest/docs/setup/additional-setup/customize-installation/)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk Signature.

## What is the impact? (Availability Impact)

An invalid overlay path will invalidate the IstioOperator configuration causing Istio to malfunction and stop serving traffic in the cluster.

## Why does this exist? (Root Cause)

Updates to Istio config will not be applied due to an invalid overlay path format.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using any version of Istio.

_Affected Images_  
All container image tags for Istio are affected.

## Additional Resources

Details of the exact github issue can be found [here](https://github.com/istio/istio/issues/34024).