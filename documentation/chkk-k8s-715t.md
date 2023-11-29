---
title: Cross-nodes connectivity issues with IPsec when upgrading to Cilium v1.13.1, v1.12.8, and v1.11.15
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Depending on the Cilium minor version that you are using, upgrade to the following recommended versions:

| Cilium Minor Version | Recommended Version for Upgrading |
| -------------------- | --------------------------------- |
| `v1.13`              | `v1.13.2`                         |
| `v1.12`              | `v1.12.9`                         |
| `v1.11`              | `v1.11.16`                        |

Important: During the update packet drops may occur. As per the community’s upgrade notes for [v1.13.2](https://docs.cilium.io/en/v1.13/operations/upgrade/#id2), [v1.12.9](https://docs.cilium.io/en/v1.12/operations/upgrade/#upgrade-notes), and [v1.11.16](https://docs.cilium.io/en/v1.11/operations/upgrade/#id1):

> These drops are expected to stop as soon as the Cilium agent is ready. IPsec error counters `XfrmInNoStates` and `XfrmOutPolBlock` may increase as a result of these drops.

## How to fix it, short-term workaround? (Mitigation)

As per their upgrade notes, this issue exists when upgrading to `v1.13.1`, `v1.12.8`, or `v1.11.15`. In order to upgrade to these versions, you can mitigate this issue by following either of the two steps:

1. Replacing workload nodes in the cluster (to get a fresh IPsec state) OR
2. Flushing the current state by running the following command on each node: `ip xfrm state flush && ip xfrm policy flush`.

## What is the impact? (Availability Impact)

Dropped connections in a cluster can disrupt communication between nodes and affect the overall availability of the cluster.

## Why does this exist? (Root Cause)

When upgrading to `v1.11.15`, `v1.12.8`, or `v1.13.1` with IPsec enabled, cross-node connectivity fails completely because the IPsec state is not refreshed, which causes dropped connections in the cluster.

## Who is impacted and when? (Trigger Conditions)

_Affected Versions_  
All clusters using Cilium versions `v1.10.x`, `v1.11.0` to `v1.11.15`, `v1.12.0` to `v.1.12.8` and `v1.13.0` to `v1.13.1` contain this Latent Availability Risk.

## Additional Resources

For more information, please refer to the following:

1. [Github Issue](https://github.com/cilium/cilium/issues/24780)
2. [PR that fixed this issue](https://github.com/cilium/cilium/pull/24773)
3. [Cilium v1.13.1 Upgrade Notes](https://docs.cilium.io/en/v1.13/operations/upgrade/#id3)
4. [Cilium v1.13.2 Upgrade Notes](https://docs.cilium.io/en/v1.13/operations/upgrade/#id2)
5. [Cilium v1.12.9 Upgrade Notes](https://docs.cilium.io/en/v1.12/operations/upgrade/#upgrade-notes)
6. [Cilium v1.11.15 Upgrade Notes](https://docs.cilium.io/en/v1.11/operations/upgrade/#id2)
7. [Cilium v1.11.16 Upgrade Notes](https://docs.cilium.io/en/v1.11/operations/upgrade/#id1)