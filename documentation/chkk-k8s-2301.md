---
title: Your GKE cluster version has reached End of Life.
category: 655c49ff76fdad0024723139
---

## How to fix it, long-term fix? (Remediation)

We strongly recommend upgrading your Kubernetes control plane version to one of the supported versions as per the guidelines provided by GKE. See the [GKE Release Schedule](https://cloud.google.com/kubernetes-engine/docs/release-schedule).

## How to fix it, short-term workaround? (Mitigation)

There is no mitigation or workaround for this Availability Risk.

## What is the impact? (Availability Impact)

Using a Kubernetes version that is no longer supported by GKE will lead to compatibility issues, and missing updates, risking the stability and functionality of your cluster.

## Why does this exist? (Root Cause)

GKE Clusters running a supported minor version will receive regular patches to fix bugs and security issues that have been reported. Based on the current Kubernetes OSS community version support policy, GKE maintains supported minor versions for 14 months, including the 12 months after the release in the Regular channel, followed by a 2-month maintenance period. During the maintenance period, no new node pool creations are allowed for a maintenance version, but existing node pools that run a maintenance version continue to remain in operation.  
At the end of the maintenance period, a maintenance version reaches end of life and officially becomes unsupported and unavailable. GKE minor versions that have reached end of life will no longer receive security patches and/or bug fixes.

## Additional Resources

For more information see:

- [GKE Release Schedule](https://cloud.google.com/kubernetes-engine/docs/release-schedule)
- [End of Life](https://cloud.google.com/kubernetes-engine/docs/release-schedule#fn3)
- [Maintenance Exclusion for v1.21](https://cloud.google.com/kubernetes-engine/docs/release-schedule#fn6)