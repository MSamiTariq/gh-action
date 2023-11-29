---
title: Restrict IstioOperator to support a list of externalIPs
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Specify a list format for `externalIPs` in the IstioOperator configuration.

```yaml
apiVersion: install.istio.io/v1alpha1
kind: IstioOperator
metadata:  
  name: istio-controlplane
  namespace: istio-system
spec:
  components:
    ingressGateways:
    - enabled: true
      k8s:
        hpaSpec:
          minReplicas: 3
        service:
+          externalIPs:
+          - 10.80.36.171
          ports:
          - name: status-port
            nodePort: 32562
            port: 15021
            protocol: TCP
            targetPort: 15021
          - name: http2
            nodePort: 30623
            port: 80
            protocol: TCP
            targetPort: 8080
          - name: https
            nodePort: 32013
            port: 443
            protocol: TCP
            targetPort: 8443
      name: istio-ingressgateway
    pilot:
      enabled: true
      k8s:
        hpaSpec:
          minReplicas: 3
  meshConfig:
    defaultConfig:
      gatewayTopology:
        numTrustedProxies: 1
      tracing:
        sampling: 3
    enableTracing: true
  profile: default
```
```yaml Terraform
# coming soon
```
```yaml Pulumi
# coming soon
```

For more details on customizing Istio installation, please refer to the official Istio documentation here:  
[Istio-Service-Spec](https://istio.io/latest/docs/reference/config/istio.operator.v1alpha1/#ServiceSpec)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk Signature.

## What is the impact? (Availability Impact)

Specifying a single value field will invalidate the Istio configuration and cause the Istio installation to fail, preventing it from serving traffic in the cluster.

## Why does this exist? (Root Cause)

ExternalIPs is expected to be a list of one or more IPs in the IstioOperater configuration.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using any version of Istio.

_Affected Images_  
All container image tags for Istio are affected.

## Additional Resources

Details of the exact github issue can be found [here](https://github.com/istio/istio/issues/33984).