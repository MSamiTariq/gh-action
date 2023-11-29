---
title: Cilium-agent crashes when a remote node without node IP addresses is removed
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

Upgrade your Cilium version in accordance with the following table:

| Cilium Version | Fixed Patch Version  |
| -------------- | -------------------- |
| `v1.13`        | `v1.13.5` or greater |
| `v1.12`        | `v1.12.13`           |
| `v1.11`        | `v1.11.20`           |

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

This defect can cause all the Cilium-agent pods on every node to restart simultaneously which in turn may cause traffic outage resulting in unwanted downtime.

## Why does this exist? (Root Cause)

This defect exists due to a bug in code where a case was not being handled properly causing it to return a nil pointer. When this nil pointer was accessed, the code threw out a nil pointer dereference error resulting in the aforementioned impact.

## Who is impacted and when? (Trigger Conditions)

The following Cilium versions will have this risk:

| Cilium Version | Patch Versions with this risk |
| -------------- | ----------------------------- |
| `v1.13`        | `v1.13.0` to `v1.13.4`        |
| `v1.12`        | `v1.12.8` to `v1.12.12`       |
| `v1.11`        | `v1.11.14` to `v1.11.19`      |

## Additional Resources

For more information, please refer to 

1. [Github Issue](https://github.com/cilium/cilium/issues/25543)
2. [PR that fixed this issue](https://github.com/cilium/cilium/pull/25851)