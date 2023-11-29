---
title: CertificateSigningRequest v1beta1 Deprecation
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Migrate manifests and API clients to use the certificates.k8s.io/v1 API version, available since `v1.19`.  
All existing persisted objects are accessible via the new API  
Notable changes in `certificates.k8s.io/v1`:

- For API clients requesting certificates:
  - `spec.signerName` is now required (see known Kubernetes signers), and requests for kubernetes.io/legacy-unknown are not allowed to be created via the `certificates.k8s.io/v1` API
  - `spec.usages` is now required, may not contain duplicate values, and must only contain known usages
- For API clients approving or signing certificates:
  - `status.conditions` may not contain duplicate types
  - `status.conditions[*].status` is now required
  - `status.certificate` must be `PEM-encoded,` and contain only CERTIFICATE blocks

```yaml sample-certificationsigningrequest.yaml
- apiVersion: certificates.k8s.io/v1beta1
+ apiVersion: certificates.k8s.io/v1
kind: CertificateSigningRequest
metadata:
  name: "2"
spec:
  extra:
    "24":
    - "25"
  groups:
  - "23"
  signerName: "20"
  uid: "22"
  username: "21"
status:
  certificate: cw==
  conditions:
  - lastTransitionTime: "2352-05-22T04:29:36Z"
    lastUpdateTime: "1985-03-23T14:10:57Z"
    message: "27"
    reason: "26"
```

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## Why does this exist? (Root Cause)

The `certificates.k8s.io/v1beta1` API version of CertificateSigningRequest is no longer served as of `v1.22`.

## Additional Resources

For more details, please refer to the official [Kubernetes documentation](https://kubernetes.io/docs/reference/using-api/deprecation-guide/#certificatesigningrequest-v122)