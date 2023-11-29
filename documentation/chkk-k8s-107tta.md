---
title: Istio config should include K8s address with Nacos MCP service
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Specify the K8s address `k8s://` in Istio config.

```yaml
---
apiVersion: install.istio.io/v1alpha1
kind: IstioOperator
spec:
  meshConfig:
    accessLogFile: /dev/stdout
    configSources:
    - address: xds://10.15.4.2:18848
+    - address: k8s://
```
```yaml Terraform
# coming soon
```
```yaml Pulumi
# coming soon
```

For more details on integrating Nacos with Istio as a MCP server, please refer to the following documentation:  
[nacos-istio](https://github.com/nacos-group/nacos-istio)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk Signature.

## What is the impact? (Availability Impact)

Istio configuration settings will not fully propagate in the cluster, preventing traffic from being correctly routed to its destinations.

## Why does this exist? (Root Cause)

Istio Gateway and VirtualService will not work with the configured Nacos MCP service.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using any version of Istio with Nacos MCP service.

_Affected Images_  
All container image tags for Istio are affected.

## Additional Resources

The GitHub issue with more details can be found here: [Istiod couldn’t sense the crd’s change when config a nacos mcp service](https://github.com/istio/istio/issues/34134)