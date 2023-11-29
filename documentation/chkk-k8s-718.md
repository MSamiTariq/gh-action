---
title: DNS proxy may forward incorrect security identity causing unexpected policy denials in Cilium pods
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

**Note: Cilium `v1.10`** is no longer officially supported. For more information, please refer to the following Knowledge Base Article: [Your Current Version of Cilium is unsupported](https://app.chkk.io/kba/chkk-k8s-713)

Depending on the Cilium minor version that you are using, upgrade to the following recommended versions:

| Cilium Minor Version | Recommended Version for Upgrading |
| -------------------- | --------------------------------- |
| `v1.12`              | `v1.12.6` or greater              |
| `v1.11`              | `v1.11.13` or greater             |
| `v1.10`              | `v1.10.20`                        |

Although this Issue was fixed in versions prior to the ones mentioned in the above table, via [this PR](https://github.com/cilium/cilium/pull/22361), there were more issues that were identified which were resolved by a follow up PR in the versions mentioned in the table above. For more details, please refer to the following Knowledge Base Article: **[Data race in DNS proxy implementation may affect pod connectivity.](https://app.chkk.io/kba/chkk-k8s-717)**

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Policy denials in your Cilium pods may prevent your pods from running or communicating with other pods and services, exposing your cluster to Availability Risks.

## Why does this exist? (Root Cause)

This issue was introduced in a previous [PR here](https://github.com/cilium/cilium/pull/20711) which introduced some policy-impacting changes. Additionally, there were two other additional bugs that were found in that PR when forwarding the source security identity of DNS requests:

1. The required number of bits were not being forwarded
2. TCP SYN didn't include the original identity, which could cause connection failures or policy bypass.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_

The following Cilium Versions are affected by this defect:

| Cilium Minor Version | Affected Patch Versions |
| -------------------- | ----------------------- |
| `v1.12`              | `v1.12.3` & `v1.12.4`   |
| `v1.11`              | `v1.11.10` & `v1.11.11` |
| `v1.10`              | `v1.10.16` & `v1.10.17` |

## Additional Resources

For more information, please refer to 

1. [PR that fixed this issue](https://github.com/cilium/cilium/pull/22619)