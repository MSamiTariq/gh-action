---
title: External Secrets Operator is running on an incompatible version of K8s.
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend running an External Secrets Operator version that is compatible with your Kubernetes version. Please refer to the following compatibility matrix:

| ESO Version | Kubernetes Version |
| :---------- | :----------------- |
| `v0.9.x`    | `v1.19 → v1.28`    |
| `v0.8.x`    | `v1.19 → v1.28`    |
| `v0.7.x`    | `v1.19 → v1.26`    |
| `v0.6.x`    | `v1.19 → v1.24`    |
| `v0.5.x`    | `v1.19 → v1.24`    |
| `v0.4.x`    | `v1.16 → v1.24`    |
| `v0.3.x`    | `v1.16 → v1.24`    |

This ARSig is a subset of [CHKK-K8S-2800 ](https://app.chkk.io/kba/chkk-k8s-2800)and the Remediation to move to the latest version of ESO will fix both Availability Risks.

## How to fix it, short-term workaround? (Mitigation)

None

## What is the impact? (Availability Impact)

External Secrets Operator is not supported by the Kubernetes version you are running, which means that the software may have incompatibilities leading to unknown behavior.

## Why does this exist? (Root Cause)

Using a version of Kubernetes not supported by External Secrets Operator introduces incompatibilities in your software and may lead to undefined behavior.

## Additional Resources

For more details, please refer to [ESO's official documentation](https://external-secrets.io/latest/introduction/stability-support/)