---
title: Overlap of node removals and IP changes could lead to shared CIDR ranges causing network connectivity issues when using Calico
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term  fix? (Remediation)

Upgrade your Calico version as recommended in the following table

| Calico version | Fixed patch versions    |
| -------------- | ----------------------- |
| `v3.23`        | `v3.23.2` and greater\* |
| `v3.22`        | `v3.22.4` and greater   |

\* _This includes all the minor versions released after `v3.23`_

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

This defect has the potential to disrupt network communication. Unresolved, it could lead to intermittent or complete communication breakdowns between nodes causing outages.

## Why does this exist? (Root Cause)

This defect originated from a bug within the Calico codebase, specifically in the wireguard module. This bug was caused by an incorrect handling of the mapping between CIDR and nodes. As a consequence, a scenario could arise where a mixture of node removals and relocation of workload IP addresses led to the possibility of multiple nodes sharing the same CIDR. Although the wireguard module was designed to avert such situations, the presence of this bug hindered its capacity to do so.

## Who is impacted and when? (Trigger Conditions)

The following Calico versions will have this risk:

| Calico Version | Patch Version affected by this defect |
| -------------- | ------------------------------------- |
| `v3.23`        | `v3.23.0 - v3.23.1`                   |
| `v3.22`        | `v3.22.0 - v3.22.3`                   |

## Additional Resources

For more information, please refer to 

1. [PR that fixed this defect](https://github.com/projectcalico/calico/pull/6185)