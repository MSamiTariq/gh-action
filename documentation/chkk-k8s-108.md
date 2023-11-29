---
title: Prevent invalid ciphers in Istio gateway cipherSuites
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Specify a valid cipher from the supported cipher list for `Gateway.server.tls.cipherSuites`. The supported cipher list is described below:

- `ECDHE-ECDSA-AES128-GCM-SHA256`
- `ECDHE-RSA-AES128-GCM-SHA256`
- `ECDHE-ECDSA-AES256-GCM-SHA384`
- `ECDHE-RSA-AES256-GCM-SHA384`
- `ECDHE-ECDSA-CHACHA20-POLY1305`
- `ECDHE-RSA-CHACHA20-POLY1305`
- `ECDHE-ECDSA-AES128-SHA`
- `ECDHE-RSA-AES128-SHA`
- `ECDHE-ECDSA-AES256-SHA`
- `ECDHE-RSA-AES256-SHA`
- `AES128-GCM-SHA256`
- `AES256-GCM-SHA384`
- `AES128-SHA`
- `AES256-SHA`
- `DES-CBC3-SHA`

```yaml
apiVersion: networking.istio.io/v1beta1
kind: Gateway
metadata:
  name: echo
  namespace: default
spec:
  selector:
    istio: ingressgateway
  servers:
  - hosts:
    - '*'
    port:
      name: https
      number: 443
      protocol: HTTPS
    tls:
      cipherSuites:
+      - ECDHE-ECDSA-AES256-GCM-SHA384
      credentialName: istio-ingressgateway-certs
      mode: SIMPLE
```
```yaml Terraform
# coming soon
```
```yaml Pulumi
# coming soon
```

For more details on securing Istio with TLS, please refer to the official Istio documentation here:  
[Istio-Server-TLS-Settings](https://istio.io/latest/docs/reference/config/networking/gateway/#ServerTLSSettings)

## How to fix it, short-term workaround? (Mitigation)

Review and update the provided cipher suites to remove any invalid ciphers from Istio gateway configuration.

## What is the impact? (Availability Impact)

Invalid ciphers will break TLS configuration causing traffic disruption with services unable to send and receive any traffic.

## Why does this exist? (Root Cause)

Invalid ciphers will break TLS configuration leading to service NACKs.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All EKS clusters or Kubernetes clusters using any version of Istio.

_Affected Images_  
All container image tags for Istio are affected.

## Additional Resources

The associated GitHub issue can be found here: [Invalid cipherSuites lead to NACKs](https://github.com/istio/istio/issues/34084)