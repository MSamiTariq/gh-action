---
title: containerd restarting on a node with pods that use Workload Identity, might cause failure to access Google Cloud APIs with POD_FINDER_IP_MISMATCH error
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

To fix the issue, upgrade your nodes to any of the following versions

- `v1.22.17-gke.3100` or later
- `v1.23.16-gke.200` or later
- `v1.24.9-gke.3200` or later
- `v1.25.6-gke.200` or later
- `v1.26.1-gke.400` or later

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Failure to access Google Cloud APIs may result in reduced performance, slower response times or your application facing downtime.

## Affected versions

The following GKE versions contain this defect

- `v1.22.16-gke.2100` and later
- `v1.23.14-gke.1900` and later
- `v1.24.7-gke.700` and later
- `v1.25.0` and later
- `v1.26.0` and later

## Additional Resources

For more details, see

- [GKE release notes for January 27, 2023](https://cloud.google.com/kubernetes-engine/docs/release-notes#January_27_2023)
- [GKE release notes for February 3, 2023](https://cloud.google.com/kubernetes-engine/docs/release-notes#February_03_2023)