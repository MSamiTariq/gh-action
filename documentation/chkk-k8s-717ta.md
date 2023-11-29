---
title: Data race in DNS proxy implementation may affect pod connectivity.
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Depending on the Cilium minor version that you are using, upgrade to the following recommended versions:

| Cilium Minor Version | Recommended Version for Upgrading |
| -------------------- | --------------------------------- |
| `v1.12`              | `v1.12.6` or greater              |
| `v1.11`              | `v1.11.13` or greater             |
| `v1.10`              | `v1.10.20`                        |

**Note: Cilium `v1.10`** is no longer officially supported. For more information, please refer to the following Knowledge Base Article: [Unsupported version of Cilium](https://app.chkk.io/kba/chkk-k8s-713)

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

A data race in proxy can lead to DNS requests getting dropped which in turn can disrupt service communication and pod-to-pod connectivity, affecting the overall availability of the cluster.

## Why does this exist? (Root Cause)

This issue was introduced in the [following PR](https://github.com/cilium/cilium/pull/22361) in which DNS proxy was patched to configure a `net.Dialer` for every outgoing request. However, the dialer was assigned to a single shared copy of `dns.Client` which lead to data corruption.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_

The following Cilium Versions are affected by this defect:

| Cilium Minor Version | Affected Patch Versions |
| -------------------- | ----------------------- |
| `v1.12`              | `v1.12.5`               |
| `v1.11`              | `v1.11.12`              |
| `v1.10`              | `v1.10.18` & `v1.10.19` |

## Additional Resources

For more information, please refer to 

1. [Github Issue](https://github.com/cilium/cilium/issues/22598)
2. [PR that fixed this issue](https://github.com/cilium/cilium/pull/22619)