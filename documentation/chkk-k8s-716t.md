---
title: A control-plane deadlock in Cilium causes network outage
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Depending on the Cilium minor version that you are using, upgrade to the following recommended versions:

| Cilium Minor Version | Recommended Version for Upgrading |
| -------------------- | --------------------------------- |
| `v1.13`              | `v1.13.2` or greater              |
| `v1.12`              | `v1.12.9` or greater              |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

A network outage in a Kubernetes cluster (could be as a result of EKS scale events) can impact the overall availability of the entire cluster and the applications running inside it.

## Why does this exist? (Root Cause)

This defect exists because of a deadlock between the IPCache and some endpoint lock. This occurs when there are L7 policies in place. Some endpoint regeneration happens at an inopportune time, and the kube-apiserver endpoints change (which is why this can be triggered by an EKS scale-down event). Because multiple subsystems are affected by the deadlock, there are wide range of symptoms that could occur such as proxied DNS lookups failing, endpoint regeneration getting stuck, and eventually the L7proxy causing the DaemonSet's liveness probe to fail after 5 minutes.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using Cilium versions `v1.12.0`to`v1.12.9` and `v1.13.0` to `v1.13.2` contain this Latent Availability Risk.

## Additional Resources

For more information, please refer to:

1. [Github Issue](https://github.com/cilium/cilium/issues/20915)
2. [PR that fixed this issue](https://github.com/cilium/cilium/pull/24773)